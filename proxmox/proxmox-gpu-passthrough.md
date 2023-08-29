# Proxmox GPU passthrough

## Step 1: Configuring the Grub

```md
nano /etc/default/grub
```

For Intel CPUs add line GRUB_CMDLINE_LINUX_DEFAULT="quiet" to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on iommu=pt pcie_acs_override=downstream,multifunction video=efifb:off"
```

For AMD CPUs:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet amd_iommu=on"
```

Once you are done editing /etc/default/grub run this command:

```md
update-grub
```

## Step 2: VFIO Modules

```md
nano /etc/modules
```

Add lines:

```
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```

## Step 3: IOMMU interrupt remapping

Run the following commands in your Shell:

```
echo "options vfio_iommu_type1 allow_unsafe_interrupts=1" > /etc/modprobe.d/iommu_unsafe_interrupts.conf
echo "options kvm ignore_msrs=1" > /etc/modprobe.d/kvm.conf
```

## Step 4: Blacklisting Drivers

```
echo "blacklist radeon" >> /etc/modprobe.d/blacklist.conf
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf
```

## Step 5: Adding GPU to VFIO

Check for the lines that show your video card.

```md
lspci -v
```

Example:

00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics]...

00:1f.3 Audio device: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller...

```md
lspci -n -s 00:02.0
lspci -n -s 00:1f.3
```

Now, we will add GPU vendor ID to the VFIO:

```
echo "options vfio-pci ids=8086:9a49,8086:a0c8 disable_vga=1"> /etc/modprobe.d/vfio.conf
```

Finally, update and restart by running the below command:

```md
update-initramfs -u
```

```md
reset
```

## Proxmox LXC Container options

```md
nano /etc/pve/lxc/<CTID>.conf
```

Add lines:

```
lxc.cgroup2.devices.allow: c 226:0 rwm
lxc.cgroup2.devices.allow: c 226:128 rwm
lxc.mount.entry: /dev/dri/renderD128 dev/dri/renderD128 none bind,optional,create=file
lxc.mount.entry: /dev/dri/card0 dev/dri/card0 none bind,optional,create=file
```

To share device on Emby change permittions on /dev/dri folder

```md
chmod -R 777 /dev/dri
```

Add /dev/dri folder to Emby docker compose

```
...
devices:
    - /dev/dri:/dev/dri
...
```