# Install NVIDIA Driver on Ubuntu

## Install NVIDIA driver

```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
```

```bash
sudo apt update && sudo apt install ubuntu-drivers-common
```

```bash
sudo ubuntu-drivers autoinstall
```

```bash
sudo apt install xserver-xorg-video-nvidia-418 nvidia-driver-418
```

reference: https://askubuntu.com/a/1130926 



## Install `nvtop`

- [nvtop](https://github.com/Syllo/nvtop)

```bash
sudo apt update && sudo apt install nvtop
```