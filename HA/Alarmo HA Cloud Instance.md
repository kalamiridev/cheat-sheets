# Install Alarmo Integration on HA Cloud Instance

## Connect to container

```sh
docker exec -it ha-instance bash
```

## Create custom_components directory

```sh
mkdir -p ./config/custom_components

cd ./config/custom_components
```

## Create alarmo custom_components directory and temp directory for cloneing alarmo repository

```sh
mkdir alarmo, temp

cd temp

git clone https://github.com/nielsfaber/alarmo.git
```

## Move alarmo files from repo to custom_componets

```sh
mv /config/custom_components/temp/custom_components/alarmo/\* /config/custom_components/alarmo/
```

## Exit and restart the container

```sh
exit

docker restart ha-instance
```

## Add Integration Alarmo in HA

Settings → Devices & Services → Add Integration → Alarmo
