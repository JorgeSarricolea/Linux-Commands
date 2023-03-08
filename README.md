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

| Sintaxis	 | Explanation | Example |
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
| du | Shows disk usage. In general, files are stored in blocks of 4KB/4096bytes. If a file is smaller it will still take up 4K of disk space. du indicates the actual occupancy. | /var/log@Host1 # du -sch *
20K      acpid
0        apache2
0        auth.log
324K     cron
2,1M     cups
108K     daemons
4,0K     incrementalBackup.sh.root.20100101.log
4,0K     incrementalBackup.sh.root.20100102.log
4,0K     incrementalBackup.sh.root.20100103.log
56K      mail
0        maillog
128K     messages
1,2M     messages.1.gz
3,7M     messages.2.gz
2,5M     msec.log
35M      mysqld
...
111M    total |
| df pydf | df disk free, shows the free space left on the disk. pydf (pydf == python disk free) performs the same task but sorting in columns and with colors. df is useful for automated scripts while pydf is better for manually viewing consumption. |  |
| find | Command to search for files. It has dozens of options that make it extremely powerful. | Look for symbolic links inside /etc:
find /etc -type l
Search for files modified 10 days or less ago:

find /etc -type f -mtime -10
Look for files modified exactly 10 days ago:

find /etc -type f -mtime 10
Looks for files modified 5 or more days ago within /etc with name extension sh or php and on each match executes a new script passing the name of the found file as a parameter. ('{}' is replaced by the name of the found file.) .

find /etc -type f -name "*sh" -or -name "*.php" -mtime +5 -exec script1.sh {} \;
For the latter case, we can use an inline script by replacing -exec script1.sh {} with a statement similar to

-exec bash -c " echo \"File:{}\" ; grep \"pattern1\" {} ; wc -l {} " |





