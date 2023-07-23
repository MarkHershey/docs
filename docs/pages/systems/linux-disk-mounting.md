# Linux Disk Mounting

## Mount a disk temporarily


```bash
#    mount <device>  <mount point>
sudo mount /dev/sdb1 /mnt/folder
```

## Mount a disk permanently

#### Step 1: Find the UUID of the disk

```bash
sudo blkid | grep UUID
```

#### Step 2: Add the disk to `/etc/fstab`

Open `/etc/fstab` with `vim` or `nano`:

```bash
sudo vim /etc/fstab
```

Which should have the following structure:

```bash
# <file system> <mount point>   <type>  <options>  <dump>  <pass>
UUID=abcd1234   /mnt/data        ext4    defaults    0       2
```

- `<file system>`: This can be in the form of a Universally Unique Identifier (UUID), a label (LABEL=somelabel), or a device file (`/dev/sdX1`). UUID is the most reliable option.
- `<mount point>`: the directory to mount the disk. It should be an empty directory.
- `<type>`: `ext4` or `ntfs` or `vfat` or `exfat` or `auto`. `auto` will automatically detect the file system.
- `<options>`: `defaults` or specific options, separated by commas. See below for more details.
- `<dump>`: `0` or `1` (This is a binary flag that indicates whether the dump utility should backup the filesystem. In the modern system, this is usually set to `0` since other backup solutions are often used.)
- `<pass>`: `0`, `1`, or `2` (This is used by the `fsck` program that checks the filesystem for errors at boot time. The root filesystem should have this set to `1`, while all other file systems should have it set to `2` (check after root) or `0` (no check).)


#### More about Mounting Options

The mount options in the `/etc/fstab` file control how the filesystem will be mounted. There are many mount options available, and some are specific to certain filesystems. Here are some of the most common options:

1. **defaults**: This option is a combination of multiple options which are `rw`, `suid`, `dev`, `exec`, `auto`, `nouser`, and `async`.
2. **rw**: This option allows the filesystem to be mounted as read-write. This means you can read, write, and execute files from this filesystem.
3. **ro**: This option mounts the filesystem as read-only. You will not be able to modify any files on this filesystem.
4. **auto**: This option tells the system to automatically mount the filesystem at startup.
5. **noauto**: This option tells the system not to automatically mount the filesystem at startup. You will need to manually mount the filesystem.
6. **user**: This option allows normal users to mount the filesystem. This is typically used for removable devices.
7. **nouser**: This option means that only the root user can mount the filesystem. This is the default option.
8. **sync**: All input/output operations should be performed synchronously. In contrast with `async`, changes to files are made as soon as requests for changes are made.
9. **async**: All input/output operations should be performed asynchronously. This is the default option. In this case, requests for changes to files on the filesystem are not made immediately.
10. **exec**: Permit the execution of binaries that are on the filesystem.
11. **noexec**: Do not allow direct execution of any binaries on the mounted filesystem.
12. **suid**: Allow operation of `suid`, and `sgid` bits. These are special permissions that allow a program to run with the permissions of the owner (or group) regardless of who runs them.
13. **nosuid**: Blocks the operation of `suid`, and `sgid` bits.
14. **nodev**: Do not interpret character or block special devices on the file system.
15. **dev**: Interpret character or block special devices on the file system.
16. **user**: Allow any user to mount and unmount the filesystem.
17. **nouser**: Only allow root to mount and unmount the filesystem. This is the default option.
18. **_netdev**: This option is used for network filesystems such as NFS and SMB. It tells the system that the filesystem should be mounted after bringing up the network.

These are the most common options, but there are more options available which are specific to certain filesystems. For example, the `ext4` filesystem has `journal`, `noload`, `data=journal` and many more. You can check the manual page for mount (`man mount`) for a full list of options.
