# Using Linux

Linux can be installed as bootable or using hypervisor mainly. Windows 10 now allows installing linux natively, The Windows Subsystem for Linux or WSL. Docker Engine is used for containerized workflow.

APT is the default package manager for LINUX. `apt-get` is CLI for APT package manager. Linux comes with Shell and/or GUI. Linux systems installed in server comes with onlu Shell by deauflt. 
`apt-get update` is used for synchronization of package index files from their sources again. 
`apt-get upgrade` is used for installing latest version of packages of the applications that are currently installed.
`apt-get install` for installing or upgrading package(s)
`apt-get remove` removes a package from the system
`apt-get purge` removes package as well as configuration files
`apt-get check` updates the package cache and checks for broken dependencies
`apt-get autoremove` removes pakcages that were installed as dependency of other packages and is not required anymore.
`apt-get --reinstall` removes and install the latest version of the package

`sudo` is for super user. It stands for **super user do!**. If current user does not have permission to do something `sudo` is the command to run the command as super user. Example, `rmdir test` if current user does not permission to delte the folder then **rmdir: failed to remove 'test/': Permission denied** is displayed. Current user does not have write permission on the current folder. But super user can do it all. `sudo rmdir test` does the job as this command invokes superuser insted of current user.

# Linux Directory Structure

Linux filesystem/directory structure is like a tree
1. **/** is the Root directory. This is the base of Linux filesystem hierarchy. 
2. **/bin** has the executable files. Here machine readable biaries are stored.
3. **/etc** has the configuration files
4. **/home** Home directory. It stores files for a given user of the system.
5. **/opt** Optional/third party software gets installed.
6. **/temp** Temporary space. Clear storage on boot.
7. **/usr** User related programs are stored here.
8. **/var** For variable data that are frequently change.

Some linux operating systems use **/srv** directory to store data that is served by linux. Example, **/srv/www** for web server files and **/srv/ftp** for FTP files.

Some applications that are not bundled with linux OS are installed in the **/usr/local**

The **~** directory means the user's home directory. Example, **/home/username/** is same as **~**

`.` means current directory and `..` means parent direcrtory.


# Shell

It is the **default interface** to linux. Also called the **Command Line Interpreter**. At the start shell diplays a promt/shell prompt. 

Linux shell is case sensitive. Using `CAT` insted of `cat` will not work.

Metacharacters are as follows (WSL does not support all metacharacters)

1. **`>`** Output redirection. Example, `pwd > command` creates a file named **command**. `cat command` displays the output of `pwd` 
2. **`>>`** Output redirection ??? append. Example, `echo $SHELL >> command` append `echo $SHELL` command output into **command** file
3. **`<`** Input redirection.
4. **`<<`** Input redirection.
5. **`*`** File substitution wildcard. Example, `ls -l Do*` will show list of contents of both Documents and Downloads 
6. **`?`** File substitution wildcard. Example, `ls t??t.doc` will show the file name **test.doc**. Any file or directory matches the pattern **t__t.doc** will be displayed as the two characters are matched using **?** wildcard.  
7. **`[ ]`** File substitution wildcard. `ls l[ai]st` will show **last** and **list** both
8. **`|`** Pipe for using multiple commands. 
9. **`;`** Command execution sequence.
10. **`( )`** Group of commands in the execution sequence.
11. **`||`** Conditional execution (OR).
12. **`&&`** Conditional execution (AND). `mkdir first && cd $_` second command `cd $_` will run only if first one runs.
13. **`&`** Run a command in the background.
14. **`#`** Use a command directly in the shell.
15. **`$`** Variable value expansion.
16. **`\`** The escape character.
17. **``cmd``** Command substitution.
18. **`$(cmd)`** Command substitution. Example, `a=$(ls -l)` stores the value of `ls -l` into variable **a**. To print the value of a, `echo "$a"` or `printf "%s", $a` can be used.
19. **`file`** command displays the type. `file CheetSheet/Typescript/README.md` shows the result **CheetSheet/Typescript/README.md: ASCII text** 

# Basic Linux Commands

1. `ls` 	- 	Lists the directory contents
2. `cd` 	- 	Changes directories
3. `pwd` 	- 	Displays the present working directory
4. `cat` 	- 	Caoncatenates and displays files
5. `echo` 	- 	Displays arguments to the screen
6. `man` 	- 	displays the online manual
7. `exit` 	- 	Exit shell or current session
8. `clear` 	- 	Clears the screen

Executing only `cd` will redirect to home directy of user **/home/username/** or **~**

`man ls` shows the details of ls command. Same way other commands can be used instead of `ls`. `--help` can be used **instead of `man`**. But not all commands supports `--help` 

`which` is used for locating the command. 
$`which ls`
: /usr/bin/ls 

Search main pages using `man -k` 

`echo` can display argument string or variables like **$PATH**. A **variable name** in linux is always in **capital** such as **VAR_NAME**. 

Use `cd -` to go to previous directory.

Use `echo $OLDPWD` to show previous **present working directory** directory.

If two commands with same name exists then the first command to in the `$PATH` variable will be executed. **/usr/bin** comes before **/usr/sbin**. If bothe have command `hello world` then command in **/usr/bin** will be executed. In order to run `hello world` in **/usr/sbin**, `/usr/sbin/hello world` has to be executed. Use `./hello world` to execute a command in current directory. 

Use `mkdir` to create a directory. To create **nested directories** use `mkdir -p`. `mkdir -p this/is/a/test` will create a directory structure of **this/is/a/test**.

Use `rmdir` to remove a directory. To remove **nested directories** use `rmdir -p`. `rmdir -p this/is/a/test` will remove a directory structure of **this/is/a/test**. If a directory has file(s) then rmdir will not work.

Use `rm -rf` rmoves the directory and all the files in it. `rm -rf` deletes only one directory. `rm -rf this/is/a/test` will delete only test and all the files in test directory.

# File Listing

`ls` for lisiting the names of files and directories. `ls -l` for long listing format. Long list formar has the follwoing information
1. The file type.
2. The file permissions **-rw-rw-r--**
3. Number of hard links to the file **1**
4. File owner **username**
5. File group **root/adminuser**
6. File size **28 in bytes**
7. Date and Time of last modification **Aug 30 04:03**
8. File name **sample.txt**

`ls` does not show hidden files. `-a` can be used for seeing all the hidden files. `-a` shows **. & ..**. To exclude these `-A` can be used.

`ls -F` shows the file types. Files can be of three types **directory**, **link** and **executable**.

1. Directory - **/**
2. Link - **@**
3. Executable - *

Some of the useful commands are as follows

1. `ls -r` show list in reverse order
2. `ls -t` most recently modified first
3. `ls -d` to show only directory names
4. `ls -R` subdirectories and files recursively
5. `ls -s` show the size in blocks
6. `ls -sh` show the size in human readable format
7. `tree` subdirectories and files recursively as a tree structure
7. `tree -d` to show only directory names

For directories and files named with **space** use the quotes. Example, `ls -l my notes` will not work but `ls -l "my notes"` will show all the subdirectories and files within "my notes". 

# Symlink

Symbolic link points to another file or folder in the computer. 

`ln -s <existing file/folder path> <path of symlink>` creates a new symlinc. `-s` stands for soft. Instead of `-s`, `-symbolic` can also be used.

Symlink can be removed using one of the three ways

1. `ls -l <path-to-assumed-symlink>`
2. `unlink <path-to-symlink>`
3. `rm <path-to-symlink>`

`find /home/user/Desktop -xtype l` finds the broken links.
`find /home/user/Desktop -xtype l -delete` deletes the broken links as well.

# File Directory and Permissions

Typical out put of `ls -l`

1. drwxr-xr-x 1 ritwik ritwik   512 Aug 27 23:08 first.website
2. -rwxr-xr-x 1 root   root   10918 Jun  1 01:36 index.html
3. lrwxrwxrwx 1 root   root      17 Sep  2 22:23 laravel -> /var/www/laravel/

The symbols **d**, **-**. **l** means **directory**, **regular file** and **symbolic link** respectively
The symbols **r**, **w**. **x** means **read**, **write** and **execute** respectively

### File
Read means user can see file's contents. `cat index.html` is allowed for the current user.
Write means file can be modified by curent user.
Execute means user can execute the file.

### Directory
Read means user can see dirctory's contents. If user does not have read permission then file names within the directory will not appear.
Write means contents cannot be added or deleted from the directory.
Execute means user can access contents and metadas for entires.

Permission categories can be of four types 

1. User (u)
2. Group (g)
3. Other (o)
4. All (a)

Everyh user has to be atleast one group. A user can be in many groups. Team lead can be in Team Leaders and Developers groups. 
`groups` or `id -Gn` shows the name of groups which user is member of. Example,

**-rwxr-xr-x 1 root   root   10918 Jun  1 01:36 index.html** in this long listing format of index.html, (from left to right) **-** means type, **rwx** means user permission, **r-x** means file's group permission and **r-x** means permission to other users. The **-** in user, groups and all user permission means specific permission is not given. Example, file's group and other users are not allowed to modify the file as write permissionis missing.

Permission can be changed using combination of **chomd**, **u(user)/g(group)/o(other)/a(all)**, **+(add)/-(substract)/=(equal)** and **r(read)/w(write)/x(execute)**. 

`$ ls -l test.data` creates a new file withe **-rw-r--r-- 1 root root 0 Sep  2 22:54 test.data** long listing format.
`sudo chmod g+w test.data` will add write permission to file's group.
`sudo chmod g-w test.data` will remove write permission from file's group.
`sudo chmod g=rw test.data` will set read and write permission to file's group.
`sudo chmod o= test.data` will set remove read, write and execute permission from others.

The Octal, Binary and String representation of permission for chmod are as following

1. **0** 	- **0** 	- 	**---**
2. **1** 	- **1** 	- 	**--x**
3. **2** 	- **10** 	- 	**-w-**
4. **3** 	- **11** 	- 	**-wx**
5. **4** 	- **100**	- 	**r--**
6. **5** 	- **101** 	- 	**r-x**
7. **6** 	- **110** 	- 	**rw-**
8. **7** 	- **111** 	- 	**rwx**

`sudo chgrp group_name file/directory` to change group of file/directory. **-rw-r--r-- 1 root   ritwik    18 Sep  2 22:55 test.data** will change group of this file to **ritwik** from **root**. 
`sudo chgrp -h ritwik laravel` will change teh group of symlink. As **symlinks are protected**, and you cannot operate on target files, previous command does not work on it.

The Octal, Binary, String Directory and String File representation of permission for umask are as following

1. **0** 	- **0** 	- 	**rwx**		- 	**rw-**
2. **1** 	- **1** 	- 	**rw-**		- 	**rw-**
3. **2** 	- **10** 	- 	**r-x**		- 	**r--**
4. **3** 	- **11** 	- 	**r--**		- 	**r--**
5. **4** 	- **100**	- 	**-wx**		- 	**-w-**
6. **5** 	- **101** 	- 	**-w-**		- 	**-w-**
7. **6** 	- **110** 	- 	**--x**		- 	**---**
8. **7** 	- **111** 	- 	**---**		- 	**---**

`chmod 0755` and `umask 0022` is same as `chmod 755` and `umask 022`. The **0** in the beginning is called setuid, setgid and sticky.

# Find

`find` command finds files **recursively** that match with the specified expression. If no argument is specified then all the files in current directory are returned.

`find` has few options as below
1. `-name` matches a pattern with case sensivity. Directories and files with matched pattern are returned. 
2. `-iname` matches a pattern ignoring case. `find ~/Documents/ -iname readme.md` finds files **README.md**.
3. `-ls` performs ls on each found files/directories. `find ~/Documents/ -iname readme.md -ls` performs `ls` command on found files.
4. `-mtime` is for finding files that are specific days old. `find . -mtime +5 -mtime -15` find files and directories in current directory that are **more than 5 days old** but **less than 15 days old**. 
5. `-size` find files that matches the file size. `find ~/Documents/ -iname readme.md -size +1k` finds the files named **readme.md** that are **more than 1 kb** in size.
6. `-newer` find all the files that are newer than specified file. `find . -newer CheetSheet/Typescript/README.md` find files that are newer than **README.md**. 
7. `-exec {} \` to execute command on files or directories. `{}` represents the directory or file. `find ~/Documents/ -iname readme.md -exec cat {} \;` execute `cat` command on each found files.
8. `-type f/d` find only directories or files if d or f is specified respectively. `find . -type d` finds only directories in current directory. 
9. `locate` can also be used to find files and directories. Searching for a file or directory can be easier with the locate command. `locate finger` will return both files and directories that have the word finger in the file or directory name.

# Display Content

1. `cat` display contents of file
2. `more` browse through a text file
3. `less` lesser features than `more`
4. `head` output beginning portion of the file
5. `tail1 output the ending portion of the file

`head` and `tail` by default show 10 lines. use `head/tail -20 file` to increase decrease or increase the number of lines.

To track the changes in file in real time use tail for that. `tail -f file`.

# Manage files and directories

1. `rm file` to remove file. 
2. `rm -r dir` to remove a directory and delete its contents recursively. 
3. `rm -f file` to remove a file forecefully
4. Always use the `ls` command to check which files and directories will be deleted before running the `rm` command
5. `cp` to copy a file. `cp README.md README.md.bak`
6. `cp file1 file2 dir` will copy both files into **dir** directory
7. `cp -r dir dir2` will copy all the files and directories within dir to dir2. If dir2 does not exists, it will be created
8. `cp -i file1 file2` will open copy command in interactive mode. It will show options to overwrite and all.
9. `cp -r dir dir2 dir3` will copy all the files and directories within dir and dir2 to dir3.
10. `diff` to show difference between two files
11. `mv` to move or rename a file
12. `mv dir dir2` will move the dir directory within dir2 directory
13. `mv dir dir4` will rename the directory to **dir4**
14. `mv -i` for interactive mv
