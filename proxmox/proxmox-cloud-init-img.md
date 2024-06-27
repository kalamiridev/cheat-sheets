# Proxmox cloud-init template

## Step 1: Download cloud image

Download image [Ubuntu Cloud Images](https://cloud-images.ubuntu.com/)

```md
wget https://cloud-images.ubuntu.com/noble/current/noble-server-cloudimg-amd64.img
```

## Step 2: Create Proxmox VM

```md
sudo qm create 9000 --memory 2048 --core 1 --name ubuntu-cloud --net0 virtio,bridge=vmbr0
```

## Step 3: Import downloaded image to local storage

```md
sudo qm disk import 9000 noble-server-cloudimg-amd64.img local-lvm
```

### Step 4: Attach the new disk to the vm

```md
sudo qm set 9000 --scsihw virtio-scsi-pci --scsi0 local:vm-9000-disk-0
```

### Step 5: Add cloud init drive

```md
sudo qm set 9000 --ide2 local-lvm:cloudinit
```

### Step 6: Make the cloud init drive bootabl

```md
sudo qm set 9000 --boot c --bootdisk scsi0
```

### Step 7: Add serial console

```md
sudo qm set 9000 --serial0 socket --vga serial0
```

### Step 8: Add cload-init properties

### Step 9: Convert to Tempate
