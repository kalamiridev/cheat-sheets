# Node Exporter on Linux

## Installing and running the Node Exporter

### 1. Download Node Exporter it from the Prometheus [downloads page](https://prometheus.io/download#node_exporter) extract it, and run it:

```ch
# NOTE: Replace the URL with one from the downloads page.
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.1/node_exporter-1.8.1.linux-amd64.tar.gz
```

### 2. Extract it

```sh
tar xvfz node_exporter-1.8.1.linux-amd64.tar.gz.tar.gz
```

### 3. Move extracted file to local bin folder

```sh
sudo mv node_exporter-1.8.1.linux-amd64/node_exporter /usr/local/bin/node_exporter
```

## Running Node Sxporter as service.

### 1. Create service

```sh
sudo nano /etc/systemd/system/node_exporter.service
```

### 2. Add a systemd Service Unit

```
[Unit]
Description=Node Exporter
After=network.target

[Service]
ExecStart=/usr/local/bin/node_exporter
Restart=always

[Install]
WantedBy=default.target
```

### 3. Reload Systemd and Start Node Exporter

```sh
sudo systemctl daemon-reload
```

```sh
sudo systemctl start node_exporter
```

```sh
sudo systemctl enable node_exporter
```

### 4. Verify the Service

```sh
sudo systemctl status node_exporter
```

### 5 Node Exporter metrics

```sh
curl http://localhost:9100/metrics
```
