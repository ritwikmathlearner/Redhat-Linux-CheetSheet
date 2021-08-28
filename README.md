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