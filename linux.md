[mobilege](/README.md#linux--utilities)
/ [Linux](/linux.md) 
    <sub>&nbsp;&nbsp;Documentation</sub>
    <sub>&nbsp;&nbsp;[tldr](https://tldr.inbrowser.app/)</sub>

# Linux

[Notes](#notes) &nbsp; · &nbsp; [Utilities](#utilities) &nbsp; · &nbsp; [Resources](#resources)

```zsh
$ which python3      # Shows first matching executable in PATH
$ which -a python3   # Shows all matching executables in PATH

$ where python3      # Same as 'which -a' but also includes aliases and built-ins

$ file /usr/bin/python3  # Describes the file type
```

```zsh
$ which python3
$ file $(!!)
```

## Directory Operations

`pwd` Print name of current working directory

`cd` Change directory

```zsh
$ cd .    # Stay in the current directory
$ cd ..   # Change to the parent directory
$ cd ~    # Change to the user's home directory
$ cd /    # Navigate to the root directory
$ cd -    # Switch to the previous directory
```

`ls` List directory contents

```zsh
$ ls -a     # Show all files and directories, including hidden ones
$ ls -h     # Show file sizes in human-readable format
$ ls -l     # Show contents in long format
```

see: The Linux Command Line, Chap 2 

## File Operations

##### Viewing Files
```zsh
$ cat filename.txt  # Display the entire contents of a file
$ head -n 5 filename.txt  # Display the first 5 lines of a file
$ tail -n 20 filename.txt  # Display the last 20 lines of a file
$ vim filename.txt  # Open a file in the Vim text editor (creates a new file if it doesn't exist)
$ nano filename.txt  # Open a file in the Nano text editor (creates a new file if it doesn't exist)
$ code filename.txt  # Open a file in Visual Studio Code (creates a new file if it doesn't exist)
```

## Shell Features

_Sequence of topics is based on: Shell Features > P26_[^1] 
- Alternative shells:
  - https://fishshell.com
    - `> fish`
    - `> fish_config` (_https://fishshell.com/docs/current/cmds/fish_config.html_) 
  - https://www.nushell.sh
    - `> nu`    


#### Wildcards
```shell
$ ls a*     # Starts with a
$ ls [ab]*  # Starts with a or b
$ ls ????   # 4 letter files or directories
```

#### Brace expansion
```shell
$ mkdir dir{A..E}             # dirA	dirB	dirC	dirD	dirE
$ touch file{1..5}.txt        # file1.txt file2.txt file3.txt file4.txt file5.txt
$ touch file{abc,def,xyz}.txt # fileabc.txt	filedef.txt	filexyz.txt
```

#### Shell variables
```shell
$ export MYVAR=5
$ echo $MYVAR
$ printenv  # Prints all environment variables
```

#### Search path
```shell
$ echo $PATH  # display current PATH environment variable
$ export PATH=$PATH:/new/path   # add new directory in path 
```
*PATH is essentially a `:` separated list of directories. When you execute a command, the shell searches through each of these directories, one by one, until it finds a directory where the executable exists. [Source](https://www.cs.purdue.edu/homes/bb/cs348/www-S08/unix_path.html)*

###### Path to an executable
`which, type, command, whence, where, whereis, whatis, hash` etc

```zsh
$ which python3
# /usr/local/bin/python3

$ which -a python3
# /usr/local/bin/python3
# /usr/bin/python3
```

#### Alias
```shell
$ alias              # Lists all aliases
$ alias ll='ls -lG'  # Creates a temporary alias
$ unalias ll         # Remove an alias
```
_To make an alias permanent, add it to: `~/.bashrc` or `~/.zshrc`. Run `source ~/.bashrc` or `source ~/.zshrc` after. [Source](https://phoenixnap.com/kb/linux-alias-command)_

#### Redirection
```shell
$ echo "hello" > file1.txt   # Create/overwrite file
$ echo "hello2" >> file1.txt # Append to file
$ mkdir existingdir 2> errors.txt # Errors
```

```zsh
$ ls -l ~ | head
```

_Redirecting Standard Input `<` isn't very common imo [Source](https://unix.stackexchange.com/a/156138)_

[⇧ Back to Top ⇧](#unix)


## Build Systems
_Topics based on: How Linux Works[^2] > 15 Development Tools_

###### Compiling a C program
```zsh
# Start with main.c, util.c, util.h
$ cc main.c util.c  #creates a.out
$ ./a.out           #Hello, World.
```

```zsh
# Start with main.c, util.c, util.h
$ cc -c main.c      #creates main.o
$ cc -c util.c      #creates util.o
$ cc main.o util.o  #creates a.out
$ ./app             #Hello, World
```

- _`-o` names output file_
- _`-c` creates object file_ [Compiler Options](https://docs.oracle.com/cd/E19957-01/806-3567/cc_options.html)
- _Static library ends with `.a`_
- _Shared library ends with `.so`_


_See: [Modern C++ Course, Lecture 1: Build Systems (2021)](https://youtu.be/zOmUHM0sFOc)_

###### Make Utility
```zsh
# Start with main.c, util.c, util.h
$ cat Makefile 
# CC=gcc
# main: main.o util.o
$ make    #creates main.o, util.o, main
$ ./main  #Hello, World.
```
_See: https://www.linuxtopia.org/online_books/an_introduction_to_gcc/gccintro_16.html_




## Package Management
- The Linux Command Line > 14. Package Management
- https://help.ubuntu.com/community/InstallingSoftware
- Ruby / [Package Management](https://github.com/mobiledge/web-development/blob/master/ruby.md#package-management)

#### Package Manager
- an application which handles the downloading and installation of packages (can itself be treated as a package)
- can be categorized into two main types: operating system (OS) based package managers and language-specific package managers
- examples:
  - Homebrew (macOS)
  - APT, apt-get (Linux Debian-based)
  - YUM, DNF (Linux Red Hat-based)
  - RubyGems (Ruby)
  - pip (Python)
  - npm, Yarn (JavaScript)

#### Package
- collection of files bundled into a single file
- everything that a particular program needs to run
- can be Source Package or Binary Package
- can depend of other packages (Package Dependencies)

#### Package Dependencies
- other software packages that a particular package relies on

#### Package Repository
- online storage location

#### RubyGems vs Bundler
- RubyGems is responsible for managing the installation and distribution of gems globally
- Bundler focuses on managing gem dependencies within a specific Ruby project


#### Homebrew
- installed in `/usr/local/Cellar/<program>/<version>/bin/<executable>`
  - Eg. `/usr/local/Cellar/tree/2.0.1/bin/tree`
- symlink in `usr/local/bin`
- symlink in `usr/local/opt`

#### NPM
- `/usr/local/lib/node_modules` modules that came with Node
- `/usr/local/lib/node_modules/npm/node_modules` modules installed by the user using `npm`
  - Eg. `ls -dl /usr/local/lib/node_modules/npm/node_modules/t*`
- `~/.nvm/versions/node/{version}/lib/node_modules/` if using node version manager (nvm)
  - Eg. `ls -dl /Users/rabinjoshi/.nvm/versions/node/v17.2.0/lib/node_modules/npm/node_modules/t*` 



## Public-key cryptography

- [2.4.1 RSA Public Key Encryption: Video](https://youtu.be/ZUZ8VbX1YNQ)
- [Introduction to Cryptographic Keys and Certificates](https://youtu.be/q9vu6_2r0o4)



## Fundamentals of Red Hat Enterprise Linux

###### Week 1: Getting Started with Red Hat Enterprise Linux

#### Software Licensing

Permissive: MIT, BSD, Apache

Copyleft: GPL

see: https://exygy.com/blog/which-license-should-i-use-mit-vs-apache-vs-gpl/

###### Week 2: Accessing the Command Line

#### SSH

*Shell is an **interpreter** that executes commands typed as strings.*

*SSH is a program used to login to a **remote** system.*

*Default terminal prompt is `<user>@<host> <folder>`.*

```shell
# Login to a remote system using a password.
[user@host ~]$ ssh remoteuser@remotehost

# Login to a remote system using a public key.
[user@host ~]$ ssh -i mylab.pem remoteuser@remotehost

# Logout
[remoteuser@remotehost ~]$ exit # or Ctrl+D
```

```shell
$ whoami # Displays user id
```

#### Viewing Files
```shell
$ file /etc/passwd  # Determine file type.
$ cat /etc/passwd   # Print and concatenate files.
$ head /etc/passwd  # Output the first part of files.
$ tail /etc/passwd  # Display the last part of a file.
```

```shell
$ history   # Command-line history.
```

#### Useful Command-line Editing Shortcuts

| Shortcut | Description |
| -------- | ----------- |
| Ctrl+A | Jump to the beginning of the command line. |
| Ctrl+E | Jump to the end of the command line. |
| Ctrl+U | Clear from the cursor to the beginning of the command line. |
| Ctrl+K | Clear from the cursor to the end of the command line. |
| Ctrl+LeftArrow | Jump to the beginning of the previous word on the command line. |
| Ctrl+RightArrow | Jump to the end of the next word on the command line. |

###### Week 3: Managing Files From the Command Line
 
```shell
$ pwd     # Print name of current/working directory.

$ ls      # List directory contents
$ ls -lah  # long listing format, include hidden files, human-readable size
$ ls -R   # recursive, include subdirectories

$ cd      # Go to home
$ cd ..   # Go to parent
$ cd -    # Go to the previous

$ mkdir                 # Create directory,  -p: nested
$ touch file1.txt       # Create empty file
$ echo -n > file2.txt   # Create empty file

$ cp -r dirA dirA       # Copy directory & its contents
$ cp -r dirA/* dirB     # Copy contents only
$ cp file1 dir          # Copy file

$ mv dir1 dir2          # Move directory & its contents
$ mv dirA/* dirB        # Move contents only
$ mv file1 dir          # Move file

$ rm -r dir1            # Remove directory & its contents
$ rm -r dir1/*          # Remove contents only
$ rm file1              # Remove file
```

#### Searching for Files & Executables

> The Linux Command Line · Chapter 17: Searching for Files

[⇧ Back to Top ⇧](#unix)

## Expansion

```shell
$ ls a*     # Starts with a
$ ls [ab]*  # Starts with a or b
$ ls ????   # 4 letter files or directories

$ mkdir dir{A..E}       # dirA	dirB	dirC	dirD	dirE
$ touch file{1..5}.txt  # file1.txt file2.txt file3.txt file4.txt file5.txt
```

###### Week 5: Managing Local Linux Users and Groups

```shell
$ id      # Display user's ID (UID), group ID (GID) and groups to which they belong
```

*"Every file is owned by one user and one group, no more, no less." What are the implications of this?* [Source](https://.stackexchange.com/a/605541)

```shell
$ ls -l file1     # view who owns the file (owner & group) and what they can do with it (read/write/execute)
$ ls -ld dir1     # view who owns the directory (owner & group) and what they can do with it (read/write/execute)
```

```shell
# switch to root user, login shell
# root's password required
# root user's account may not have a valid password at all for security reasons, use sudo in that case
$ su -           


# switch to user1, login shell
# user1's password required
$ su - <user1>   
```


```shell
# sudo is an alternative to su (because the root user's account may not have a valid password at all for security reasons)
# user's own password required (not the root's like in su)
# whether a user has sudo priviledges is determined by the /etc/sudoers file
$ sudo <some command>


# switch to root user WITHOUT needing the root's password
$ sudo su -
```

###### Managing Local User Accounts

*Unlike Linux, MacOS does not have the same commands like `useradd`, `usermod`, and `userdel` for creating, modifying, and deleting user accounts. Same for groups.* 


###### Week 6: Controlling Access to Files with Linux File System Permissions

```shell
$ chmod go-rw file1      # (Symbolic way) Remove read and write permission for group and other
$ chmod a+x file2        # (Symbolic way) Add execute permission for everyone

$ chmod 644 samplefile   # (Numeric way) Set read and write permissions foruser, read permission for group and other
$ chmod 750 sampledir    # (Numeric way) Set read, write, execute for user, read and execute for group, and no permission for other
```

#### Processes

```shell
$ ps aux     # List all running processes
$ top        # Display dynamic real-time information about running processes
```

```shell
$ jobs       # Show status of all jobs

$ bg         # Resume the most recently suspended job and run it in the background
$ bg %1      # Resume job '1' and run it in the background

$ fg         # Bring most recently suspended background job to foreground
$ fg $1      # Bring job '1' to the foreground
```

*Shell warns user of suspended jobs when closed.*

[⇧ Back to Top ⇧](#unix)





## Notes 

*MacOS is based on BSD*

```shell
$ echo "Hello World" # Print given arguments.

$ man <command> # q to exit
$ tldr <command>
```

#### Filesystem
![filesystem-hierarchy](/images/filesystem-hierarchy.png)


#### Important Files
- `/etc/passwd`  information about users 
- `/etc/shadow`  information about passwords
- `/etc/group`   information about groups
- `/etc/sudoers` information about which users can sudo

#### Dates & Times[^1]

```zsh
$ date    # Displays the system date
$ date -u # Displays the date in UTC (Coordinated Universal) time

$ cal     # Displays a calendar for the current month
$ cal -3  # Displays previous, current and next month
```

## Utilities
- [tldr](https://github.com/tldr-pages/tldr) `tldr find`
- [tree](https://formulae.brew.sh/formula/tree) `tree -L 2`

## Resources
- [Modern C++](https://youtube.com/playlist?list=PLgnQpQtFTOGRv7VS6fYerEbT4ckBovKur&feature=shared) `YouTube Playlist`
- [Unix Exercises](https://github.com/mobilege/unix/blob/master/unix-exercises.md)
- [The Missing Semester of Your CS Education](https://missing.csail.mit.edu)
- [Fish Tutorial](https://fishshell.com/docs/current/tutorial.html#tutorial) 





[^1]: Linux Pocket Guide · 3rd Edition
[^2]: How Linux Works · Brian Ward · 3rd Edition
