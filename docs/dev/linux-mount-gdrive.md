# Mount Google Drive on Headless Linux (Ubuntu)

!!! info ""

    `google-drive-ocamlfuse` is a FUSE filesystem for Google Drive, written in OCaml. 

    GitHub: [astrada / google-drive-ocamlfuse](https://github.com/astrada/google-drive-ocamlfuse)

## Install [google-drive-ocamlfuse](https://astrada.github.io/google-drive-ocamlfuse/)

```bash
sudo add-apt-repository ppa:alessandro-strada/ppa
```

```bash
sudo apt-get update && sudo apt-get install google-drive-ocamlfuse
```

## Headless Authorization - Simple trick

!!! info ""
    Reference: [google-drive-ocamlfuse: Headless Usage & Authorization](https://github.com/astrada/google-drive-ocamlfuse/wiki/Headless-Usage-&-Authorization#simple-another-way)

```bash
echo $'#!/bin/sh\necho $* > /dev/stderr' > xdg-open
```

```bash
chmod 755 xdg-open
```

```bash
env PATH=`pwd`:$PATH google-drive-ocamlfuse
```

## Mounting Google Drive

!!! info ""
    Let's say we want to mount Google Drive to `~/G_DRIVE` for example

Create a new directory serve as the mounting point

```bash
cd ~
mkdir G_DRIVE
```

Mount to the directory
```bash
google-drive-ocamlfuse G_DRIVE
```

## Unmounting

```bash
fusermount -u G_DRIVE
```

or 

```bash
umount G_DRIVE
```