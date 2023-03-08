# What is Linux?

##### Linux is a popular operating system that is based on the Unix operating system. It has many distributions that have different interfaces for installing software, different user interfaces, etc. One thing that all 'distros' have in common is that they all have a command line interface, or terminal. In fact, sometimes there is no user interface at all except the terminal itself. A Linux server running a web application on AWS, for example, might contain only the software needed to run the application, and no graphical user interface at all. It is crucial to learn the Linux command line if you are going to be a productive Linux user and/or administer a Linux server.

### Help commands

| Sintaxis | Explanation |
|-----------|-----------|
| info | Self explanatory general information. Overly detailed; Sorts commands by utility. |
| man <command> | Complete manual (or almost complete) on a command. There is a manual for the man command itself, accessed by man man |
| <command> --help | Basic help on a command (not all offer it) |
| <command> --usage | Basic syntax on a command (not all offer it) |
| whatis <command> | Very little information about a command |
| apropos <command> | Parecido al anterior |

### Folder and file management

| Sintaxis | Explanation | Example |
|-----------|-----------|-----------|
| dir | lists the files (referring to all types of files: directories, files themselves, symbolic links, etc.) |  |
| ls [-a] [-l] | visualizes the files and folders in colors to distinguish the different types. -a reflects hidden files, which start with a dot in their name; they do not normally appear either on the console or in graphical mode. -l gives extra information about the files instead of just writing the names. |  |
| touch <path> | change the metadata (date, creation time) or create blank files | touch -t 03122010 file21.txt touch file21.txt |
| mkdir <path> | create directories | mkdir ~/This\ is\ not\ private |
| cd <path>	 |  | coque@sarricolea:~$ cd Documents |
| cd ..	 | always change to the directory immediately above it. don't paste dots to the command like in MS-Dos! It won't recognize the command | coque@sarricolea:~/Documents/examples$ cd .. |
| rmdir <path>	 | allows you to delete an empty directory | cp -r /home/task /root/path |
| cp <source> <destination> | copies the file or directory <source> to <destination> | mv Istory History |
| mv <source> <destination> | allows moving and/or renaming the file <source> to <destination> | rm /home/task rm -r /home/Task |
| rm [-i] [-r] <branch> | it does not move to the trash, it permanently deletes the files. In principle, it deletes files one by one to delete an entire folder you need to delete the files inside first, either by hand or with the -r option (recursive; deletes everything inside) the -i option makes it ask for confirmation before delete, very convenient if used with the -r option |  |
| cat <path> | view content of a file; several can be concatenated the visualization is done without pause; if the text is longer than the screen it cannot be retrieved. | cat /etc/passwd |
| more <path> | a more advanced way of reading a file, pauses at each line. It can be read by pressing enter repeatedly (or space to skip screens) |  |
| less <path> | an even more advanced way of reading a file, allows you to scroll through it with the arrow keys. Press Q to quit |  |
| pwd | show current path | coque@sarricolea:~/Docs$ pwd   /home/coquesv/Docs |
| du | Shows disk usage. In general, files are stored in blocks of 4KB/4096bytes. If a file is smaller it will still take up 4K of disk space. du indicates the actual occupancy. | /var/log@Host1 # du -sch * |
| find | Command to search for files. It has dozens of options that make it extremely powerful. | Look for symbolic links inside /etc: find /etc -type l     Search for files modified 10 days or less ago: find /etc -type f -mtime -10     Look for files modified exactly 10 days ago: find /etc -type f -mtime 10 |
| df pydf | df disk free, shows the free space left on the disk. pydf (pydf == python disk free) performs the same task but sorting in columns and with colors. df is useful for automated scripts while pydf is better for manually viewing consumption. |  |

### Backups
  
| Sintaxis | Explanation | Example |
|-----------|-----------|-----------|
| rsync | It allows you to synchronize folders locally or on a remote system accessible via a network, perform incremental backups and snapshots (similar to MacOSX's "Time Machine" system) of a folder or directory. rsync checks before copying a file that it doesn't already exist on the destination, it checks if there were changes and if there were, it copies only the part of the file that changed. This verification can greatly multiply the speed of synchronization (up to 10 times in local copies and up to 1000 in copies through WAN networks -ADSL for example-). | Hard links allow access to a file from several alternative paths, in this case from .../mysql.201001/path1 and .../mysql.201008/path2. When we delete the file from a path with rm, the file is still accessible from the rest of the paths or hard links. When the last hard link is removed the file is removed. With this technique we can create snapshots of a directory as it was on a given date while the space occupied on disk is similar to an incremental copy, since between one date and another only the files that have changed are stored. |
  
### Related to permissions and users
  
| Sintaxis | Explanation | Example |
|-----------|-----------|-----------|
| passwd [-d] [<user>] | substituting user for the username (or not typing anything for the user running the command) allows you to change the password, or set a new one if you don't have one. The -d option allows you to delete it, leaving the account without a password (dangerous). Only the superuser can change passwords other than their own. In case of error the password will remain unchanged. | coque@sarricolea:~$ passwd Changing the password for marivi. (current) UNIX password:   Enter new UNIX password:   Retype new UNIX password:
It is understood that the blank spaces are for typing the passwords, as is the custom in GNU/Linux they will not appear on the screen when typing them. |
| chmod <permissions> <path> | change the access permissions to a file. Permissions can be given by an octal number or by the notation <affected users <grant mode <permissions> | chmod a=rwx konquest   Allow all users to read, write and execute konquest   chmod u-wx konquest   The owning user is denied the ability to write or run konquest |
| chown <user>[:<group>] <path> | changes ownership of <path> in favor of user <user>, also changing the owning group to <group>, if specified | chown task:Docs History |
| sudo <command with options> | run a command with root privileges; For it to work it is necessary to enter the password of the current user | kant@kant:/etc/ sudo cp fstab fstab~
[sudo] password for kant: |
| your [<user>] | Change of user (it is necessary to enter the password of the new user). If it is not marked which user to change to by default, try changing to root. Curiosity: you can change to root user with the password of the normal user using sudo su |  |
| gksu <command> | graphical version of sudo | A window will appear to enter the password, if it is entered correctly the kate /etc/fstab command will start with superuser permissions, loading its configuration and allowing that file to be opened and modified, with restricted permission. The above example only works for Kubuntu or a system that includes the kate file editor; In any case, the operation of the gksu command is the same. |




