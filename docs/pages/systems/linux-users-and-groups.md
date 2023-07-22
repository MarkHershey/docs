# Linux Users & Groups

## Users

Check the list of users on the system:

```bash
cat /etc/passwd
```

Create a new user with home directory:

```bash
sudo useradd -m USERNAME
```

Set a password for a user:

```bash
sudo passwd USERNAME
```

## Groups

Add a user to a group:

```bash
sudo usermod -aG GROUP_NAME USERNAME
```

Check all groups a user belongs to:

```bash
groups USERNAME
```

Check all users in a group:

```bash
grep GROUP_NAME /etc/group
```

Remove a user from a group:

```bash
sudo gpasswd -d USERNAME GROUP_NAME
```