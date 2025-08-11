#### FATAL: no pg_hba.conf entry for host "172.18.0.2",

```sh
cd /etc/postgresql/17/main
```

```sh
sudo nano pg_hba.conf
```

Add line:

```
# IPv4 local connections
host        all         all         172.18.0.1/32       md5
```
