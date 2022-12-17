# Meshtastic simple How-To

- https://meshtastic.org/docs/getting-started

## how to install

- Load new FW via **meshtastic flasher GUI** to some folder
- go to unpacked firmware folder and install FW `.\device-install.bat -f firmware-tlora-v2-1-1.6-2.0.7.91ff7b9.bin`

## configure with BLE

- install python-cli (https://meshtastic.org/docs/software/python/cli)
- configure basic settings:
	- `meshtastic --set lora.region EU_868`
	- `meshtastic --set network.wifi_enabled false`
	- `meshtastic --set bluetooth.enabled true`
	- `meshtastic --set bluetooth.mode FIXED_PIN`
	- `meshtastic --set bluetooth.fixed_pin 1234`
	- `meshtastic --set device.role CLIENT`

## enable WiFi (and disable BLE)

- `meshtastic --set network.wifi_enabled true`
- `meshtastic --set bluetooth.enabled false`
- `meshtastic --set network.wifi_ssid your_ssid`
- `meshtastic --set network.wifi_psk your_wifi_password`

## enable debug

- `meshtastic --set device.debug_log_enabled true`
- `meshtastic --set device.serial_enabled true`

## special HAM version 433MHz (no encryption with callsign)

- `meshtastic --set lora.region EU_433`
- `meshtastic --set-ham AB1CDE`

## import/export config

- export config `meshtastic --export-config > example_868_config.yaml`
- import config `meshtastic --configure example_config.yaml`

## use specific port

- append `--port COMx` to cli parameters

## web client

- for BT and Serial (chromium-based browsers only) https://client.meshtastic.org
- for wifi http://meshtastic.local 
- general info https://meshtastic.org/docs/software/web-client

## full configuration

- https://meshtastic.org/docs/settings/config/
