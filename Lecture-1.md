#Lecture 1 Day 1#
**Bash Born Again Shell
Initiallly in bash shell we got the Username@ServerName

-Once the System Login it open first of all the /etc/profile
*It set all the env variables,paths and history sizes in linux*

-when the /etc/profile runs itself then the remaining scripts are run inside the profile.t. The profile.d is available in /etc/profile.d
*In profile.d there is setting of colors,cvs,gnome are available

-After the profile.d is run the next script is run in the user home directory and this script is known as .bash_profile and this modfiy serveral env variable come from profile.d here we can create our custom variables too

-After this file run then the .bashrc file is run. This is also in the user home directory and it set our local command and variables and we can amend our command prompt feel here from this file

After the .bashrc the next file which run is /etc/bashrc **

#User Creation,Deletion,Modifying#

##How to add a new user##
-useradd asim
*By running this command a new user is added but this user will not be able to logged in because the password is not yet set.

#How to delete a user#
-userdel -r asim
*Here the -r act as a recursive delete which means The user its home director the data in the directory and including mailbox everything will be lost.

#If we want to add a user and also all the Caption which is showed during login 
-useradd -c "Muzamil" muzamil
*Now the new user muzamil will be added with the name caption "Muzamil" *

#By default every user has a bash shell after login but what if we dont want to give the user a shell or change default shell#
-useradd -s /bin/tsch  Sami
*Now when the sami logged in he will always got the tsch shell after login*

#When a new user is created by default it got a dir in /home but if we want to add a custom directory3
-useradd -c "Fawad" -d /home/admin/fawad fawad
*Now when the user fawad is created it's directory is created in the /home/admin/fawad

##When ever you want to edit any user details##
-usermod -c "Asim Kamal Khan" asim
*Now you dont need to delete and again create the user and add the para's you can usermod and set the caption,directory,shell..etc*

##How can we add a password to user the user be able to logged in##
-useradd -p 88qw123 user9
*By using this method the password will be added but this is not the right approach to write password in the shelll openly

##How to lock the user so the login is disabled
-passwd -l user9
*Now the user is created. Have a shell,home directory but the passwd is locked so it is not allowed to login*

##To unlock the user back##
-passwd -u user9

##To enforce the user to change password after the given interval##
-chage -M 90 user9
*Now the user9 will have to change the passwd after 90 days if the passwd is not changed the account will be locked*
#To give warning to the user for this expiry message#
-chage -W 3 user9
*Now the user will get warning just before 3 days to change your password*
#To check the details of Expiry and warning we use#
-chage -l user9

##To expire an account and set the expiry date we use ##
-chage -E 2026-10-28 user9

##The file where all this information is stored is /etc/passwd##
-less /etc/passwd
*The format there is like this root:x:0:0:root:/root:/bin/bash
username:x shows that a passwd is attached:uid:gid:caption:home directory:shell
#The next file is /etc/shadow#
*Here all the hashes of the passwords are stored and the ! there in the entry shows that this user don't have a password yet
#The next file is /etc/group#
*Here the information of the primary and secondary groups are available*
#The next file is /etc/groupshadow#
*This file is useful when you set password to the group*

##To get help in the Linux ##
-man command | man ls
*If want to take help for any command just type man in start of that command*
#To see the more info with proper dir's available explore the path /usr/share/doc#


##Shutting down the server##
-shutdown -r +5
*This means to restart the server after 5 min of shutdown*
#But what if you change your mind and dont want to shutdown#
-shutdown -c 
*By using this command the shutdown process is terminated*
#Broadcast message to all the users that the system is going to shutdown at this specific time#
-shutdown -h 22:00 "System will not be able after 10 PM"
*With This command the system will send message to all the users that the sever is not availeable after the 10Pm*
