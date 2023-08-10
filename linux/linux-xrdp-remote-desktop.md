## Instalation

```sh
apt install xrdp -y 
```

## Status

```sh
systemctl status xrdp 
```

## Configuring Xrdp Service

```sh
sudo usermod -a -G ssl-cert xrdp
sudo nano /etc/xrdp/startwm.sh 
```

```
---
if test -r ~/.profile; then
        . ~/.profile
fi

# Add two lines 
Unset DBUS_SESSION_ADDRESS
Unset XDG_RUNTIME_DIR


test -x /etc/X11/Xsession && exec /etc/X11/Xsession
...
```

### Restart Service

```sh
systemctl restart xrdp
```

## XRDP Change Desktop Envirement

```sh
sudo update-alternatives --config x-session-manager
```
> ' * 2 /usr/bin/gnome-session '

## XRDP Croatian Keyboard Layout 

### Edit Config file
```sh
sudo nano /etc/xrdp/xrdp_keyboard.ini
```

### Add 

```conf
[default_rdp_layouts]
rdp_layout_hr=0x0000041A

[default_layouts_map]
rdp_layout_hr=hr
```
