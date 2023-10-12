## Error killing pod: FailedKillPod

```shell
for p in $(kubectl get pods -n namespace-name | grep Terminating | awk '{print $1}'); do kubectl -n namespace-name delete pod $p --grace-period=0 --force;done
```