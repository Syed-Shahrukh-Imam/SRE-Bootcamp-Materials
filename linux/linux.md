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

## Displaying contents of Files

These commands prove to be very useful.

```
cat file - Displays the contents of a file
more file - Browse through a text file.
less file - More features than more.
head file - Output the beginning or the top portion of the file.
tail file - Output the ending portion of the file. 
```

The following command will allow you to follow a file that is being updated. This can be important when displaying or working with log files. 

```
tail -f <file name>
```

## Finding files and directories. 

The command to do this is *find*. This recursively finds files in path that match expression. If no arguments are supplied it finds all the files in the current directory struture. The syntax is shown below: 

```
find [path] [expression]
```

The find command has some very useful features. 

```
-name pattern : find files and directories that match the pattern. 
-iname pattern: it is like -name, but ignores case. 
-ls : performs an ls of each found items.


-mtime days: Find files that are days old.
-size num: Finds file that are of size num
-newer file: Finds file that are newer than file.
-exec command {} \; : run command against all files that are found. 
```

Another helpful command is the locate command. The syntax for the command is as follows:

 ```
 locate pattern
 ```
 This command is used to:
 - Lists files that match pattern
 - Faster than the find command
 - Queries an index
 - Results are not real time.
 - May not be enabled on all systems
 - It is *faster* than the find command. This works using an index. Usually there is a lag between the index between updating and using the locate command.
 
 ## Wildcards
 
 A Wildcard is a character or string used for pattern matching. Globbing expands the wildcard pattern into a list of files and/or directories (paths). Wildcards can be used with most commands.
 - ls
 - rm
 - cp
 
 There are two types of wildcards: 
 - * : matches zero or more characters.
 - ? : matches exactly one characters. 
 
 ### More Wildcards
 [ ] - This is a character class
 - This matches any of the characters included between the brackets. Matches exactly one character. For eg,
 ```
 [aeiou] - This matches all the vowels. 
 ```
 - Moreover, we use [!] which matches any of the characters NOT included between the brackets. Matches exactly one character. 
 
## I/O Redirection
There are three different types of I/O.
 
- Standard Input --> stdin --> 0
- Standard Output --> stdout --> 1
- Standard Error --> stderr --> 2

The number represents file descriptors. These mean open files. It is easier for the machine to refernce these as numbers. 
 
### Redirection
```
 > - Redirects standard output to a file. 
 
 >> - Redirects standard output to a file. Appends to any existing contents.
 
 < - Redirects input from a file to a command. 
```
    
## Aliases
Aliases can be thought of as a text expander. It allows for using shortcuts, useful when repeated use of long commands and useful for commands that we use often.
    
The syntax is:

```
alias [name[=value]]
```

## Comparing Files.
    
There are three ways to do this. 
- diff file1 file2 : Compare two files. 
- sdiff file1 file2 : Side by side comparision
- vimdiff file1 file2 : Highlight differences in vim
    
## Searching in Files and Using Pipes
To look for text within a file we use the *grep* command. The typical syntax of using grep is shown below: 
```
grep pattern file
```
### *grep* Options
- -i : Perform a search, ignoring the case. 
- -c : Count the numnber of occurences in a file.
- -n : Precede output with the line number. 
- -v : Invert Match. Print the lines that do not match. 


## Processes and Job Contronl

To display the current process in the current session we run the *ps* option. The *ps* command has a few useful flags. 

```
-e : Everything, all processes.
-f : Full format listing.
-u username : Display the username's processes. 
-p username : Display information for the PID

```

Other ways to view processes include: 

- pstree
- top
- htop

## Background and Foreground Processes

``` 
command & : This tells shell to start the *command* in the background.
Crtl C : Kills the foreground process.
Crtl Z : Suspends the foregorund process. 
```

## Scheduling Repeated Jobs with Cron

- cron - is a time based job scheduling service.
- crontab - a program to create, read, update and delete your job schedules. 
- Use cron to schedule and automate tasks.

### Crontab format

```
* * * * * command

From the right ... 

First Asterik : Day of the week (0-6)
Second Asterik : Month of the year (1-12)
Third Asterik : Day of the Month (1-31)
Fourth Asterik : Hour (0-23)
Fifth Asterik : Minute (0-59)

```

