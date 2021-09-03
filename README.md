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
Read means user can see file's contents. `cat index.html` is allowed fot the current user.
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
