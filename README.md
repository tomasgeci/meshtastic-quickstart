# Meshtastic simple How-To

- https://meshtastic.org/docs/getting-started

## which frequency to use - based on region and regulations

### disclaimer

- please keep in mind that not each frequency is generally available for you - use of improper frequency can be a violation of law in your country
- please check your local regulations before start - usage of frequency spectrum is strictly regulated by local authorities
- check frequencies allowed for LoRa in your region (https://www.thethingsnetwork.org/docs/lorawan/frequencies-by-country/)
- please don't use EU_433 (433MHz) as a default option - it has some regulations and default module configuration does not fullfill those rules
- holders of HAM-radio licence can use EU_433 in IARU region R1 - see HAM-only section of this document

### recommended frequency in EU

- EU_868 (868MHz) in most of European Union countries
- check your country on the list (https://www.thethingsnetwork.org/docs/lorawan/frequencies-by-country/)

### antennas

- you **can't use** a high gain antenna to transmitt - default board radio settings and antenna with gain over 2.15dBi (for example simple dipole) will violate allowed ERP/EIRP
- only +16dBm EIRP is allowed in EU_868 (https://www.thethingsnetwork.org/docs/lorawan/regional-parameters/#eu863-870-maximum-eirp--erp)
- it is recommended to use original small `stock` antenna delivered with module
- in case of EU_433 and HAM-radio - consider your local permissions in 433MHz band acording to your HAM-radio license

## how to install

- load new firmware via **web installer** (https://flasher.meshtastic.org/)
- load new FW via **Meshtastic Flasher GUI** (https://meshtastic.org/docs/getting-started/flashing-firmware/esp32/python-flasher)
- or *install via CLI*
	- download firmware file from https://github.com/meshtastic/firmware/releases and unpack `firmware*.zip` or use **Meshtastic Flasher GUI** to download firmware files
	- go to unpacked firmware folder and install firmware (change `bin` file according to your board and version) `.\device-install.bat -f firmware-tlora-v2-1-1.6-2.0.7.91ff7b9.bin` (tested on Windows 10)

## configure with BLE (for EU 868MHz version)

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

## special HAM-only version 433MHz (no encryption allowed with callsign required)

- **this frequency is allowed to use only with HAM-radio licence**
- `meshtastic --set lora.region EU_433`
- `meshtastic --set-ham AB1CDE` where `AB1CDE` is your HAM-radio callsign

## import/export config

- export config `meshtastic --export-config > example_868_config.yaml`
- import config `meshtastic --configure example_868_config.yaml`

## use specific port

- append `--port COMx` to cli parameters

## web client

- for BT and Serial (chromium-based browsers only) https://client.meshtastic.org
- for wifi http://meshtastic.local 
- general info https://meshtastic.org/docs/software/web-client

## full configuration

- https://meshtastic.org/docs/settings/config/
