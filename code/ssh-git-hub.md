# Configure SSH for GitHub

### Check Existing Key

```sh
is -al ~/.ssh
```
 ### If Not Exists Generate

```sh
ssh-keygen -t rsa -b 4096 -C "email@your-domain"
```

### Get Key

```sh
cat ~/.ssh/id_rsa.pub
```

### Print Key

```sh
ssh -T git@github.com
```

### Test Connection

```sh
eval "$(ssh-agent -s)"
```

### If we want our private key to be readable by the logged in user

```sh
chmod 400 ~/.ssh/id_rsa
```

### If we want our private key to be both readable and writable by the logged in user

```sh
chmod 600 ~/.ssh/id_rsa
```

### Clone 

```sh
git clone git@github.com:your-repository.git
```
