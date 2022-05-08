# Installation-of-WebGrab-Plus-in-the-LibreElec-and-CoreElec-System


1.  Install Addon Docker from 

>repository / All repositories / Services  -  DOCKER

I wrote them all because some use LibreElec and others use CoreElec.

   >Open the terminal ssh:

2.  Install WebGrab+Plus
Copy the entire code and paste it into the terminal. WebGrab+Plus is downloaded and configured automatically.
 
Code:

-----------------------------------------------------------------------------------------------------------------------------------------------

    docker run -d \
      --name=webgrabplus \
      --hostname="Your WebGrab+Plus registered name" \
      --mac-address="MAC address of your (already) registered PC at WebGrab+Plus" \
      -e PUID=0 \
      -e PGID=0 \
      -e TZ=Europe/Amsterdam \
      --restart unless-stopped \
      linuxserver/webgrabplus:3.2.3

 ---------------------------------------------------------------------------------------------------------------------------------------------- 
  
   Replace Quotes and everything in them with your data.

>Install:

3.  There are two other folders in the volumes folder. They have a long name. (A mixture of letters and numbers) 
    Both folders contain one folder  "_data"
    One is empty (automatically there save guide.xml) and in the second are the WebGrab+Plus configuration files.

    >/storage/.kodi/userdata/addon_data/service.system.docker/docker/volumes/9a861848d91ffaae41779e1196a9e308d3c0b044fbe7fab240b22dde5bec8804/_data/
    
    That folder name is unique and different for everyone!

    How to configure "WebGrab ++. Config.xml" I will not deal with here. I guess that's clear. 

    All you have to do is use "license enforcement" in the login line. "f" Then when it clicks, remove the letter!

    Autostart is set in the "wg3-cron" file

4.  Restart Docker.



-
If you want to have folders in another place, add two more lines.
-

This will create a "wg ++" folder in the "storage" folder with two more "config" folders with configuration files and "data" where the guide.xml will be stored. In WebGrab ++. Config.xml, leave the repository path set as is.

Code:

-----------------------------------------------------------------------------------------------------------------------------------------------

    docker run -d \
     --name=webgrabplus \
     --hostname="Your WebGrab+Plus registered name" \
     --mac-address="MAC address of your (already) registered PC at WebGrab+Plus" \
     -e PUID=0 \
     -e PGID=0 \
     -e TZ=Europe/Amsterdam \
     --restart unless-stopped \
     -v "/storage/wg++/config/":/config \
     -v "/storage/wg++/data/":/data \
     linuxserver/webgrabplus:3.2.3
  
------------------------------------------------------------------------------------------------------------------------------------------------                    
You can change the time zone according to your location. It must be spelled correctly!
Check the correct zone name at:
https://en.wikipedia.org/wiki/List_of_tz...time_zones 


-or-

# Install Script

Edit the information in the script

    --hostname="Your WebGrab+Plus registered name" \
    --mac-address="MAC address of your (already) registered PC at WebGrab+Plus" \
 
Save and EXIT.
 
Copy to "storage" 

Create an executable file:
     
     chmod +x WebGrabPlus_install
     
   Run script:
     
     ./WebGrabPlus_install

# WebGrab + Plus (LinuxServer.io)

You can also install WebGrab + Plus (LinuxServer.io) from the "LinuxServer.io's Docker Add-ons" Repository.

However, you must first change the version from "latest" to "3.2.3"

In the folder

        /storage/.kodi/addons/packages/

You need to edit one script in

     docker.linuxserver.webgrabplus-2.1.0.zip

in folder "bin" is script 

    docker.linuxserver.webgrabplus

in line 24 - version needs to be added. ": 3.2.3" 

     ...........  docker pull $DOCKERIMAGE":3.2.3 ..........

and

in the last line 40 it should be changed from 

    :latest  to  :3.2.3 

That is all. Then it will install version 3.2.3 and not the last one. 4.2.2 which has a problem grabgrab from some sites.


# The issue with 4.x versions has been fix in V4.2.2.5 if u prefer to use dotnet


https://github.com/SilentButeo2/webgrabplus-siteinipack/tree/master/eval...

