# NPS

[ehang-io/nps](https://github.com/ehang-io/nps) is a lightweight, high-performance, powerful intranet penetration proxy server, with a powerful web management terminal.

- get latest [release](https://github.com/ehang-io/nps/releases)

## Setup Server (Public Cloud) Side

Download

for AMD64 Ubuntu Server
```bash
wget https://github.com/ehang-io/nps/releases/download/v0.26.9/linux_amd64_server.tar.gz
```

Extract
```bash
tar -xvf linux_amd64_server.tar.gz
```

Install
```bash
sudo ./nps install
```

Configure after installation
```bash
nano /etc/nps/conf/nps.conf
```

Visit Web Dashboard at `xxx.xxx.xxx.xxx:8080`
- default user `admin`
- default pass `123`

Create Client Record

## Setup Client (Private Target) Side

**Download**

for AMD64 Ubuntu Client
```bash
wget https://github.com/ehang-io/nps/releases/download/v0.26.9/linux_amd64_client.tar.gz
```

**Register to system**
```bash
sudo ./npc install -server=xxx.xxx.xxx.xxx:8024 -vkey=xxx
```

**Startup**
```bash
sudo npc start
```

**Stop**
```bash
sudo npc stop
```

**Deregister**
```bash
./npc uninstall
```

**Update**
```bash
sudo npc stop && sudo npc-update update
```