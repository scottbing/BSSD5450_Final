# BSSD5450 Ambient Computing
### Final Project

<p>Originally the project was intended to demonstrate a home lighting IOT system. It was to involve the control of home lighting from a python application. In an effort to keep costs to a minimum, a simple white BLE bulb was chosen.  Two light bulbs were selected, a Magic Smart Bulb and a Phillips Hue White Blanco Model A19. The Magic Smart Bulb did not offer a public API.  The Phillips organization, on the other hand, not only exposes their API, but they also encourage hobbyists to develop lighting implementations.  Phillips provides a lighting SDK and coordinates a developer's interest group.<p>   
https://developers.meethue.com/develop/get-started-2


## Getting Started

The final project consists of two python programs
```
phillips_bulb.py - Phillips Hue Light
speak_bulb.py    - SenseHat Simulation
```
### Reverse Engineering
Reverse engineering a smart device involves using diagnostic tracing and capture facilities that trap commands and data streams over the network.  This is the process that was used for the execution of this project.  The [Nordic nRF Connect](https://play.google.com/store/apps/details?id=no.nordicsemi.android.mcp) application was an invaluable tool.  It allows for the capture of Bluetooth and WiFi transmissions.  It was used to determine the applicable manufactures' commands.  The Bluetooth technology is based upon a GATT server protocol.  The GATT server protocol is composed of characteristics.  These characteristics define the operation that occurs against the lighting devices.  These operations include read, write, and property toggle.  Once the syntax of the commands was determined,  they could be inserted into scripts and programs.
<p>A second backup project was developed using the Raspberry Pi Sense Hat facility.  The intention was to develop a similar project where the lights would be simulated on a sense hat device instead of a hub.  Light on, light off, light dim, light brighten, and light color change functions ar simulated on this project.</p> 



My final project controls a Phillips Hue Smart Light bulb with a python application.  In order to figure out what Bluetooth commands to send to the device, I had to use a utility that exposed the light bulb's GATT.  I used the Nordic Master Console application to accomplish this.  This is a no-cost application that can be freely downloaded and installed on a smartphone ora tablet.  With this application, I was able to connect to the light bulb and view its internal GATT structure.  
The application opens with the device discovery screen.   Upon the first visit to the application, the scan function must be initiated. This is a one=time operation. When the application is opened again, a scan will b automatically performed so any new devices will be discovered. This scan discovers any Bluetooth devices within a fifty-meter range.  This is the standard range of a Bluetooth 4.x device.
After discovering the devices, this is the screen that appears.  It shows all of the discovered devices.  If the device is connectable, it will also display a Connect button. 

![alt text](/assets/images/initial_screen.jpg)

The Hue bulb is displayed at the bottom of the screen.  This is the screen that appears when the Connect Button is chosen
![alt text](/assets/images/detail_screen.PNG)

This screen contains a list of Services. The services that have the 16-bit UUIDs, the Generic Attribute, Generic Access, Device Information are all standard.  They are defined by the Bluetooth SIG's RFP.  The UUID's are documented here. The 128-bit Unknown Characteristics are manufacture custom UUIDs. Note that they are all defined as Primary services.  The next screen appears when one of these Services is selected. 
![alt text](/assets/images/characteristics.PNG)

This screen shows the individual characteristics belonging to the selected service. 
So armed with this information, the application Wireshark was used to capture the exact commands that were issued to change the state of the light bulb. This particular light bulb has three settings, dim light, bright light, and night light. Using the smartphone app that accompanies the light bulb continually dimmed the lights several times.
Then I captured the trace information from my phone.  My phone is an Amsunge (s Android phone.  This phone contains a Bluetooth log called hci_btsnoop.log.  Unfortunately, my phone does not have an SDCard.  So I had to enable the Bluetooth HCI Snoop Log. And then select Tale a Bug Report.  This is the way it must be done if the phone does not have an SDCard.  If the phone has an SDCard, the hci_bootnoop.log can simply be found and downloaded from the SDCard.emulated.0 directory. Android provides a python program called bstnooz.py that can be used to extract the hci_btsnoop.log from the Bug Report.  The btsnooz.log can simply be opened in Wireshark. 
![alt text](/assets/images/wireshark.PNG)

I matched this data against the data reported on the nrfConnect, and I was able to determine the code for dim the lights.





### Prerequisites

Required Materials

```
Raspberry Pi 3
Phillips Hue Light Bulb (any Model)
phillips_bulb.py script
```

### Installing
```
## Software required **
Raspian Operating System
Python Interpreter Compiler
Bluetooth software - bluez
Gatt software - gatlib
```

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Mak esure light bulb is turned on

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
