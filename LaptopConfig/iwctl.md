To connect to a Wi-Fi network using `iwctl`, the command-line tool for managing wireless networks on Linux, follow these steps:

1. **Launch iwctl**:
   Open a terminal and start `iwctl` by typing:
   ```sh
   sudo iwctl
   ```

2. **List Available Devices**:
   Identify your wireless device:
   ```sh
   device list
   ```

3. **List Available Networks**:
   Scan for available Wi-Fi networks:
   ```sh
   station <device_name> scan
   ```

4. **Show Scanned Networks**:
   After scanning, display the list of networks:
   ```sh
   station <device_name> get-networks
   ```

5. **Connect to a Network**:
   Connect to the desired network using its SSID:
   ```sh
   station <device_name> connect <SSID>
   ```
   If the network requires a password, you will be prompted to enter it.

6. **Exit iwctl**:
   After successfully connecting, exit `iwctl` by typing:
   ```sh
   exit
   ```

**Example**:
Assume your wireless device is named `wlan0` and you want to connect to a network with the SSID `MyNetwork`. The commands would be:
```sh
sudo iwctl
device list
station wlan0 scan
station wlan0 get-networks
station wlan0 connect MyNetwork
exit
```

This sequence will connect your device to the specified Wi-Fi network.
