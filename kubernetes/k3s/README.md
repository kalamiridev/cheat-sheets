# K3S Installation

[K3S Documentation](https://docs.k3s.io)

## Disable Firewal - Ubuntu, Debian

```bash
sudo ufw disable
```

## Install and Configuration Flags with install script

```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable servicelb --disable traefik --write-kubeconfig-mode 644 --kube-apiserver-arg default-not-ready-toleration-seconds=30 --kube-apiserver-arg default-unreachable-toleration-seconds=30 --kube-controller-arg node-monitor-period=20s --kube-controller-arg node-monitor-grace-period=20s --kubelet-arg node-status-update-frequency=5s" sh - 
```
**Admin Kubeconfig Options Flag, no sudo**  
--write-kubeconfig-mode 644

**Customized Flags for Kubernetes Processes**  
--kube-apiserver-arg  
--kube-controller-arg  
--kubelet-arg

**Listeners Flag - for loadbalancer on front**  
 sh -s - server --tls-san load_balancer_ip_or_hostname

**Node Labels and Taints for Agents Flag - No pods scheduled on server node**  
sh -s - server --node-taint CriticalAddonsOnly=true:NoExecute

## Get Node Token 

```bash
sudo cat /var/lib/rancher/k3s/server/node-token
```

## Join K3S Cluster

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://<your-ip>:6443 K3S_TOKEN=<your-token> sh -
```

## Delete the node from cluster

1. Find the node 
```bash
kubectl get nodes
``` 
2. Drain the node
```bash
kubectl drain <node-name>
```

3. Delete the node
```bash
kubectl delete node <node-name>
```

## Deploy an autoscaler

```bash
kubectl autoscale deploy/<container-name> -n <namespace> --cpu-percent=95 --min=3 --max=10
```