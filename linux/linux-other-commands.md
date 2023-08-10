## Bulk Rename

```sh
ind . -type f -name "*.yaml" -exec rename 's/\.yaml$/.yml/' '{}' \;
```

## Check Debian Version 

### Using hostnamectl command

```sh
hostnamectl
```

### Using the lsb_release command
The lsb_release command can be used to find the version of a Linux OS. It might not be already installed in your OS, so you will need to first install it. Run the following command in the Terminal to install lsb_release:

```sh
apt install lsb-release
```

Once installed, run the following command in Terminal to find the version of your OS:

```sh
lsb_release -a
```

### Kernel version

```sh
uname -r
```

## Keeping your Debian System Secure

```sh
nano /etc/apt/sources.list
```

Add Line

```
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
```

```sh
apt-get update && apt-get upgrade -y
```

## Region & Language

```sh
nano /etc/default/locale
```

```conf
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_NUMERIC=hr_HR.UTF-8
LC_TIME=hr_HR.UTF-8
LC_MONETARY=hr_HR.UTF-8
LC_PAPER=hr_HR.UTF-8
LC_MEASUREMENT=hr_HR.UTF-8
```

```sh
dpkg-reconfigure locales
```