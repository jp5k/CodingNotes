# Ubuntu Notes

Install Java 8
This link
[https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04)

Then this link to set environment variables.

[http://askubuntu.com/questions/175514/how-to-set-java-home-for-java](http://askubuntu.com/questions/175514/how-to-set-java-home-for-java)

Install GIT
[https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04)
sudo apt-get update 
sudo apt-get install git
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"

Install Node.js
[http://www.hostingadvice.com/how-to/install-nodejs-ubuntu-14-04/#node-version-manager](http://www.hostingadvice.com/how-to/install-nodejs-ubuntu-14-04/#node-version-manager)



Scan for wireless networks
sudo iwlist scan    = useful for scanning wireless addresses

just type a program name to launch from terminal e.g. google-chrome

Ctl+Alt+T for terminal
System → Settings → Keyboards → Shortcuts for list of shortcuts

Windows key held down for all shortcuts 

ls /usr/share/applications/   to get list of all applications (typically have a desktop file)
just type in name of program to launch it (note when close terminal, this will clos program)

Click on dash, and type system monitor to see all processes running.

Press ALT to bring up HUD when in an application.  Can then type to get command you want.

Git repository
go to directory
git init
git clone https://github etc…

To move to USB, and track progress from downloads
rsync –info=progress2 ~Downloads/Sing.2017 /media/john/C6EC-C003/

echo $PATH   to get a list of all directories on your path. 


Unpack tar file into an opt directory, e.g. to unpack IntelliJ idea (with SUDO permissions)
sudo tar xvzf ideaIU-2017.2.5.tar.gz -C /opt/IntelliJ

Tomcat 
-------
Install Tomcat.  Be careful to ensure compiling and Tomcat version are all using the same Java version.
I had an issue with EccDeployer not having the correct spring beans in the deployer, and was getting a bad CEN 
signature.  Delete the files from the repository, and download again.


Oracle Database
---------------
To allow JOHN user to be able to create tables under SYSTEM database:

`alter user JOHN quota unlimited on system;`


To Copy Files from One Directory to Another
----------------------------------------------
sudo cp -a OriginalProject DestinationProject
-a will  copy all subdirectories and files underneath main folder