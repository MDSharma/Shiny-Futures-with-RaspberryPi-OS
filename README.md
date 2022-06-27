# Install Shiny Server on Raspberry Pi with R

It's time to have a Shiny Pi...

Yes, your Raspberry Pi can easily serve as a Shiny Server for you. You can host your own Shiny Apps, with complete control on your environment! The following scripts should allow you to do it easily. 

Note to self: While your Raspberry Pi will be operating as a server, please remember that it is a small sized server - please manage your expectations along the lines of the hardware configuration of your Pi. If in dobut, give us a shout.


## Contents
- [Warnings](#Warnings)
- [Inportant Tasks Solved in the Script](#Important-Tasks-Solved-in-the-Script)
- [Installation with Stable R](#Installation-with-Stable-R)
- [Installation with Backport R](#Installation-with-Backport-R)
- [Uninstall Shiny-Server and R](#Uninstall-Shiny-Server-and-R)


## Warnings
These scripts are provided "as is" with no warranty of any kind. As such, users should read the script to ensure they are confident in its integrity. 

## Important Tasks Solved in the Script
- Handles system library dependencies for installing and running a Shiny Server
- Installs all R packages required for Shiny Server to start and index.html to successfully open
- Edits external/node/install-node.sh to obtain the correct NodeJS installation for a Raspberry Pi
- Builds Shiny Server via packaging/make-package.sh
- Configures Shiny Server, sets up initial server applications, and places all the required system directories
- Resolves Pandoc issues arising from Shiny Server using it's packaged Pandoc distribution by removing this directory and giving the system-installed version precedence


## Installation with Stable R

The provided Stable_RPiShinyServer.sh script will install the latest Shiny Server distribution along with the stable R version via the following command (N.B. the script takes awhile to run due to the R library installations):
```bash
wget -O - https://raw.githubusercontent.com/MDSharma/Shiny-Futures-with-RaspberryPi-OS/master/StableInstall_RPiShinyServer.sh | bash
```

## Installation with Backport R
Warning: you may attempt this at your own risk. If you already have R installed, this could remove all previously installed R libraries. If you would like to try using the latest (or later) version of R, you may follow these instructions to point the Raspberry Pi to the required mirrors (N.B. if you would like to upgrade your Raspberry Pi to a newer OS such as the Buster-based version, see here: https://www.raspberrypi.org/documentation/raspbian/updating.md).


### Add Secure Apt Key
Sourced from: https://cloud.r-project.org/bin/linux/debian/#secure-apt
```bash
sudo apt-get install dirmngr --install-recommends
sudo apt-key adv --keyserver keys.gnupg.net --recv-key 'E19F5F87128899B192B1A2C2AD5F960A256A04AF'
sudo apt-get -y update && sudo apt-get -y upgrade
```

### Add the Branch-Specific Mirror
Sourced from: https://cloud.r-project.org/bin/linux/debian/#supported-branches

#### For Buster & R 4
```bash
echo 'deb http://cloud.r-project.org/bin/linux/debian buster-cran40/' | sudo tee --append /etc/apt/sources.list
```

#### For Buster & R 3.6.3
```bash
echo 'deb http://cloud.r-project.org/bin/linux/debian buster-cran35/' | sudo tee --append /etc/apt/sources.list
```

#### For Stretch & R 3.6.3
```bash
echo 'deb http://cloud.r-project.org/bin/linux/debian stretch-cran35/' | sudo tee --append /etc/apt/sources.list
```

#### Finally Install Shiny Server and R
```bash
wget -O - https://raw.githubusercontent.com/MDSharma/Shiny-Futures-with-RaspberryPi-OS/master/StableInstall_RPiShinyServer.sh | bash
```

## Uninstall Shiny Server and R
To remove Shiny Server AND R, please run the following command to execute the Uninstall_RPiShinyServer.sh script:
```bash
wget -O - https://raw.githubusercontent.com/MDSharma/Shiny-Futures-with-RaspberryPi-OS/master/Uninstall_RPiShinyServer.sh | bash
```
If you would only like to remove Shiny Server, please look into this script and only use what you need.
