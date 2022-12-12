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

 '.'  Refers to the current directory.
 '..' Refers to the parent directory.
 'cd' Refers to the changing directory.
  


