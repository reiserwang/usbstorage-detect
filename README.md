# usbstorage-detect
A Linux system service sample for detecting USB storage


1. Create a new file called 'usb-deterct.service' in the '/etc/systemd/system' directory with following contents

```css
[Unit]
Description=USB storage detection service

[Service]
Type=simple
ExecStart=/path/to/your/script.sh

[Install]
WantedBy=multi-user.target
```

2. Replace /path/to/your/script.sh with the actual path to your following sample Bash script:

```bash
#!/bin/bash

# check for USB storage device
if [ "$(lsblk | grep -c 'usb')" -ne 0 ]; then
    echo "USB storage device detected!"
else
    echo "No USB storage device found."
fi
```

3. Reload the systemd daemon to pick up the new service file:
```bash
sudo systemctl daemon-reload
```

4. Enable the service to start automatically at boot time:
```bash
sudo systemctl enable usb-detect.service
```

5. Start the service:
```bash
sudo systemctl start usb-detect.service
```

