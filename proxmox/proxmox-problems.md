**Error:** Failed to start pvestatd.service after update because hostname was changed  
**Solution:** Change [hostname](https://github.com/kalamiridev/cheat-sheets/blob/f5bbee0e3ebcec5a7c00ca563342f620d7858f4b/linux/linux-hostname.md)

**Error:** Backup job failed
```shell
nano /etc/vzdump.conf 
```
**Solution:** Add tmpdir into vzdump.conf 
```shell
# vzdump default settings
tmpdir: /tmp
#tmpdir: DIR
```