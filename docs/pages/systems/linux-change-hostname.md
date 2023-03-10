# Change Hostname in Linux

## Check current hostname

```bash
hostname
```

## Temporary change hostname

```bash
hostname NEW_HOSTNAME
```

This will change the hostname for the current session only. Hostname will be reset to the original one after reboot.

## Permanent change hostname

Use `hostnamectl` to change the hostname, this will change the hostname in `/etc/hostname` file and take effect immediately without reboot.

```bash
sudo hostnamectl set-hostname NEW_HOSTNAME && sudo systemctl restart systemd-hostnamed
```

However, you still need to manually update `/etc/hosts` file

```bash
sudo nano /etc/hosts
```

Replace any `OLD_HOSTNAME` with `NEW_HOSTNAME`, new line should look like this:

```bash
127.0.0.1 localhost
127.0.1.1 NEW_HOSTNAME
```