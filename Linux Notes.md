# Ubuntu Notes

Install Java 8
--------------

Install Java 8
This link
[https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04)

Then this link to set environment variables.

[http://askubuntu.com/questions/175514/how-to-set-java-home-for-java](http://askubuntu.com/questions/175514/how-to-set-java-home-for-java)

Install Git
-----------

Install GIT
[https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04)
sudo apt-get update 
sudo apt-get install git
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"

Install Node.js
---------------

Install Node.js
[http://www.hostingadvice.com/how-to/install-nodejs-ubuntu-14-04/#node-version-manager](http://www.hostingadvice.com/how-to/install-nodejs-ubuntu-14-04/#node-version-manager)


Install MySQL
-------------

See this link:
[https://www.digitalocean.com/community/tutorials/how-to-install-the-latest-mysql-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-the-latest-mysql-on-ubuntu-16-04d)

To test it is up and running:
`mysqladmin -u root -p version`

To get list of ports etc from sql server:
`mysql SHOW GLOBAL VARIABLES LIKE 'PORT'`

also:
`ps aux | grep mysql`

also list of verbose parameters:
`mysqld --verbose --help`

To restart mysql server:
`sudo /etc/init.d/mysql start`

To set old password types:
[mysqld]
default-authentication-plugin=mysql_native_password

Log into MYSQL from command line
`mysql -u root -p`

Can then type SQL commands
`Create user 'john'@'localhost' IDENTIFIED WITH mysql_native_password BY 'pass';`

For setting up Spring projects to use MySQL.  This will allow new Spring users to be entered.
sudo mysql --password
    




Upgrade IntelliJ 
---------------

Minor versions will be in place upgrades.  

For major releases, download the latest .tar.gz file from the IntellJ site
`https://www.jetbrains.com/idea/download/?fromIDE=#section=linux`

Unpack tar file into opt directory, e.g. to unpack IntelliJ idea (with SUDO permissions)
sudo tar xvzf ideaIU-2017.2.5.tar.gz -C /opt/IntelliJ

Change the launchsript to point to new IntelliJ
`gedit /home/john/bin/launchsript`

`To remove old version of IntelliJ (and force the delete without prompt every time)`
rm -rf mydir  

Also need to update the desktop shortcut icon.  Do this within applicaton 
Tools --> Desktop entry


General Stuff
-------------
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

File Permissions
----------------
To give permission to all files rwx in CodingNotes directoy:

`sudo chmod -R 777 CodingNotes/`

To Kill software on a particular port
-------------------------------------
`sudo kill $(sudo lsof -t -i:4200)`

Files
-----
Use `cat` to display contents of a file from 

Remove files and directories (with force remove)
----------------------------
sudo rm -fr mydir
 


