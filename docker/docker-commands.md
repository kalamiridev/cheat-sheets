## Connect into Container Shell

```sh
docker exec -it pihole bash
```

## Error Starting Docker

### Delete daemon.json if exists

```sh
rm /etc/docker daemon.json
```

```sh
systemctl restart docker
```

```sh
systemctl enable docker.service
```