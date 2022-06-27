# Install Shiny Server on Raspberry Pi with R

It's time to have a Shiny Pi...

Yes, your Raspberry Pi can easily serve as a Shiny Server for you. You can host your own Shiny Apps, with complete control on your environment! The following scripts should allow you to do it easily. 

### Notes to self: 
While your Raspberry Pi will be operating as a server, please remember that it is a small sized server - please manage your expectations along the lines of the hardware configuration of your Pi. If in dobut, give us a shout.

If you are wondering.. why host my apps on a Pi? and why not continue on shinyapps.io?.. the answer is quite simple, if you want to gain some basic web development / web engineering skills and enjoy having full control of the server, then it's quite straightforward and rewarding to get started on a Pi. Conversely, if you just want ease of use, then head straight onto https://www.shinyapps.io/.

## Contents
- [Warnings](#Warnings)
- [Inportant Tasks Solved in the Script](#Important-Tasks-Solved-in-the-Script)
- [Installation with Stable R](#Installation-with-Stable-R)
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

## Uninstall Shiny Server and R
To remove Shiny Server AND R, please run the following command to execute the Uninstall_RPiShinyServer.sh script:
```bash
wget -O - https://raw.githubusercontent.com/MDSharma/Shiny-Futures-with-RaspberryPi-OS/master/Uninstall_RPiShinyServer.sh | bash
```
If you would only like to remove Shiny Server, please look into this script and only use what you need.
