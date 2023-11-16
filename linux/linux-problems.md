### **Problem**: Microsoft Edge has locked this profile to prevent corruption. If you're sure no other processes are using this profile, you can unlock it and relaunch Microsoft Edge.

### **Solution**:

```shell
sudo rm -rf  ~/.config/microsoft-edge/Singleton*
```
