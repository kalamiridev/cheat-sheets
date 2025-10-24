# Proxmox iSCSI

## Resize disk - Rescan iSCSI node and resize disk

Rescan

```md
iscsiadm -m node --rescan
```

Check size

```md
ilsblk /dev/sda
```

Resize

```md
pvresize /dev/sda
```

## After removing iscsi logout from sessions

Check sessions

```md
iscsiadm -m session
```

Session logout

```md
iscsiadm -m node -T iqn.2000-01.com.synology:pve-target.06e2120d16e -u
```
