## After Installation

### Debian Software

Software and Updates -> Debian Software ->
Check All

```sh
sudo apt update && sudo apt upgrade -y
```

### Install Flatpak

```sh
sudo apt install flatpak
```

Flatpak applications via a graphical user interface (GUI):

```sh
sudo apt install gnome-software-plugin-flatpak
```

Add flathub repo

```sh
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### Install Preload

```sh
sudo apt install preload
```

### Install Nvidia drivers
