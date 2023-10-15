# MetalLB Installation

[MetalLB Documentation](https://metallb.universe.tf/)

## Instalation By Manifest

```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.11/config/manifests/metallb-native.yaml
```

# MetalLB Configuration

## Defining The IPs To Assign To The Load Balancer Services

```yml
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: default-pool
  namespace: metallb-system
spec:
  addresses:
  - 192.168.99.220-192.168.99.250
  autoAssign: false # Controlling automatic address allocation
```

## Announce The Service IPs Layer 2 Configuration

```yml
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: default
  namespace: metallb-system
spec:
  ipAddressPools:
  - default-pool
```