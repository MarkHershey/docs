# SSH Authentication

## Three methods of Authentication

`ssh username@hostname`

1. Password Authentication (Secret-key/ Symmetric Cryptography)
2. Public Key Authentication (Asymmetric Cryptography)
3. Host Based Authentication (Whitelisting)



## Setting up Public Key Authentication

The motivation for using public key authentication over simple passwords is security. Public key authentication provides cryptographic strength that even extremely long passwords can not offer. With SSH, public key authentication improves security considerably as it frees the users from remembering complicated passwords (or worse yet, writing them down).

Each SSH key pair includes two keys:

- A **public key** that is copied to the SSH server(s). Anyone with a copy of the public key can encrypt data which can then only be read by the person who holds the corresponding private key. Once an SSH server receives a public key from a user and considers the key trustworthy, the server marks the key as authorized in its authorized_keys file. Such keys are called authorized keys.

- A **private key** that remains (only) with the user. The possession of this key is proof of the user's identity. Only a user in possession of a private key that corresponds to the public key at the server will be able to authenticate successfully. The private keys need to be stored and handled carefully, and no copies of the private key should be distributed. The private keys used for user authentication are called identity keys.

Reference: [www.ssh.com/ssh/public-key-authentication](https://www.ssh.com/ssh/public-key-authentication)


### Step 1: Generate an SSH Key

Run `ssh-keygen -t rsa` in terminal and follow its instructions,

or `ssh-keygen -t rsa -b 4096` for extra enhanced security.

>- `-t` “Type” This option specifies the type of key to be created. Commonly used values are:
>   - `rsa` for RSA keys
>   - `dsa` for DSA keys
>   - `ecdsa` for elliptic curve DSA keys
>
>
>- `-b` “Bits” This option specifies the number of bits in the key. The regulations that govern the use case for SSH may require a specific key length to be used. In general, 2048 bits is considered to be sufficient for RSA keys.
>
> Reference: [www.ssh.com/ssh/keygen/](https://www.ssh.com/ssh/keygen/)

Key pair generated will be stored at the following path by default:

- `~/.ssh/id_rsa` (Private Key)
- `~/.ssh/id_rsa.pub` (Public Key)





### Step 2: Add the public key to a server

Public key should be copied into your target server's `~/.ssh/authorized_keys` file. Use either one of the following methods to do that.

##### Method 1: Manual

1. SSH into your server using password authentication.
2. Create the `.ssh/` folder under home directory if it doesn't exist.
3. Create the `authorized_keys` file under `.ssh/` folder if it doesn't exist, no file extension needed.
4. Copy your public key from `~/.ssh/id_rsa.pub` at your local machine to the `~/.ssh/authorized_keys` file on your server.

5. You might need to change the permission of the folder.
```
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/*
```

or

```
cat ~/.ssh/id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```

##### Method 2: Using `ssh-copy-id`

*Linux user can use this command by default, macOS user need to install it first by `brew install ssh-copy-id`.*

```
ssh-copy-id user@host
```

or use `-i` to explicitly specify which key to be copied over:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@host
```
- `-i` Specifies the identity file that is to be copied (default is `~/.ssh/id_rsa`). If this option is not provided, this adds all keys listed by `ssh-add -L`. Note: it can be multiple keys and adding extra authorized keys can easily happen accidentally!


> **How `ssh-copy-id` works**
>
> ssh-copy-id uses the SSH protocol to connect to the target host and upload the SSH user key. The command edits the authorized_keys file on the server. It creates the .ssh directory if it doesn't exist. It creates the authorized keys file if it doesn't exist. Effectively, ssh key copied to server.
>
>It also checks if the key already exists on the server. Unless the -f option is given, each key is only added to the authorized keys file once.
>
>It further ensures that the key files have appropriate permissions. Generally, the user's home directory or any file or directory containing keys files should not be writable by anyone else. Otherwise someone else could add new authorized keys for the user and gain access. Private key files should not be readable by anyone else.
>
> Reference: [www.ssh.com/ssh/copy-id](https://www.ssh.com/ssh/copy-id)







### Step 3: Turn Off Password Authentication

Make a copy of the config file just in case
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

Edit the config file:
```
sudo nano /etc/ssh/sshd_config
```

Ensure these two lines exist and it is uncommented:
```
PubkeyAuthentication yes
PasswordAuthentication no
```

Restart the SSH service
```
sudo service ssh restart
```
or
```
sudo systemctl reload sshd.service
```

### Step 4: Test your connection

```
ssh user@host
```
or specify your key explicitly:
```
ssh -i ~/.ssh/mykey user@host
```
- OpenSSH only allows a maximum of five keys to be tried automatically. If you have more keys, you must specify which key to use using the `-i` option to `ssh`.

### Additional Note for Server Setup

#### create new user

- `adduser <username>` add linux user
- `id <username>` check user permissions
- `usermod -aG sudo <username>` grant root permission to user
- `id <username>` check user permissions

#### set up SSH key under new user

- `cd /home/<username>`
- refer from Step 2

#### disable password authentication and root login

- `PasswordAuthentication no`
- `PermitRootLogin no`
- `sudo systemctl reload sshd`

#### change owner of new user's home folder from root to new user

- `sudo chown -R <username>:<username> /home/<username>`
- `chmod 700 /home/<username>/.ssh`

### Additional Note for GitHub Setup

- Step 1: Key Generation
- Step 2: Copy and paste the public key to your [Github > Settings > SSH and GPG keys](https://github.com/settings/keys)
- Step 3: `ssh-add ~/.ssh/<your-key-name>`

>- `ssh-add` adds private key identities (from your `~/.ssh` directory) to the authentication agent (`ssh-agent`), so that the ssh agent can take care of the authentication for you.
>
>- In Unix, `ssh-agent` is a background program that handles passwords for SSH private keys. The `ssh-add` command prompts the user for a private key password and adds it to the list maintained by `ssh-agent`. Once you add a password to `ssh-agent`, you will not be prompted for it when using `SSH` or `scp` to connect to hosts with your public key.
>
>Reference:
>   - [What exactly does ssh-add do?](https://superuser.com/questions/360686/what-exactly-does-ssh-add-do)
>   -[About ssh-agent and ssh-add in Unix](https://kb.iu.edu/d/aeww)
>   -[Understanding ssh-agent and ssh-add](http://blog.joncairns.com/2013/12/understanding-ssh-agent-and-ssh-add/)


### Start SSH Agent
```
eval "$(ssh-agent -s)"
```
