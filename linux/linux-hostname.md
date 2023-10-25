## Debian/Ubuntu change Hostname (computer name) without a system restart

### Display the current hostname

```sh
hostname
```

### Type the following commands

```sh
sudo hostname <new-hostname>
```

### Next edit the /etc/hostname file and update hostname

```sh
sudo nano /etc/hostname
```

### Edit the /etc/hosts file and update the lines that reads your old-host-name

```sh
sudo nano /etc/hosts
```

## Debian/Ubuntu Linux Change Hostname Using hostnamectl

```sh
hostnamectl
```

### To change hostname

```sh
sudo hostnamectl set-hostname <new-hostname>
```
