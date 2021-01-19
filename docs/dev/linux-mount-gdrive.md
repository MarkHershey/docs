# Mount Google Drive on Headless Linux (Ubuntu)

!!! info ""
    Reference: [google-drive-ocamlfuse: Headless Usage & Authorization](https://github.com/astrada/google-drive-ocamlfuse/wiki/Headless-Usage-&-Authorization)

## Install [google-drive-ocamlfuse](https://astrada.github.io/google-drive-ocamlfuse/)

```bash
sudo add-apt-repository ppa:alessandro-strada/ppa
```

```bash
sudo apt-get update && sudo apt-get install google-drive-ocamlfuse
```

## Simple trick

```bash
echo $'#!/bin/sh\necho $* > /dev/stderr' > xdg-open
```

```bash
chmod 755 xdg-open
```

```bash
env PATH=`pwd`:$PATH google-drive-ocamlfuse
```