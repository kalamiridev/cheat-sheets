# SSH Support

## Installation

```sh
sudo apt install openssh-server
```

### Check status

```sh
sudo systemctl status ssh
```

### Start SSH automatically on boot

```sh
sudo systemctl enable ssh
```

## Configuration

```sh
sudo nano /etc/ssh/sshd_config
```

## SSH Keys

### Create SSH Key RSA

```sh
ssh-keygen
```

### Create SSH Key ED25519 (more secure and shorter key)

```sh
ssh-keygen -t ed25519 -C "comment"
```

### View public key

```sh
cat ~/.ssh/id_rsa.pub
```

## Copy Public SSH Key

### If ssh folder and file not exists

**Login as user**

```sh
mkdir ~/.ssh
```

```sh
cd ~/.ssh
```

```sh
touch authorized_keys
```

**Check Permissions**

```sh
ls -ld ~/.ssh
```

```sh
ls -ld ~/.ssh/authorized_keys
```

### Set Permissions if not match

- chmod 700 ~/.ssh
- chmod 600 ~/.ssh/id_rsa
- chmod 644 ~/.ssh/authorized_keys

### Copy public key to remote machine from Linux

```sh
ssh-copy-id -i ~/.ssh/id_ed25519.pub user@your-machine-ip
```

### Copy public key to remote machine from Windows

```
scp C:\Users\User\.ssh\id_rsa.pub user@your-machine-ip:~/.ssh/authorized_keys
```

### View authorized keys on remote machine

```sh
cat .ssh/authorized_keys
```

### Edit SSH config

```sh
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

```sh
sudo nano /etc/ssh/sshd_config
```

```config
Include /etc/ssh/sshd_config.d/*.conf

PermitRootLogin no
PasswordAuthentication no

KbdInteractiveAuthentication no

UsePAM yes

X11Forwarding yes
PrintMotd no

AcceptEnv LANG LC_*

Subsystem       sftp    /usr/lib/openssh/sftp-server
```

```sh
sudo systemctl restart ssh
```

### Download Config File

```sh
scp /etc/ssh/sshd_config user@your-machine-ip:/home/user/Downloads
```

### Remove Hosts

```sh
 rm -f .ssh/known_hosts
 ssh-keygen -R "hostname"
```
