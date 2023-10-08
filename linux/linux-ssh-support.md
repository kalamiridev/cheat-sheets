# SSH Support

## Installation

```sh
apt install openssh-server
```

## Configuration

```sh
nano /etc/ssh/sshd_config
```

## Status

```sh
systemctl status ssh
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
nano /etc/ssh/sshd_config
```

```config
PermitRootUser no
PasswordAuthentication no
```

```sh
systemctl restart ssh
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

### Start SSH automatically on boot

```sh
sudo systemctl enable ssh
```