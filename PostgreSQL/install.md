# Installation & Configuration with pgVector

### Install it from the official repository

```sh
sudo apt install -y postgresql-common
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
```

### Install pgvector

```sh
sudo apt install postgresql-17-pgvector -y
```

### Enable the pgvector extension

```sh
sudo -u postgres psql
```

```sh
CREATE EXTENSION vector;
```

### Start PostgreSQL automatically

```sh
sudo systemctl enable postgresql
sudo service postgresql start
```

### Make it accessible via an IP address

```sh
/etc/postgresql/{version}/main/postgresql.conf
```

Change line:

listen_addresses = '\*'

### Check versions

```sh
sudo apt list --installed | grep postgresql
```

### Configure PostgreSQL to Allow Remote Connections

```sh
/etc/postgresql/{version}/main/pg_hba.conf
```

Change to local network

| TYPE | DATABASE | USER | ADDRESS        | METHOD |
| ---- | -------- | ---- | -------------- | ------ |
| host | all      | all  | 192.168.1.2/32 | md5    |

### Restart service

```sh
sudo systemctl restart postgresql
```
