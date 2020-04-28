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

![alt text](images\initial_screen.PNG)


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
