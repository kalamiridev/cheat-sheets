## Commands


> **df** - disk free  
> **du** - disk usage


## Display Usage in Megabytes and Gigabytes

```sh
df -h
```

## Display a Specific File System

```sh
df -h /
```

## Remove directory
> Use the rmdir or **rm -d** command to remove empty directories.  
> Use the **rm -r** command to remove non-empty directories.

```sh
rm -d -r ~/.ssh
```

## Check Permitions

### For directory

```sh
ls -ld directory-name
```

- indicates the beginning of the command options.

> **l** - asks for a long list which includes the permissions.  
> **d** - indicates that the list should concern the named directory itself; not its contents. If no directory name is given, the list output will pertain to the current directory.

### For file

```sh
ls -lh file-name
```