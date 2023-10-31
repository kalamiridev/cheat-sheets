## Bulk Rename

```sh
ind . -type f -name "*.yaml" -exec rename 's/\.yaml$/.yml/' '{}' \;
```

## Check Debian/Ubuntu Version using hostnamectl command

```sh
hostnamectl
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

**Or**

```sh
sudo dpkg-reconfigure locales
```

## Disable Suspend via Terminal

```sh
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
