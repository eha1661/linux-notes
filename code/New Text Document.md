# Summary 
1. __[Intro Shell](#introshell)__
2. __[Navigation](#navigation)__
3. __[Exploring The System](#exploringsystem)__
4. __[Manipulating Files and Directories](#manipulatingfilesdirectories)__
5. __[Working With Commands](#workingwithcommands)__
6. __[Redirection](#redirection)__
7. __[Expansion and Quoting](#expansionquoting)__
8. __[Keyboard Tricks](#keyboardtricks)__  (TO CHECk)  
9. __[Permissions](#permissions)__ (TO CHECK)
10. __[Processes](#processes)__ (NOW)
11. __[ProcessEnvironmentes](#environment)__ (TOMORROW)
12. __[VI and VIM ](#vim)__ (TOMORROW A SEPERATE MD)

## Intro Shell <a name="introshell"></a>  
__What is a Shell__
The shell is a program that takes keyboard commands and passes them to the operating system to carry out. All linux distributions supply a shell program called __bash__ (bourne-against-shell) [[1]](#ref1)

__shell prompt__
``` shell
username@machinename:~$
```
(#) if the terminal session has superuser priveledges

__command history__
Linux distributions remember the last 1,000 commands by default.
If we press the up arrow, we will see that the previous command entered

__some simple cammands__
* date : to displays the current time and date
* df : to see the current amount of free space on our disk drives, enter df
* free : to display the amount of free memory
* exit : to end the terminal session


__composition of a command line__

```command -options arguments```
* short option consists of one letter for example : -l 
* long options consist of a word preceded by two dashes : --help

----------------------------------------------------------------------------
## Navigation <a name="navigation"></a>
Unix-like systems such as Linux always have a single file system tree, regardless of how many drives or storage devices are attached to the computer. 

The directory we are standing in is called the __current working directory__.

To display the current working directory
``` shell
username@machinename:~$ pwd
```

To list the files and directories in the current working directory
``` shell
username@machinename:~$ pwd
```
> Absolute Pathnames
/usr/bin
    
> Relative Pathnames
 . (dot) and .. (dot dot) are used to


shortcut | result|
:-------:| ------|
|cd      |Changes the working directory to your home directory|

----------------------------------------------------------------------------
## Exploring The System <a name="exploringsystem"></a>
__Listing files and subdirectories__

To list of files and subdirectories contained in the current working directory ```ls``` 
<img src="/code/images/ls-options.PNG" alt="ls" style="width:500px;"/>


The long format listing returns many info. for example 
```-rw-r--r-- 1 root root   32059 2017-04-03 11:05 oo-cd-cover.odf ``` \
<img src="/code/images/ls-l-info.PNG" alt="ls" style="width:500px;"/>


To show a brief description of a file ```file filename```

There are many kinds of files. In fact, one of the common ideas in Unix-like operating
systems such as Linux is that “everything is a file”

__less command__
less command is a program to view text files ```less filename```

__Directories in Linux File System__

<img src="/code/images/linux-repo-1.PNG" alt="ls" style="width:500px;"/>
<img src="/code/images/linux-repo-2.PNG" alt="ls" style="width:500px;"/>
<img src="/code/images/linux-repo-3.PNG" alt="ls" style="width:500px;"/>
<img src="/code/images/linux-repo-4.PNG" alt="ls" style="width:500px;"/>

__Symbolic Links (soft link or symlink)__
It is possible to have a file referenced by multiple names (more details below).
```
lrwxrwxrwx 1 root root   11 2018-08-11 07:34 libc.so.6 -> libc-2.6.so
```
__Hard links__ 
Hard links also allow files to have multiple names, but they do it in a different way (more details below)

----------------------------------------------------------------------------

## Manipulating Files and Directories <a name="manipulatingfilesdirectories"></a>

__Wildcards__ 
<img src="/code/images/wildcards-1.PNG" alt="ls" style="width:500px;"/>

<img src="/code/images/wildcards-2.PNG" alt="ls" style="width:350px;"/>

<img src="/code/images/wildcards-3.PNG" alt="ls" style="width:500px;"/>

__commands__ 
- To create directories ```mkdir directory...```
- ```cp``` command
    - copies the single file or directory item1 to the file or directory item2 
    ```cp item1 item2```
    - copies multiple items (either files or directories) into a directory
    ```cp item... directory```
    - cp options
    <img src="/code/images/cp-options.PNG" alt="ls" style="width:500px;"/>
    - some examples
    <img src="/code/images/cp-examples.PNG" alt="ls" style="width:500px;"/>

- ```mv``` command
    - The mv command performs both file moving and file renaming, depending
on how it is used
    - mv options
    <img src="/code/images/mv-options.PNG" alt="ls" style="width:500px;"/>
    - mv exampes
    <img src="/code/images/mv-examples.PNG" alt="ls" style="width:500px;"/>

- ```rm``` command
    - rm command is used to remove (delete) files and directories
    - __be carefull__ Linux do not have an undelete command
    - rm options
    <img src="/code/images/rm-options.PNG" alt="ls" style="width:500px;"/>
    - rm examples
    <img src="/code/images/rm-examples.PNG" alt="ls" style="width:500px;"/>

- ```ln```
    - hard links
        - to create a hard link ```ln file link```
        - By default, every file has a single hard link
that gives the file its name. When we create a hard link, we create an additional directory
entry for a file
        - limitation : A hard link cannot reference a file outside its own file system
        - limitation : A hard link may not reference a directory.

    - symbolic links
        - to cteate a soft link ```ln -s item link```
        - They work by creating a special type of file that contains a text pointer to the referenced file or directory (like Windows shortcut)

-----------------------------------
## Working With Commands <a name="workingwithcommands"></a>

__What is a command?__ \
a command can be:
- An executable program : it can be compiled binaries or a program written in a scripting language 
- A command built into the shell itself (shell builtins). For example  ```type```
- A shell function : miniature shell scripts incorporated into the environment
- An alias

__commands__ 
- ```type``` command
    - it is a shell builtin that displays the kind of command the shell will execute
- ```which``` command
    - it displays the executabl's location
- ```help```
    - it shows the help for shell builtins
- the option __help__ 
    - it display usage information for many executable programs. For example ```python3 --help``` 
- ```man```
    - man is special program used to view documentation ( manual or man page) of a particular program.
    For exmaple ```man ls```
- ```whatis```
    - The whatis program displays the name and a one-line description of a man page matching a specified keyword
- ```info```
    - The GNU Project provides an alternative to man pages for their programs, called info. 
    e.g ```info ls```
- ```alias```
    - it create an alis. For example ```alias foo='cd /usr; ls; cd -'```
    - to remove an alias ```unalias command1```
    - to see all the aliases defined in the environment ```alias```
    - aliases vanish when your shell session ends

__tricks__
- It’s possible to put more than one command on a line ```command1; command2; command3...```

-----------------------------------

## Redirection (I/O Redirection) <a name="redirection"></a>

Programs such as ```ls``` actually send their results to a special file called __standard output__ (often expressed as __stdout__) and their status messages to another file called __standard error__ (__stderr__). By default, both standard output and standard error are linked to the screen and not saved into a disk file.

In addition, many programs take input from a facility called __standard input__ (__stdin__),  which is, by default, attached to the keyboard.

I/O redirection allows us to change where output goes and where input comes from.

__Redirecting Standard Output__ \
We use the __>__ redirection operator followed by the name of the file. We append redirected output to a file instead of overwriting the file from the beginning, using the __>>__ redirection operator

Example
- saving ls output to a file
    ```shell
    ls -l /usr/bin > ls-output.txt
    ```
    ```shell
    ls -l /usr/bin >> ls-output.txt
    ```
- the redirection operator with no command preceding it will truncate an existing file or create a new, empty file.
    ```shell
    > ls-empty.txt
    ```
__Redirecting Standard Error__

Redirecting standard error lacks the ease of a dedicated redirection operator.

While we have referred to the first three of these file streams as standard input, output, and error, the shell references them internally as file descriptors 0, 1, and 2, respectively.

The shell provides a notation for redirecting files using the  file descriptor number

examples:
-  Redirecting ls standard error
    ```shell
    ls -l /bin/usr 2> ls-error.txt
    ```
- Redirecting Standard Output and Standard Error to One File
    ```shell
    ls -l /bin/usr > ls-output.txt 2>&1
    ```
    ```shell
    ls -l /bin/usr &> ls-output.txt
    ``` 
    ```shell
    ls -l /bin/usr &>> ls-output.txt
    ``` 
- In case we don't need outputs from a command
    ```shell
    ls -l /bin/usr 2> /dev/null
    ``` 

__Redirecting Standard Input__

commands:
- ```cat```
    - it reads one or more files and copies them to standard output
    - it is often used to display short text files
    - example : join some files ```cat movie.mpeg.0* > movie.mpeg```
    - cat is not given any arguments, it reads from standard input (standard input is keyboard by default)
     Type ctrl-D to tell cat that it has reached the end of file (EOF)
    - Using the __<__ redirection operator, we change the source of standard input from the keyboard to the file myfile.txt
    ```shell
    cat < myfile.txt
    ``` 

__Pipelines__ \
Using the pipeoperator __|__, the standard output of one command can be piped into the standard input of another.
```shell
command1 | command2
``` 

The pipelines can be used as follows:
- Filters:
    - Filters take input, change it somehow, and then output it. 
    - example:
        ``` shell
        ls /bin /usr/bin | sort | less
        ```
- Report or Omit Repeated Lines
    - ```uniq``` accepts a sorted list of data from either standard input or a single filename argument and, by default, removes any duplicates from the list
    - example : ```ls /bin /usr/bin | sort | uniq | less``` 
- Print Line, Word, and Byte Counts
    - ```wc```is used to display the number of lines, words, and bytes contained in files
    - example : ```ls /bin /usr/bin | sort | uniq | wc -l```
- Print Lines Matching a Pattern ```grep```
    - grep is a powerful program used to find text patterns within files. ```grep pattern filename```
    - example : ```ls /bin /usr/bin | sort | uniq | grep zip```
- Print First/Last Part of Files ```head/tail```
    - You might want only the first few lines or the last few lines
    - example : ```head -n 5 ls-output.txt```
- Read from Stdin and Output to Stdout and Files (tee)
    - The tee program reads standard input and copies it to both standard output (allowing the data to continue down the pipeline) and to one or more files
    - exampe : ```ls /usr/bin | tee ls.txt | grep zip```

## Expansion and Quoting <a name="expansionquoting"></a>  
__Expansion__\
Bash performs several substitutions upon the text before it carries out command.\
For example, ```echo *```; the bash command expands ```*```into the files at the current directory.\
There are different expansions available:
* Pathname expansion
``` shell
username@machinename:~$ echo /user/*/share
```
* Tilde expansion: it expands into the name of the home directory of the named user
it
* arithmetic expansion: it follows this form ```$((expression))```
``` shell
username@machinename:~$ echo $((2 + 2))
```
``` shell
4
``` 
* brace expansion 
``` shell
username@machinename:~$ echo Front-{A,B,C}-Back
``` 
``` shell
Front-A-Back Front-B-Back Front-C-Back
```
``` shell
username@machinename:~$ echo {01..15}
``` 
``` shell
01 02 03 04 05 06 07 08 09 10 11 12 13 14 15
```

* parameter expansion
``` shell
username@machinename:~$ echo $USER
``` 
Note: if you misspell the name of a variable, the expansion will still take place but will result in an empty string.

* command substitution
``` shell
username@machinename:~$ ls -l $(which cp)
``` 

__Quoting__
* double quotes 
``` shell
username@machinename:~$ ls -l "two words.txt"
``` 
``` shell
username@machinename:~$ echo $(cal)
``` 
``` shell
username@machinename:~$ echo "$(cal)"
``` 

* single quotes : if we need to suppress all expansions, we use single quotes 

* escaping characters : use ```\``` to eliminate the special meaning of these special charcters ```$, !, &, spaces, \ and others```
``` shell
username@machinename:~$ echo "$USER won \$200.00"
``` 

## Keyboard Tricks <a name="keyboardtricks"></a>
__command line editing__
* Cursor movement
<img src="/code/images/cursorr-movement_cmd.png" alt="ls" style="width:500px;"/> 


__Using history__
* searching hisotry
> we can view the contents of the command history list by ```history | less```

<img src="/code/images/history-cmd.png" alt="ls" style="width:500px;"/> 

* History expansion
<img src="/code/images/history-expansion.png" alt="ls" style="width:500px;"/> 

## Permissions <a name="permissions"></a>
__Owners, Group Members, and Everybody Else__

When user accounts are created, users are assigned a number called a user ID (uid)
which is then mapped to a username. The user is assigned a group ID (gid) and may belong to additional groups.

To show available ids in your system ```id```

Files containing informations about users, groups are:
* ```/etc/passwd``` : user accounts
* ```/etc/group``` : groups 
* ```/etc/shadow``` : user's password

__Reading, Writing, and Executing__
Access rights to files and directories are defined in terms of read access, write access, and execution access.
```-rw-rw-r-- 1  me   0  2018-03-06  14:52  foo.txt```
the listing consists of: file type, ownership,  permissions ...
<img src="/code/images/file-types.png" alt="ls" style="width:500px;"/> 
<img src="/code/images/owner-group-world.png" alt="ls" style="width:200px;"/> 
<img src="/code/images/permission-attributes.png" alt="ls" style="width:500px;"/> 

__Changing File Mode__
To change the mode (permissions) of a file or directory, use the chmod command. Be aware that only the file’s owner or the superuser can change the mode of a file or directory. chmod supports two distinct ways of specifying mode changes: Octal number representation and symbolic representation

1. Octal number representation \
The table below shows file mode in binary and octal
<img src="/code/images/file-mode-table.png" alt="ls" style="width:400px;"/>

example:
``` shell
username@machinename:~$ chmod 600 foo.txt
username@machinename:~$ ls -l foo.txt
``` 
``` shell
-rw------- 1  me  me  0  2018-03-06 14:52 foo.txt
``` 

2. symblic representation
chmod Symbolic Notation is defined : 
<img src="/code/images/file-mode-table.png" alt="ls" style="width:400px;"/>

If no character is specified, “all” will be assumed.

Some examples
<img src="/code/images/symbolic-mode-examples.png" alt="ls" style="width:400px;"/>

__Changing Identities__
There are three ways to take on an alternate identity:
* Log out and log back in as the alternate user.
* Use the su command.
* Use the sudo command.

* ```su``` command
The su command is used to start a shell as another user.

``` shell
su [-[l]] [user]
```

* ```sudo``` : Execute a Command As Another User
The administrator can configure sudo to allow an ordinary user to execute commands as a different user (usually the supe-ruser) in a controlled way.Also, sudo does not require access to the superuser’s password.


* ```chown``` : Change File Owner and Group
The chown command is used to change the owner and group owner of a file
or directory. Superuser privileges are required to use this command. 
```
chown [owner][:[group]] file...
```
Some examples
<img src="/code/images/chown-1.png" alt="ls" style="width:400px;"/>
<img src="/code/images/chown-1.png" alt="ls" style="width:400px;"/>

----------------------------------------------------------------------
# Resources 
1. The Linux Command Line A Complete Introduction by William E. Shotts 
<a name="ref1"></a>
2. [markdown shd101](https://shd101wyy.github.io/markdown-preview-enhanced/#/markdown-basics)
3. [Mastering Markdown](https://shd101wyy.github.io/markdown-preview-enhanced/#/markdown-basics)
