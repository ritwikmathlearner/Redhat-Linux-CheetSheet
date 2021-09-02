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
