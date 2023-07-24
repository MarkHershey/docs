# Switch between GUI and CLI in Linux

## Switch to GUI

```bash
sudo systemctl isolate graphical.target
```

This command switches the runlevel to a graphical interface. Runlevels are modes that define what processes can run in the system. The "graphical.target" is similar to the traditional runlevel 5, which starts the system normally with a display manager (i.e., GUI).

## Switch to CLI

```bash
sudo systemctl isolate multi-user.target
```

This command switches the runlevel to a multi-user, non-graphical interface, similar to the traditional runlevel 3. This starts the system in multi-user text mode. The multi-user target does not start a graphical session.

## Set a default target

```bash
sudo systemctl set-default graphical.target
```

This command sets the default runlevel to be a graphical interface for future boots. It creates a symbolic link from `/etc/systemd/system/default.target` to `/usr/lib/systemd/system/graphical.target`.

Every time the system is booted, systemd checks the default target and starts the services configured under that target.

## Check current target

```bash
systemctl get-default
```

This command shows the current default target (i.e., the target that will be used during the next system boot).