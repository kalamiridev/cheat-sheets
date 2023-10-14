## Disable Firewal - Ubuntu, Debian

```bash
sudo ufw disable
```

## Install K3S

```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable servicelb --disable traefik --write-kubeconfig-mode 644 --kube-apiserver-arg default-not-ready-toleration-seconds=30 --kube-apiserver-arg default-unreachable-toleration-seconds=30 --kube-controller-arg node-monitor-period=20s --kube-controller-arg node-monitor-grace-period=20s --kubelet-arg node-status-update-frequency=5s" sh - 
```
### No pods scheduled on server node
sh -s - server --node-taint CriticalAddonsOnly=true:NoExecute

### For loadbalancer on front
sh -s - server --tls-san load_balancer_ip_or_hostname

## Get Node Token 

```bash
sudo cat /var/lib/rancher/k3s/server/node-token
```

## Join K3S Cluster

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://your-ip:6443 K3S_TOKEN=your-token sh -
```

