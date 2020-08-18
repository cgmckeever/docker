# docker

## esp-wifi-repeater

- ` docker build -t esp-sdk -f Dockerfile.18.04.esp_sdk .`

- `docker images; read -p "ImageID: " id; docker run --rm --name esp-sdk -ti $id /bin/bash`

-   `rm -rf /tmp/repeater/; mkdir -p /tmp/repeater/; \
docker cp esp-sdk:/esp/esp_wifi_repeater/firmware/0x00000.bin /tmp/repeater/; \
docker cp esp-sdk:/esp/esp_wifi_repeater/firmware/0x02000.bin /tmp/repeater/ `

- `esptool.py erase_flash`

- `esptool.py --port /dev/tty.usbserial-1420 write_flash -fs 4MB -ff 80m -fm dio 0x00000 /tmp/repeater/0x00000.bin 0x02000 /tmp/repeater/0x02000.bin`

- `esptool.py --port /dev/tty.usbserial-1420 write_flash -fs 4MB -ff 80m -fm dio 0x00000 firmware/0x00000.bin 0x02000 firmware/0x02000.bin`



set ssid ToscheStation2e
set password
set ap_ssid FBI-12
set ap_password 123456789

set nat 1
portmap add TCP 8080 196.168.4.2 80
portmap add TCP 2020 196.168.4.3 80