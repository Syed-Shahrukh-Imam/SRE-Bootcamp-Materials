# Linux Learning Materials.

TODO : Add the materials from the Google Docs.

## Man Pages

Man pages are used to provide a detailed description of the linux command. The syntax is:

```
man <linux-command>
```
Man pages can be searched using:
```
man -k SEARCH_TERM
```


## Environment Variables.

Environment variables store information. The storage location has a name and a value. Environment variables are typically uppercase. Access the contents by executing:

```
echo $VAR_NAME
```

PATH - is an env variable. Controls the command search path. Contains a list of directories. 

which - This command allows us to search for the path of the command we execute. For example, 

```
which cat
```

Should output:

```
/bin/cat
```

This means it shows the location of where this cat (basically an instruction file that tells the shell to do the cat).

**Fun Fact :** 'tac' command is the reverse of 'cat'. So tac is used to output the file in the reverse order.

 ## Working with Directories.

 Directories are containers for other files and directories. They provide a tree like structure. They can be accessed ny name or shortbut. 

 Directory Shortcuts:

```
 '.'  Refers to the current directory.
 '..' Refers to the parent directory.
 'cd' Refers to the changing directory.
```

Make directories using:

```
mkdir <directory name> 
```

Remove directories using 
```
rmdir <directory name> This removes the directory if is clean

rm -rf <directory name> This removes directory either empty or 
```

## File and Directory Permissions

On doing ls we can see a long listing format for the files and directories. 

Running 'ls -l'

```
drwxr-xr-x  4 syedimam  staff  128 12 Dec 11:36 linux
```
 Looking at the permissions section we can see what type of file is it. 
 - '-' means regular file.
 - 'd' means directory.
 - 'l' means symbolic link. 

 For our case, we can see that it is a directory. Other characters means 
 - 'r' for read. 
 - 'w' for write.
 - 'x' for execute.

### Permission Categories. 

Here are symbols for representing each category in permissions:

- 'u' means user
- 'g' means group
- 'o' means other
- 'a' means all

### Groups

- Every user is in at least part of one group
- Users can belong to many groups
- Groups are used to organize users
- The *groups* command is used to display a user's groups.
- You can also use *id -Gn*
- New files belong to your primary group 
- The *chgrp* command changes the group, Using *chgrp <new group name> <file name>
### Numeric Based Permissions

Numbers 0s and 1s can be used for setting persmissions. 
- 0 --> Value for off
- 1 --> Value for on

In permissions order has meaning. Permissions are always in read, write and execute order.\

The file creation mask determines the default permissions. If no masks used permissions would be 777 for directories or 666 for files./

*umask* sets the file creation mask to mode. That is, the command is used to set default permissions for files and directories the user creates. umask basically takes away the permission. 