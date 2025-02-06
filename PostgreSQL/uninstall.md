### Uninstall the PostgreSQL application

```sh
sudo apt-get --purge remove postgresql
```

### Remove PostgreSQL packages

```sh
dpkg -l | grep postgres
```

```sh
sudo apt-get --purge remove <package_name>
```

### Remove PostgreSQL directories

```sh
sudo rm -rf /var/lib/postgresql/
sudo rm -rf /var/log/postgresql/
sudo rm -rf /etc/postgresql/
```

### Remove the postgres user

```sh
sudo deluser postgres
```

### Verify uninstallation

```sh
psql --version
```
