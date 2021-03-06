# Linux Commands

## Basic

-   `ls -la`
-   `cd`
-   `rm`
-   `cp`
-   `mv`
-   `nano`
-   `touch`
-   `mkdir`
-   `rmdir`

### System

- `sudo apt update` check for updates
- `sudo apt upgrade` actually download and install updates
- `lsb_release -a` check ubuntu version
- `echo` print function
- `sudo reboot` reboot
- `sudo shutdown -h now` shutdown now
- `ifconfig`
- `iwconfig`
- `ping <domain name | ip address>`
- `top` show processes; use `q` to quit
- `uname -a` check machine info
- `lsusb` list usb
- `lspci` list pci

### User & Permission

??? info "List all user"
    ```bash
    less /etc/passwd
    ```
    or
    ```bash
    users
    ```

??? info "List all groups"
    ```bash
    less /etc/group
    ```
    or
    ```bash
    groups
    ```

??? info "List all groups that a specific user belongs to"
    ```bash
    groups USER
    ```
    or
    ```bash
    id USER
    ```

??? info "List all users in a specific group"
    ```bash
    getent group GROUP
    ```

??? info "Add user to a group"
    ```bash
    usermod -aG GROUP USER
    ```
    - New group will be one of the user's secondary groups

??? info "Change user's primary group"
    ```bash
    usermod -g GROUP USER
    ```

??? info "Change current user's password"
    ```bash
    passwd
    ```

??? info "Change other user's password with sudo"
    ```bash
    sudo passwd USER
    ```

## File Permissions

!!! info "*NIX System Permissions"
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

!!! info ""
    To change directory permissions for everyone, use `u` for users, `g` for group, `o` for others, and `ugo` or `a` for all.

??? info "Change owner for all files inside a folder"
    ```bash
    sudo chown USER[:GROUP] FILE(s)
    ```

??? info "Change user permission of a file"
    ```bash
    chmod NEW_PERMISSIONS FILE
    ```

??? Examples
    ```bash
    chmod u+x example.sh
    chmod ug+r example.sh
    chmod ug-w example.sh
    chmod a+rwx example.sh
    ```

### Disk

#### Check disk utilization 

```
df -h
```

- `-h` for "Human-readable" output


#### Check file/folder size

```
du -sh {dir}
```

- `-s` for "specified" file/dir only
- `-h` for "Human-readable" output

### Navigate Around File System

- `ls` list files
- `ls -l` list files with details
- `ls -la` list all files with details including hidden files
- `cd` change directory
- `cd ..` move out / up current directory by one layer
- `cd ~` change to home Directory
- `pwd` print working directory

### Working with Files and Folders

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

secure copy

```
scp [local file] [remote user]@[remote address]:[remote path]

scp example.json root@178.128.22.33:/home/root/example
```






### Switch User

- `su -` switch to root user
- `su [username]` switch back to yourself
