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