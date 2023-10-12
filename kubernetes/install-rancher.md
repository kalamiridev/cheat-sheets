## Install Docker for Ubuntu

```bash
curl https://releases.rancher.com/install-docker/20.10.sh | sh
```

## Install Rancher Docker Container

```docker
sudo docker run --name=rancher --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
```

