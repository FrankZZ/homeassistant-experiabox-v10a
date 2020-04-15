# homeassistant-experiaboxv10a
ExperiaBox V10A custom device_tracker component for Home-Assistant.io

## Purpose
The purpose of this custom component for [Home-Assistant](https://home-assistant.io) is to track devices that are connected either wired or wirelessly to a Experia Box V10A, including clients connected to the guest network.

## Inspired by
This project was inspired by the nmap device_tracker component and the custom components that allows [Home-Assistant](https://home-assistant.io) to track devices connected to the Experia Box V8 and Experia Box V10:

- [Official Home-Assistant nmap device_tracker](https://www.home-assistant.io/components/nmap_tracker/)
- [Experia V8 device_tracker](https://community.home-assistant.io/t/device-tracker-for-arcadyan-vgv7519-router-experia-box-v8/29362) by [MvdB](https://community.home-assistant.io/u/mvdb)
- [Experia V10 device_tracker](https://github.com/kadima-tech/experia-v10-device-tracker) by [kadima-tech](https://github.com/kadima-tech/)

## Setup instructions
### Copying into custom_components folder
Create a directory `custom_components` in your Home-Assistant configuration directory.
Copy the whole [experiaboxv10a](./experiaboxv10a) folder from this project into the newly created directory `custom_components`.

The result of your copy action(s) should yield a directory structure like so:

```
.homeassistant/
|-- custom_components/
|   |-- experiaboxv10a/
|       |-- __init__.py
|       |-- device_tracker.py
|       |-- manifest.json
```

### Enabling the custom_component
In order to enable this custom device_tracker component, add this code snippet to your Home-Assistant `configuration.yaml` file:

```yaml
device_tracker:
  - platform: experiaboxv10a
    host: mijnmodem.kpn
    username: admin
    password: PASSWORD
```

Please use [secrets](https://www.home-assistant.io/docs/configuration/secrets/) within Home-Assistant to store sensitive data like IPs, usernames and passwords.

## Experia Wifi
This device_tracker queries the Experia Box V10A directly.
If you are using an Experia Wifi access point in conjunction with your Experia Box V10A, the clients connected to the Experia Wifi access point will also be reported by this device_tracker.

## Troubleshooting
I have observed that sometimes the Experiabox V10A times out on the `GET /cgi/cgi_clients.js` call. What I did to work around this problem is rebooting the Experiabox V10A. 
