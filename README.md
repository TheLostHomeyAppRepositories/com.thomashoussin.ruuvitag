# RuuviTag

Adds support for RuuviTag Bluetooth Sensor

## About RuuviTag
RuuviTag is an advanced open-source sensor beacon platform designed to fulfill the needs of business customers, developers, makers, students, and can even be used in your home and as part of your personal endeavours. See https://ruuvi.com/ fore more information. 

## RuuviTag driver
This apps allows integration of RuuviTag and Ruuvitag Pro (RAWv1 and RAWv2 format) in Homey, allowing to monitor :
- Temperature
- Humidity
- Pressure
- Acceleration
- Battery
- RSSI
- Movement (RAWv2 only)
- Entering/leaving range : it can be used as a BLE beacon, triggering an event when the device enters or leaves the range. The number of attempts scan can be configured per device in device settings.

Scan duration (how long homey listens for BLE advertisment) and polling interval (how long between two scans) can be configured in app settings.

## Ruuvi gateway
This apps allows integration of RuuviTag Gateway in Homey. You need first to activate API-key (bearer token) in Ruuvi Gateway ; see https://docs.ruuvi.com/gw-examples/polling-mode for more information. After that Homey will poll the latest data with timestamps from the gateway. 
Gateway IP adress should be auto-detected ; you need to enter the bearer token in the next screen, and then choose Ruuvitag to add in Homey. 

The driver offers the same capabilities as the Ruuvitag driver. Polling interval can be setup for each device independently. 

If you want to use several Ruuvi gateway, you should plug only one at a time during setup.

## Ruuvi API (removed in latest version)
The app also allows Homey to act as a Ruuvi Station gateway. 
- Before v0.2 : You have to allow public access in the app settings (default is private) ; 
- In v0.2 : gateway is public by default ; due to changes in SDKv3, access is public and cannot be changed. 

Then in Ruuvi Station, in gateway settings, use : 
- http://<your_ip>/api/app/com.thomashoussin.ruuvitag for local access only
- https://<cloudid>.connect.athom.com/api/app/com.thomashoussin.ruuvitag (cloudId can be found on http://developer.athom.com/tools/system)

Device must have been locally added in Homey ; after that, data received through API updates Ruuvitag device (if device is unknown, data is discarded). Presence is not modified when receiving data through gateway. 

## Donations
Feel free to donate to  support the project !
[<img src="https://www.paypalobjects.com/en_GB/i/btn/btn_donate_SM.gif">](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=RVBS24SPLU922&currency_code=EUR)

# Version History
###  v0.3.5
    - Detects if hostname ends with .local in gateway autodiscovery
###  v0.3.4
    - Typo in import
###  v0.3.3
    - Bugfixes in gateway
###  v0.3.2
    - Code factoring
###  v0.3.1
    - First version with gateway support (WIP), ruuvipro improvments, trigger fix
### v0.3.0
	- Test version for cloud support 
### v0.2.1
	- Improve memory usage 
### v0.2
	- Update to SDKv3 
### v0.1.1
	- Bug fix, updated y18n
### v0.1.0
	- Add reset in sequence number detection : low bat warning. This adds alarm_battery capability for Ruuvitag in RAWv2 format and a maintenance action to reset alarm
### v0.0.6
	- Add preference to show / hide notification messages
### v0.0.5 
	- Add API for Ruuvi Station gateway
### v0.0.4
	- Fixed pressure unit, updated trigger title
### v0.0.3
	- Add triggers when RuuviTag enters/leaves,  fixed bug with acceleratio with RAWv1
### v0.0.2
	- Add app settings, acceleration capability, icons
### v0.0.1
	- Initial version