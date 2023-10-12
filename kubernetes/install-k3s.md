## Install K3S

```bash
curl -sfL https://get.k3s.io | K3S_KUBECONFIG_MODE="644" INSTALL_K3S_EXEC="server --disable traefik --disable servicelb" sh - 
```

## Get Node Token 

```bash
cat /var/lib/rancher/k3s/server/node-token
```


## Join K3S Cluster

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://your-ip:6443 K3S_TOKEN=your-token sh -
```

