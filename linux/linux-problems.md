### **Problem**: Microsoft Edge has locked this profile to prevent corruption. If you're sure no other processes are using this profile, you can unlock it and relaunch Microsoft Edge.

### **Solution**:

```shell
sudo rm -rf  ~/.config/microsoft-edge/Singleton*
```

## Package lists error:

E: Failed to fetch http://ba.archive.ubuntu.com/ubuntu/dists/noble-updates/main/i18n/Translation-en.xz

### **Solution**:

Remove package list region ba. from URL

```shell
sudo nano /etc/apt/sources.list.d/ubuntu.sources
```

```
Types: deb
URIs: http://hr.archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

to

```
Types: deb
URIs: http://archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

```shell
sudo nano /etc/apt/sources.list
```

Check lists

```shell
ls /var/lib/apt/lists
```
