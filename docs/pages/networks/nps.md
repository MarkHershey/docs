# NPS

[ehang-io/nps](https://github.com/ehang-io/nps) is a lightweight, high-performance, powerful intranet penetration proxy server, with a powerful web management terminal.

- get latest [release](https://github.com/ehang-io/nps/releases)

## Setup Server (Public Cloud) Side

**Download**

for AMD64 Ubuntu Server
```bash
wget https://github.com/ehang-io/nps/releases/download/v0.26.10/linux_amd64_server.tar.gz
```

**Extract**
```bash
tar -xvf linux_amd64_server.tar.gz
```

**Install**
```bash
sudo ./nps install
```

**Configure**

- Replace default `web_username` and `web_password`

```bash
nano /etc/nps/conf/nps.conf
```

**Allow UFW**

```bash
sudo ufw allow 8080,8024
sudo ufw show added
sudo ufw enable
```

**Start NPS Server**

```bash
nps start # start nps server
nps restart # restart nps server
nps stop # stop nps server
nps reload # reload config file
```

**Visit Web Dashboard** at `xxx.xxx.xxx.xxx:8080`

- default user `admin`
- default pass `123`

**Create Client Record**

- Give it a name
- `Unique verify Key` is the `vkey` we will be using from the client side, you can let it generate automatically or specify your own.
- Confirm


## Setup Client (Private Target) Side

**Download**

for AMD64 Ubuntu Client
```bash
wget https://github.com/ehang-io/nps/releases/download/v0.26.10/linux_amd64_client.tar.gz
```

**Extract**
```bash
tar -xvf linux_amd64_client.tar.gz
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