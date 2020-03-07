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

Each number is any combination of read, write and execute.

Read -> 4
Write -> 2
Execute -> 1

If you want  read and execute, it should have permisson number as 5(4 + 1).
If you want read and write, it should have permission as 6(4 + 2).
If you want only execute , it should have permission number of 1.

Note: Generally read and execute are the common permissions given to group and other users. i.e. 5.

Change permissions
------------------
To change the permissions for a file use the command --> sudo chmod 755 filename . 

Note: The same command works for directories also, but permission level for subdirectories and files will not change. To recursively apply permissions to directories use "-R".

Change Ownership
----------------
To change the user ownership of a file ->  sudo chown {username} {filename}. For folder use "-R".
To change the group ownership of a file -> sudo chgrp {username} {filename}. For folder user "-R".

Linux Network Configuration
---------------------------
The command "ifconfig"(ipconfig equivalent in windows) gives all the network cards information. It gives information like network card1, network card2, mac address etc.
Here is the sample output:

eth0      Link encap:Ethernet  HWaddr 12:5d:28:6d:79:57
          inet addr:172.31.80.133  Bcast:172.31.95.255  Mask:255.255.240.0
          inet6 addr: fe80::105d:28ff:fe6d:7957/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:296535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:374490044 (374.4 MB)  TX bytes:15989071 (15.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:14456 (14.4 KB)  TX bytes:14456 (14.4 KB)

Note: we have one network adapter as per the above response. i.e. eth0. inet address is 172.31.80.133.

If you want to release your ip address and want to renew your network configuration with new ip address --> sudo dhclient

Note:
Dynamic Host Configuration Protocol (DHCP) is a protocol for assigning dynamic IP addresses to devices on a network. With dynamic addressing, a device can have a different IP address every time it connects to the network.

If you change the networking configuration files in anyway, you need to restart the networking service. For this, use the command

sudo /etc/init.d/networking {stop/start/restart}

Network configuration
---------------------
In Linux network configuration file is /etc/network/interfaces. This is the file that controls the ipaddresses for the network cards on the system. Here is the file in from the aws ec2 instance.

			# This file describes the network interfaces available on your system
			# and how to activate them. For more information, see interfaces(5).

			# The loopback network interface
			auto lo
			iface lo inet loopback

			# Source interfaces
			# Please check /etc/network/interfaces.d before changing this file
			# as interfaces may have been defined in /etc/network/interfaces.d
			# See LP: #1262951
			source /etc/network/interfaces.d/*.cfg

Note: The loopback device is a special, virtual network interface that your computer uses to communicate with itself. It is used mainly for diagnostics and troubleshooting, and to connect to servers running on the local machine.

So, if you want your computer get a dhcp address, you just need the below two lines.

	auto lo or auto eth0
	iface eth0 inet dhcp

The rest of the configuration comes automatically from dhcp server. If you want to give a static ipaddress, you need to configure address,network,broadcast,gateway etc like below.

auto lo or auto eth0 --> It means auto decides(negotitates) network cards either 10mbps,10gbps etc.
iface eth0 inet static --> It means this is a static ip address.
address xxxx -> This is the ipaddress.
netmask --> This is the subnet mask.
network xxxx -> This is the network address. For ex, if ipaddress is 10.0.0.9, network would be 10.0.0.0.
broadcast xxxx -> This is the broadcast address. For ex, if ipaddress is 10.0.0.9, broadcast ad would be 10.0.0.255. This represents the is the address range that this computer sends a message to every other computer on the same network.
gateway --> This is the router/modem address using which you interact with outside world.

Note:
Any changes done to this file or other networking, don't forget to restart the service as described in the above section.

DNS configuration
-----------------
If you want to put a static ip address for configuration of dns, interfaces file doesn't have configuration for this. This information is present in /etc/resolv.conf.
It has entries in the below format like windows hosts file. 
{dnsname} ipaddress

To check the hostname of your computer,

sudo /bin/hostname

If you want to change the hostname,

sudo /bin/hostname {newName}

Note: You need to restart the network service after changing hostname.

Ping
----
Generally, routers are present at 10.1.10.1. If you use "ping 10.1.10.1" it responnds. But, if you get "destination not found", there is an issue connecting to router. 
This could be due an issue in interfaces file having wrong address or your network cards disabled or due to some other reason.

Ping {domainname} --> For ex: ping google.com

If ping {router} is working fine, but ping google.com is not working properly, then there is an issue with dns configuration. So, you need to get into resolve.conf and change dns server configuration.

UFW firewall
------------
To check the status of firewall, "sudo ufw status".

If you want to configure your firewall(either to allow all or block all) --> "sudo ufw default allow" or "sudo ufw default deny".

To turn on/ turn of, firewall -> sudo ufw enable/disable.

To create a rule
----------------
To allow/deny port ranges -> sudo ufw allow/deny 80.
To allow/deny traffice from specific ip addresses -> sudo ufw allow/deny from 207.120.156.255
Allow/deny from specific ipaddress to a port ->  sudo ufw allow/deny from 207.120.156.255 to any port 22

Note: any in the command represents all protocols.
Note: If you want to do the above for a set of ipaddresses, you need to execute the command multiple times.

To delete a rule
----------------
sudo ufw delete allow/deny 80
sudo ufw delete allow/deny from 207.120.156.255

The above commands allow wildcards also. For ex: sudo ufw allow/deny from 207.120.*.*

SSH and FTP
-----------
SSH
---
Using SSh and FTP we can remotely administer our linux server. By default ssh is installed in ubuntu. If not install ssh using 'sudo apt-get install ssh'. It's a networking service. It runs on port 22. If port 22, is not enabled enable it using above firewall setting.

Once ssh is enabled, get the ipaddress or dns name(if available over internet), and connect to your linux machine using softwares like putty.

FTP
---
FTP is for uploading and downloading files to your linux server. For this your linux server should have vsftpd(very secure file transfer protocol daemon) installed.
To make ftp work propertly, you need to change some configuration. The configuration for this software is present at the location /etc/vsftpd.conf. The following settings need to be available. By default, FTP runs on port 21.

a)local_enable=YES
b)write_enable=YES --> This says, people can write to server. By default, all users have read access to download files from linux server.

Followed by those changes, we need to restart service --> sudo service vsftpd restart.

From the remote machine to access your linux server you need a ftp client. For windows we use winscp or filezilla etc.

Linux Backup with tar and Cron jobs
-----------------------------------
Tar means tape archive file. We can take linux backup in tar files. It is generally used to collect a large no of files and placing them into one easily distributed archive file.

Cron jobs allow us to schedule tasks. These jobs we can configure to take backup of your linux system. These jobs can be used to schedule many other tasks.

By default tar is installed in your linux system. If not, install tar using --> sudo apt-get install tar.

Creating backup 
---------------
sudo tar -cvpzf mybackup.tar.gz --exclude=/mnt / 

c -> create(
v -> verbose(Displays console messages of what is happening)
p -> preserving permissions.(If you don't use p the once file generated, you will not have any permissions on the files that you are preserving.)
z -> compression(once tar file is created, this compression will help to reduce the size as much as possible)
f -> file(To give a filename)
exclude --> To exclude everything inside /mnt directory because these are external drives
/ -> root directory

So, the above command takes a backup of everything in your server except /mnt directory. 

Note: The command is recursive, you don't need to mention -R. Also, we know that linux doesn't care aboue file associations/extension like .tar.gz, but this is for us to identify what that file is.

Recovery from backup
--------------------
sudo tar -xvpzf mybackup.tar.gz -C /recovery

x -> for extracting
C -> extract to a different new directory, so that it will not override anything in the current system.

Note: Most of the times, if the file is not a compressed one, we don't use z. Also, if you don't want any verbose output, we don't use v. All other paramerters like c,v,p,f,x are mostly used every time.

Cron Job
--------
To create a crontab, use the command "sudo crontab -e". If you type this command for the very first, it will ask you to open this with editor of choice. Choose an editor.

The last line you will see will be like this.

	m h  dom mon dow   command
	To define the time you can provide concrete values for minute (m), hour (h), day of month (dom), month (mon), and day of week (dow) or use '*' in these fields (for 'any').

Valid values 
------------
m -> 0-59 <br>
h -> 0-23<br>
dom -> 1-31<br>
mon -> 1-12<br>
dow -> 0-6<br>

For ex, if you want to setup a cronjob for recovery task every day, midnight
	
	0 0 * * * sudo tar -cvzpf /home/ubuntu/mybackup`date +\%d-\%H:\%M`.tar.gz /var/www/

To understand date, please refer to the link https://devanswers.co/how-to-automatically-backup-web-server-doc-root-tar-cron/
