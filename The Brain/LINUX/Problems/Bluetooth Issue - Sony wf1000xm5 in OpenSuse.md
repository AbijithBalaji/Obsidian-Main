
# Fixing Bluetooth [[Issues]] with WF-1000XM5

## Step-by-Step Commands

### 1. Remove the Device (Clear Pairing Info)
Open `bluetoothctl`:
```bash
bluetoothctl
```

Remove Device 
```bash
remove AC:80:0A:FC:41:25
```

### 2. Restart the Bluetooth Service

Restart `bluetoothctl`
```bash
quit
```

Restart the Bluetooth service to clear cached data:
```bash
sudo systemctl restart bluetooth
```

### 3. Reset the Bluetooth Adapter
If restarting the service doesn’t help, reset the adapter:
``` bash
sudo rfkill block bluetooth 
sudo rfkill unblock bluetooth
```

### 4. Re-Enter Pairing Mode on the WF-1000XM5

Ensure your headphones are in pairing mode

### 5. Re-Pair the Device

Reopen `bluetoothctl`
```bash
bluetoothctl
```

Power on the adapter and set it to discoverable:
```bash
power on
scan on
```

Pair the device (replace `AC:80:0A:FC:41:25` with the detected MAC address):
```bash
pair AC:80:0A:FC:41:25
trust AC:80:0A:FC:41:25
connect AC:80:0A:FC:41:25
```


