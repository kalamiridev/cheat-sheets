## Instalation

```sh
apt install nfs-common nfs-kernel-server
```

### Create New Directory to Mount

```sh
mkdir -p /foldername
```

### Mount NFS Shared Directory to Created Directory

```sh
mount -t nfs your-machine-ip:/volume1/foldername /home/user/foldername
```

### Take ownership

```sh
chown sasa /home/user/foldername
```

### Check Ownership

```sh
df -h /home/user/foldername
```

### Permanently mount on Reboot

```sh
nano /etc/fstab
```

Add line

```
your-machine-ip:/volume1/foldername      /foldername       nfs     defaults        0       0
```

### Mount using Webmin UI

1. Tools -> File Manager -> Add Directory
2. Netowrk Filesystem (nfs) -> System -> Disk and Network Filesystem

### Unmount
```sh
umount -f -l /foldername
```

> -f – Force unmount (in case of an unreachable NFS system. Requires kernel 2.1.116 or later.)  
> -l – Lazy unmount. Detach the filesystem from the filesystem hierarchy now, and cleanup all references to the filesystem as soon as it is not busy anymore. (Requires kernel 2.4.11 or later.)

### NAS nfs Plex Privilages

NFS Permition -> Squash: Map all users to admin