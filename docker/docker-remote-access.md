# Configuring remote access with systemd unit file

1. Use the command to open an override file for `docker.service` in a text editor.

```console 
sudo systemctl edit docker.service 
``` 
2. Add or modify the following lines, substituting your own values.

```systemd
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://0.0.0.0:2375
```
3. Save the file.

4. Reload the `systemctl` configuration.

```bash
sudo systemctl daemon-reload
```

5. Restart Docker.

```shell
sudo systemctl restart docker.service
```

6. Verify that the change has gone through.

```console 
sudo netstat -lntp | grep dockerd
```