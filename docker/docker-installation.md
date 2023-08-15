## Install Docker Engine

Update packages

```bash
sudo apt update && sudo apt full-upgrade -y
```

Install packages to allow apt to use a repository over HTTPS

```bash
sudo apt install ca-certificates curl gnupg lsb-release
```

Add Dockers official GPG key

```bash
sudo mkdir -p /etc/apt/keyrings
```

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Use the following command to set up the repository

```bash
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine

```bash
sudo apt update
```

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## Uninstall Docker Engine

```bash
sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Delete all images, containers, and volumes

```bash
sudo rm -rf /etc/docker
```

```bash
sudo rm -rf /var/lib/docker
```

```bash
sudo rm -rf /var/lib/containerd
```