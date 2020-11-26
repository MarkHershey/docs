# Frequently Used Linux Commands

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
-  `uname -a` check machine info
- `blkid` check hard drive
- `df` disk info
- `lsusb` list usb
- `lspci` list pci



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

>More about removing directories: [How to Remove (Delete) Directory in Linux](https://linuxize.com/post/remove-directory-linux/)

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


change owner for all files inside a folder

```
sudo chown -R username:username [folder]
```

change user permission of a file

```
chmod [updated permissions] [filename]
chmod u+e example.sh
```



### Switch User

- `su -` switch to root user
- `su [username]` switch back to yourself
