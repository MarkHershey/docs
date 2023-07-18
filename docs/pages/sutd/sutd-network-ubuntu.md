# Connect to SUTD Network on Ubuntu

Contents:

1. Essential Information
2. Connect to SUTD Network on Ubuntu via Command Line Interface (CLI)
    1. Wired Connection
    2. Wireless Connection (SUTD_Wifi)



## 1. Essential Information



## 2.1 Connect to Wired SUTD Network on Ubuntu via CLI


### Resulting Network Configuration

Network Configuration is stored at the following path:

```bash
/etc/NetworkManager/system-connections/ConnectionName.nmconnection
```

which requires root access to view. The file contains the following information:

```conf
[connection]
id=ConnectionName
uuid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
type=ethernet
autoconnect-priority=-999
interface-name=enp0s31f6

[ethernet]

[802-1x]
anonymous-identity=1000000
eap=peap;
identity=1000000
password=XXXXXXXXXXXX
phase2-auth=mschapv2

[ipv4]
method=auto

[ipv6]
addr-gen-mode=stable-privacy
method=auto

[proxy]
```


## 2.2 Connect to Wireless SUTD Network (SUTD_Wifi) on Ubuntu via CLI