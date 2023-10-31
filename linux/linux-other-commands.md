## Bulk Rename

```sh
ind . -type f -name "*.yaml" -exec rename 's/\.yaml$/.yml/' '{}' \;
```

## Check Debian Version

### Using hostnamectl command

```sh
hostnamectl
```

## Keeping your Debian System Secure

```sh
sudo nano /etc/apt/sources.list
```

Add Line

```
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
```

```sh
sudo apt update && sudo apt upgrade -y
```

## Region & Language

```sh
sudo nano /etc/default/locale
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

## Disable Suspend via Terminal

```sh
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
