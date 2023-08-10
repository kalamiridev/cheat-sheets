## Disable proxmox commmercial repo

```md
sed -i "s/^deb/\#deb/" /etc/apt/sources.list.d/pve-enterprise.list
```

Or Comment it

```md
nano /etc/apt/sources.list.d/pve-enterprise.list
```


## Add the proxmox community repo

```md
echo "deb http://download.proxmox.com/debian/pve $(grep "VERSION=" /etc/os-release | sed -n 's/.*(\(.*\)).*/\1/p') pve-no-subscription" > /etc/apt/sources.list.d/pve-community.list
```

## Update software repositories

```md
apt update && apt full-upgrade -y
```

```md
reboot
```

## Remove no subscription nag popup proxmox 7

```md
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid sub)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js
```

## Restart pveproxy service

```md
systemctl restart pveproxy.service
```

## Optional: Install the software that will help you in the future

You will need this software sooner or later. Better install it now, to not waste any time later down the road, for example ifupdown2 will keep your host from rebooting, when you change the network config.

```md
apt-get install -y ifupdown2 bmon iftop tmux mc htop
```

## Laptop specific tuning

TLP will help with better power management and battery monitoring. Systemd/logind file entries will keep the laptop from going to sleep when the lid is closed.

```md
apt install -y tlp
```

```md
systemctl disable network-manager --now
```

```md
echo "@reboot root systemctl disable network-manager --now" >> /etc/crontab
```

```md
echo "HandleLidSwitch=ignore" >> /etc/systemd/logind.conf
```

```md
echo "HandleLidSwitchExternalPower=ignore" >> /etc/systemd/logind.conf
```

```md
echo "HandleLidSwitchDocked=ignore" >> /etc/systemd/logind.conf
```

Or edit config file

```md
nano /etc/systemd/logind.conf
```

## You can check your battery status with the next commands

```md
tlp-stat -b
```

```md
tlp-stat -s
```

Tune ZFS to use a small amount of RAM, 512Mb in this case (the maths behind the number is very simple: 512x1024x1024). I am running my testing box for a year now, with no issues or data loss. As far as I am concerned, this is safe to do, but  smart  people on the internet will definitely tell you otherwis

```md
echo "options zfs zfs_arc_max=536870912" >> /etc/modprobe.d/zfs.conf
```

## Upgrade the system

```md
apt -y dist-upgrade
```

```md
reboot
```