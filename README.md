# SSH
Create

All Collections
Files management
SSH connection and SSH keys
SSH cheat-sheet
SSH cheat-sheet
Check all the most useful SSH commands in one place
Updated over a week ago
Table of contents
After you connect to your account via SSH, you might need these commands for:

Managing location

Files and folders management

Managing archives

Managing databases

Checking inodes and disk usage per directory

Managing WordPress websites

Managing location
pwd (print working directory) - show the full path to the directory in which you are currently.

pwd
 

cd (change directory) - move from one folder to another. 

cd directory_name
cd directory_name - go to this subfolder of the current folder 

cd .. - go one level up

ls (list) - show the list of all files and folders in the current directory.

ls
ls -a include hidden files (which begin with a dot)

Files and folders management
cp (copy).  You can copy both files and folders. 

cp copy_what copy_where
If you would like to copy to a higher directory, insert the full path, starting from home

How to copy files or folders using SSH?

mv (move). Same as cp, you can move both files and folders.

mv move_what move_where
 

mkdir (make directory) - create a new empty directory.

touch - create a new empty file.

mkdir folder_name
touch file_name
 

rmdir (remove a directory) - delete the folder.

rm (remove) - delete a file. You can mention several files at a time.

rmdir folder_name
rm file_name
rm -r deletes folders, their subfolders, and their content

How to delete files or folders using SSH?

 

grep - find a specific text inside files.

grep -inrl 'text'
 

find - find files with a specific name.

find . -type f -name 'name*.php'
Managing archives
Create an archive
Create an archive of specific files: 

ZIP: zip archive-name.zip filename1.php filename2.php filename3.php
TAR: tar -cvf archive.tar filename1.php filename2.php filename3.php
TAR.GZ: tar -zcf NewArchive.tar.gz filename1.php filename2.php filename3.php

 

Where instead of archive type the name of the future archive, and after that - exact files which should be included.

Create an archive of the whole folder:

ZIP: zip -r archive.zip DirectoryName 
TAR: tar -cvf archive.tar DirectoryName 
TAR.GZ: tar -zcf archive.tar.gz DirectoryName

 

Unpack an archive
ZIP: unzip archive.zip 
TAR: tar -xvf archive.tar 
TAR.GZ: tar -zxvf archive.tar.gz

Managing databases
Import database file.sql to the database_username database.

mysql -u database_username -p database_name < file.sql
For this command, you should be in the folder where the file.sql is located

How do I import a database over SSH?

Export of database_username database to the file.sql file. 

mysql -u database_username -p database_name > file.sql
For this command, you don't need to create a file beforehand

How do I export a database over SSH?

For both commands, in the next step, you should insert the database password

Checking inodes and disk usage per directory
Show the inodes number for every subdirectory of the current folder. 

find . -printf "%h\n" | cut -d/ -f-2 | sort | uniq -c | sort -rn
 

Show the disk usage per each subdirectory and file of the current folder.

du -shc * | sort -rh
How to check inodes and disk usage per folder using SSH?

It can also be done faster via File Manager (beta)

Managing WordPress websites
Purge WordPress cache
wp cache flush
wp litespeed-purge all
 

Replace WordPress core files
rm -rf wp-includes
rm -rf wp-admin
wp core download --skip-content --force
Or:

backup=WP_`date +%s` && mkdir $backup && mv wp-admin $backup && mv wp-includes $backup && mv *.php $backup && wget
