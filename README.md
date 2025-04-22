Exp 6 :Locate the Files 

AIM:
To find the owner of the file sarah and copy the file to the given path of /root/find.user. 

EQUIPMENTS REQUIRED:
Hardware: Minimum 4 GB RAM and 25 GB storage – essential for running services like Cockpit and handling system updates smoothly.
Software: Red Hat Enterprise Linux (RHEL) or any open-source Linux OS like Fedora or CentOS Stream – used for system administration and repository creation.

PROCEDURE & COMMENTS:
Opening a terminal 
The first line [root@servera ~]# shows that the user is logged in to the server with the username root and is currently in their home directory (~). This indicates the user is logged in with administrator privileges. 
Creating a directory
The second line mkdir /root/find.user creates a new directory named /root/ find.user. The mkdir command is used to create new directories. In this case, the new directory is created in the root user's home directory (/root).

Finding user files
 The third line find / user sarah -type f searches for files owned by the user sarah throughout the entire file system (starting from the root directory /). The find command is a powerful tool for searching for files and directories based on various criteria.
 Here's a breakdown of the options used with find:
 • /: This specifies the starting directory for the search (the root directory in this case).
 • user sarah: This searches for files that are owned by the user sarah.
 • -type f: This option tells find to only search for files (as opposed to directories). 
4. Potential error handling 
The lines find: '/proc/1146/task/1146/fdinfo/5': No such file or directory and find: '/proc/1146/fdinfo/6': No such file or directory are informational messages. The find command is reporting that it encountered errors while searching for files in /proc/1146/task/1146/fdinfo/5 and /proc/1146/fdinfo/6. These directories are part of the process file system, a special file system used by the kernel to store information about running processes. It is common for find to encounter errors while searching in these directories because they are dynamic and constantly changing.
The line find: '/proc/1147': No such file or directory is another informational message from find. It is reporting that it could not find a directory called /proc/ 1147. This could be because there is no process with that ID currently running on the system. 

5. Finding additional user files 
These errors do not prevent the find command from continuing its search. The output shows that the find command successfully found several files owned by the user sarah in other locations on the system:
 /var/spool/mail/sarah
 /home/sarah/.bash_logout 
/home/sarah/.bash_profile 
/home/sarah/.bashrc 
6. Copying files 
The line find / user sarah -type f exec cp {} /root/find.user \; copies all the files found by the find command in the previous step to the new directory /root/find.user. 
Here's a breakdown of this command: 
• find / user sarah -type f: This is the same part of the command from the previous step that searches for files owned by the user sarah. 
• exec cp {} /root/find.user \;:
	◦ exec: This keyword tells the find command to replace itself with the following command for each file that is found. 
	◦ cp {} /root/find.user: This is the command that copies each file
		▪ {}: This is a placeholder that is replaced with the actual filename found by find. 
    /root/find.user: This is the destination directory where the files will be copied. 
   ◦ ;: This terminates the exec command.  
7. Listing the contents of the directory
The last line ls -a /root/find.user/ lists the contents of the directory /root/ find.user. The ls command is used to list files and directories. The -a option tells ls to show all files, including hidden files.  
The output .bash_logout .bash_profile .bashrc sarah shows that the four files found by find were successfully copied into the directory /root/find.user. 

EXPECTED OUTPUT:
![OSOS_EXP_06](https://github.com/user-attachments/assets/b55c4dbb-90e9-4c8b-b712-1af1d2c9eb98)

RESULT:
Thus the owner has been found and the file has been copied successfully. 
