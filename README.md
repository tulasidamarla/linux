# linux

Linux
-----
Linux operating system is open source unix like operating system found in 1991 by Linus Torvalds. It has nothing to do with unix. It is not a derivate of Unix. Because of many commands of Linux are like Unix, people have thought it is derivate of Unix, but it is not. In earlier days, unix was licensed OS. So, Linux is the first open source OS distro(distribution). Many organizations, educational institutions have modified linux as per their need. Most popular linux OS in the market are Redhat, SUSE, debian, fedora, ubuntu, DSL(damn small linux with a size of 53mb). 

Most of the Linux distributions have two versions like Server and Desktop. Mostly, server versions are stripped down versions(without GUI and without many other features) because you know what needs to be installed as per the need.

Root
----
Root is the highest level. 
1)If you login with "root" username, you have logged in as the highest level admin.
2)Root for the OS is the highest level where OS is installed. For windows, it may be "C:\". For Linux may be "/".
3)For users, root is the highest level an user can get into. In linux users have home directory as the root. For ex, for if username is "app", root may /app.

Capitalization
--------------
In Linux, everything is case sensitive. For example the directory home and Home are not same unlike windows. It is because Linux uses ascii characters, so h and H are different.

Installing applications
-----------------------
Ubuntu uses apt-get to install applications, where as Redhat and fedora uses yum.

Note: Server versions of linux are meant to be like dbservers, apache web servers etc. They are not meant to be like desktop using chrome to browse websites.

Why server OS's are barebone?
Ans: Any OS with applications is an opportunity for hackers. Server OS generally won't come with any applications unlike desktop because it is intended for hosting different kinds of server applications. For ex, Mac os is so secure, but people have findout a hacking possibility with mac version of adobe software.

SUDO(Super user do)
-------------------
All Linux or unix systems have an administrator with root access. They can do anything on the computer. 

Ubuntu does not login anyone as root. So, any user who wants to run as an administrator need to add "sudo" before the command, which means super user do.

Man pages
---------
It stands for manual pages. It gives information about all commands existing in the system. Usage: man {command}. use 'q' to quit the man page.

tasksel --> It opens a page which contains predefined collections of software to install like Email server, LAMP(Linux apache mysql php) server, Postgre database etc.

Installing applications
-----------------------
There are repositories from which we can install softwares. So, when you use sudo apt-get install {appname} command, it hits repository and downloads the software and install.

For ex, to install apache webserver,

sudo apt-get install apache2


Removing applications
---------------------
sudo apt-get remove {appname}.

For ex, sudo apt-get remove apache2

To Upgrade existing softwares
-----------------------------
sudo apt-get upgrade

Services
--------
After installing software servies, you may have to change some configuration. Post configuration change, to reflect those change you may need to restart the service. Similarly, you may need to stop/start services when needed. To do that,

sudo /etc/init.d/apache stop
sudo /etc/init.d/apache start
sudo /etc/init.d/apache restart

top
---
top command is like windows task manager. It displays information like pid, start time, memory usage, cpu usage etc. If you try top command it opens a console with all the tasks detail. If you want to know the options available, type 'h' and enter. This gives list of all available commands. come out of the help window and try the commands.

Basic navigation
----------------
Use cd command for basic navigation. cd means change directory. 
cd / -> navigates to root directory.
cd /etc/init.d -> navigates to init.d directory under etc under root.
cd - -> navigates to previous directory.

Vim editor
----------
In Unix/Linux, there won't be any file extensions. To open any file as an administrator you should know what type of file and how to open it. To open configuration files or other types of text files, there are lots of tools available like vi, vim etc.

To create a new file or to open a file using vim editor-> vim {filename}

Sometimes, you may not be able to open some configuration files if you don't have permission. you need to change the ownership of the file. For this.

sudo chown {username} {filename}

Editing and Searching
---------------------
When we open the file using vim editor, by default it's in read only mode. 

To go to insert mode user the command i or a.
To come out of the insert mode use Esc command.
To search for a text, come out of edit mode and try the command :/{searchtext}. This command searches from your current position to the bottom of the document.
To try search from the cursor position to the top :?{searchtext}

If you are already on the vim editor and want to switch to another file without existing, use the command :e {filename}.
To exit vim use the command -->  :q
To force exit vim use the command --> :q!
Note:
Using q will not save file contents.

To save the file contents and exit use the command --> :wq

To make the changes to a file and save as new file use the command  --> :w {newfilename}. Now to exit the new file use :q command.

List files
----------
To list files use the command ls.
ls -l -> list of files in longer format. It displays user permissions, user details(user who owns the file/directory), group details(group that owns the file/directory), date modified, users who own that etc.
ls -lt -> list of files in longer format and in descending order of date/time modified.
ls -ltr -> list of files in longer format and in ascending order of date/time modified.
ls -m -> list of files in a comma seperated string.

Search files
------------
To search for files use the command find.

To look for files in the current directory or sub directories use the command -> find -name {filename}.
Note: The filename is case sensitive. If you want it to be case insensitive use the command -> find -iname {filename}.

To look for files in a specific directory path use the command -> find /requiredpath -name {filename}.

Note: you can do wildcard search like "find -name *.conf". If wildcards throw an exception, please use escape character \ before *.

Create/Delete/Move directories
------------------------------
To create directories use the command --> sudo mkdir /path/to/directory/{dirname}.
To remove directory use the command --> sudo rm {dirname} -R.
Note: -R to remove all subfolders/files recursively. If you want to remove a file the same command can be used, but without R.
 
To move/rename files you can use the command --> sudo mv /frompath/{sourcefilename} /topath/{destfilename}

To move directory, use -R with the above command.

Note: If both sourcefilename and destfilename are same, then it's a simple move. If they are different, then it's a move along with renaming.

Copy a file
-----------
We do copy files to not make any changes to the original file. For this, use the command -> sudo cp /frompath/{sourcefilename} /topath/{destfilename}.

To copy directories, use -R with the above command.

Mounting Drives
---------------
If you have external hard drive, and if you want to plugin, it should be mounted. In linux, any drive that you want to plugin like flash drive, CD ROM etc have to be mounted.

In Linux, to mount a drive, you first need to create a directory and then you point that directory to that drive. For this, use the following command.

sudo mkdir /mnt/{drivename} --> In linux, it is a general convention to mount all drives under one directory, say /mnt. For ex, you want to mount two external drives say myharddrive, mypendrive. For this use the below commands.

sudo mkdir /mnt/myharddrive 
sudo mkdir /mnt/mypendrive

Now, find the information about the drives. For this use the command,

fdisk -l --> This displays the physical drives that are connected to your system at present.

The fdisk command, returns output something of the format /dev/sda1, /dev/sda2 etc.

To mount the drive now use the command,

sudo mount /dev/sda2 /mnt/myharddrive

For reading cdrom, in ubuntu it is loaded at /dev/cdrom. Now, to mount this use the command.
sudo mount /dev/cdrom /mnt/mycdrom.

Note: Now you can get into mycdrom directory and access it like any other directory.

Unmounting
----------
Once you are done with using your mounted drive, before removing the drive, it is safe to unmount the drive first. For ex, to unmount the cdrom from the above example, use

sudo umount /dev/cdrom

After unmounting, go to /mnt/mycdrom and try "ls" , now you see no files or directories.

Users, Groups and Permissions
-----------------------------
If you want to see all the users in the system, use the command "cat /etc/passwd". This will list users along with their details like home directory etc. If you want, you can edit the /etc/passwd like changing the username. 

Add user --> sudo adduser {username}

This commands prompts to enter password/re-enter password and other details like full name, room number, phone number etc.

Delete use --> sudo userdel {username}

To change password --> sudo passwd {username}

User groups
-----------
In linux world, changing user permission is easy, but in real world we generally have large no of users and changing permissions to each one of them is not easy. So, we use usergroups to add users into the group and changing permissions to the group. 

To create a group --> sudo groupadd {groupname} --> For ex: sudo addgroup mygroup
To delete a group --> sudo groupdel {groupname}

To add an user to the group --> sudo adduser {username} {groupname} --> For ex: sudo adduser tulasid mygroup
To remove an user from the group --> sudo deluser {username} {groupname}

Note: The above command "deluser" is to delete user from group, this is not same as deleting user. The command for this is "userdel".

To see users information with associate groups --> sudo cat /etc/group.

Permissions
-----------
In unix/linux permissions are represented by 3 digit numbers like 755, 777 etc. The first digit represent the permissions of the owner, second represent permissions for the members of the group and third represents for others.



















