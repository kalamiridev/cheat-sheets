# Creating New Users in Linux

## Creating new users in Linux does the following:
1. Provides a unique UID and GID
    > 0 is reserved for root and assigned automatically.  
    > 1-999 is for system accounts and services.  
    > 1000 and above are for regular users.  
2. Edits files that store account information
    > /etc/passwd - Lists all registered users on the system.  
    > /etc/shadow - Stores encrypted user passwords.  
    > /etc/group - Defines user groups.  
    a> /etc/gshadow - Stores encrypted group passwords.

### Add User

```sh
sudo adduser your-username
```

### Install sudo

```sh
apt install sudo
```

### Add user to sudo group

```sh
usermod -aG sudo your-username
```

### View user id

```sh
sudo id your-username
```

### Connect as other user

```sh
su your-username
```