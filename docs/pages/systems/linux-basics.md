# Linux Command-line Basics

## Basics of Basics

### Navigate around the file system

- `ls` list files
- `ls -l` list files with details
- `ls -la` list all files with details including hidden files
- `cd` change directory
- `cd ..` move out / up current directory by one layer
- `cd ~` change to home Directory
- `pwd` print current working directory

### Create/Modify files and folders

-   `touch <filename>` create a new file
-   `mkdir <dirname>` make a new directory (folder)
-   `rm <filename(s)>` remove file(s)
-   `rmdir <dirname(s)>` remove empty directory(s)
-   `rm -rf <dirname(s)>` remove directory(s) recursively
-   `cp` copy files(s)
-   `mv <filename> <new filename>` rename a file
-   `mv <filename(s)> <target path>` move file(s) to target path
-   `nano <filename>` launch nano text editor to edit file content

### Check system information

- `lsb_release -a` check ubuntu version
- `echo` print function
- `sudo reboot` reboot
- `sudo shutdown -h now` shutdown now
- `ifconfig`
- `iwconfig`
- `ping <domain name or ip address>`
- `top` show processes; use `q` to quit
- `uname -a` check machine info
- `lsusb` list usb
- `lspci` list pci


## User & Permissions

### User and groups 

Create a new user with home directory

```bash
sudo useradd -m username
```
    
List all users

```bash
less /etc/passwd
# or
users
```

List all groups

```bash
less /etc/group
# or
groups
```

List all groups that a specific user belongs to

```bash
groups USER
# or
id USER
```

List all users in a specific group

```bash
getent group GROUP
```

Add a user to a group

```bash
usermod -aG GROUP USER
```

- New group will be one of the user's secondary groups

Change a user's primary group

```bash
usermod -g GROUP USER
```

### User password

Change the current user's password

```bash
passwd
```

Change any user's password with sudo privileges

```bash
sudo passwd USER
```

### Switch user

- `sudo -i` becoming root user (require current user password)
- `su -` become root user (require root password)
- `su [username]` switch to user

> Ref: [Difference between sudo -i and su -](https://unix.stackexchange.com/a/98534)

### File Permissions

!!! info "UNIX System Permissions"
    Example:
    ```
    drwx------   5 markhuang  staff   160B Jan 13 11:13 .ssh
    lrwxr-xr-x   1 markhuang  staff    40B Jan  8 17:41 .tmux.conf -> ./dotfiles/tmux/tmux.conf
    -rw-------   1 markhuang  staff   797B Jan  9 16:39 .viminfo
    ```
    
    - First char: `d`/`l`/`-` stands for `dir`/`link`/`file`
    - following 3 chars: `r`/`-` + `w`/`-` + `x`/`-` represent `Read`,`Write`,`Execute` permission for **owner user**.
    - following 3 chars: `r`/`-` + `w`/`-` + `x`/`-` represent `Read`,`Write`,`Execute` permission for **owner group**.
    - following 3 chars: `r`/`-` + `w`/`-` + `x`/`-` represent `Read`,`Write`,`Execute` permission for **other user**.


Change owner for all files inside a folder

```bash
sudo chown USER[:GROUP] FILE(s)

# e.g. Change the owner and group of example.txt to user jack and group jack
sudo chown jack:jack example.txt
```

Change user permission of a file

```bash
chmod NEW_PERMISSIONS FILE

# e.g. Add execution permission for owner to example.sh
chmod u+x example.sh
# e.g. Add execution permission for owner and group to example.sh
chmod ug+x example.sh
# e.g. Remove execution permission for everyone to example.sh
chmod a-x example.sh
# e.g. Add read permission for everyone to example.sh
chmod a+r example.sh
# e.g. Change the permissions of example.sh to `rwxrwxrwx`
chmod 777 example.sh
```

!!! info ""
    - `u`: permission for owner user
    - `g`: permission for owner group
    - `o`: permission for other user
    - `a`: permission for all
    - `ugo`: permission for all
    - `+`: add permission
    - `-`: remove permission
    - `777`: permission equivalent to `rwxrwxrwx`
    - `644`: permission equivalent to `rw-r--r--`


## Disk

#### Check disk utilization 

```bash
df -h
```

- `-h` for "Human-readable" output

Example:

```bash
df -x tmpfs -x squashfs -x devtmpfs -x vfat -hT
```

- `-x` or `--exclude-type` for excluding certain file systems Type
- `-T` for printing file system type

#### Check file/folder size

```bash
du -sh {dir}
```
Example:

```bash
du -sh ./*
```

- `-s` for "specified" file/dir only
- `-h` for "Human-readable" output



## Working with Files and Folders

- `mkdir new_folder_name` make directory (create a new folder)
- `rmdir some_folder` remove a empty folder
- `rm -rf some_folder` remove a folder and everything inside

> More about removing directories: [How to Remove (Delete) Directory in Linux](https://linuxize.com/post/remove-directory-linux/)

- `touch example.txt` create a new file
- `nano example.txt` edit a file using the nano text editor
- `vim example.txt` edit a file using the vim text editor
- `cat example.txt` print out file content
- `rm example.txt` remove a file (delete a file)

move a file
```
mv [current path to file] [new path to file]
mv example.txt ~/Desktop/example.txt
```

rename a file
```
mv [current file name] [new file name]
mv example.txt example_renamed.txt
```

copy a file
```
cp [current path to file] [new path to file]
cp example.txt example_copy.txt
```

### Copy files between machines

!!! info ""
    `scp` also supports autocompletion for remote files and directories if you have existing SSH connection to the remote machine.

secure copy to remote machine

```
scp [local file] [remote user]@[remote address]:[remote path]

scp example.json root@178.128.22.33:/home/root/example
```

secure copy from remote machine

```
scp [remote user]@[remote address]:[remote file] [local path]

scp root@178.128.22.33:/home/root/example.json .
```

When copying a good number of files

- Consider using a simpler encryption algorithm
- Consider using `rsync` instead of `scp`
- Consider using `parallel-scp` and `parallel-rsync`
