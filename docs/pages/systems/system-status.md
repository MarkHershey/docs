# System Status Checking One-Liners

## Get all users with UID >= 1000

```bash
awk -F: '($3>=1000 && $3<=60000 && $1 !~ /^#/ && $1 != "") {print $1}' /etc/passwd
```

## Get the CPU model

```bash
awk -F: '/model name/ {name=$2} END {print name}' /proc/cpuinfo
```

## Get the Operating System Name and Version

```bash
grep '^PRETTY_NAME=' /etc/*-release | cut -d'=' -f2 | tr -d '"'
```

```bash
echo $(grep '^NAME=' /etc/*-release | cut -d'=' -f2 | tr -d '"') $(grep '^VERSION=' /etc/*-release | cut -d'=' -f2 | tr -d '"')
```

## Get the Kernel Version

```bash
uname -r
```

## Get the Number of CPU cores

```bash
grep -c ^processor /proc/cpuinfo
```

## Get the Total Memory in Gigabytes

```bash
free -g | awk '/^Mem:/ {print $2}'
```

## Get the Total Space of all Disks

```bash
df -h -x tmpfs -x squashfs -x devtmpfs -x vfat -x efivarfs --total | grep 'total' | awk '{print $2}'
```

## Get the Total Free Space of all Disks

```bash
df -h -x tmpfs -x squashfs -x devtmpfs -x vfat -x efivarfs --total | grep 'total' | awk '{print $4}'
```