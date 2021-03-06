[ ![pulse](http://cdn.shopify.com/s/files/1/0100/6632/products/PulseSensorAmpedFinger-web_2_large.jpg?14)](http://patriciogonzalezvivo.com/2013/ofxpulsesensor/ )

OpenFramework addon to read that from [PulseSensor](http://pulsesensor.myshopify.com/) develop by [Joel Murphy](http://www.joelmurphy.net/) and [Yury Gitman](http://www.mybeatingheart.com/yury/).

This addon helps you get the heartbeat (BPM and IBI) and use it in your openFrameworks project using the GPIO's of your RaspberryPi or by using an Arduino to send the signal by Serial connection.

<iframe src="http://player.vimeo.com/video/77236762" width="575" height="359" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe> 

# Installing
Clone [this addon repository](https://github.com/patriciogonzalezvivo/ofxPulseSensor) into your `openFrameworks/addons` folder:

	cd openFrameworks/addons
	git clone https://github.com/patriciogonzalezvivo/ofxPulseSensor

# Setting Up

**On you computer through an Arduino**
Using Arduino as Server and your laptop (tested on OSX) as a client:

1. Flash your Arduino with this [firmware](http://pulse-sensor.googlecode.com/files/PulseSensorAmped_Arduino_1dot1.zip)
2. Connect the Arduino by USB to this computer and the PulseSensor to the arduino following this [guide](http://pulse-sensor.googlecode.com/files/PulseSensorAmpedGettingStartedGuide.pdf) or this [video](https://vimeo.com/58657081)
3. Add this addon to your program (see arduino-example) and compile

**In the RaspberryPi through the GPIOs**:

![photo](https://raw.github.com/andreasmuller/RaspberryPiWorkshop/master/wiringPiPotentiometerExample/wiringPiPotentiometerExampleSPI_bb.jpg)

1. RaspberryPi don't have analog-in like Arduino. That's why we are going to use [**MCP3008**](https://www.adafruit.com/products/856) to transform the resistance of the photocell into pulse frequency. Maybe you also want to by the [Pi Cobbler breakout](http://www.adafruit.com/products/914) to make the connections easier.

2. Everything is almost like [this tutorial](http://learn.adafruit.com/send-raspberry-pi-data-to-cosm) except that we are not using ```#23```, ```#24``` and ```#25``` instead we are using SPI just like [Jason Van Cleave](https://github.com/jvcleave) and [Andreas Muller](https://github.com/andreasmuller) did in [this example](https://github.com/andreasmuller/RaspberryPiWorkshop/tree/master/wiringPiPotentiometerExample). Off course instead of using a potentiometer the PulseSensor.

3. Configure your RaspberryPi for wiringPi ( https://github.com/openFrameworks-RaspberryPi/openFrameworks/wiki/Raspberry-Pi-Using-the-GPIO-pins-with-Wiring-Pi-and-openFrameworks ).

	sudo nano /etc/modprobe.d/raspi-blacklist.conf

Comment with # (or remove) those lines

	sudo reboot
	
4. Add ofxPulseSensor to your addons.make file, compile and run as root. (Attention! Because the wiringPi the App need to be run in super user mode or sudo )

	make
	sudo make run

More References about Analog Inputs in RaspberryPi:

* <http://learn.adafruit.com/reading-a-analog-in-and-controlling-audio-volume-with-the-raspberry-pi/connecting-the-cobbler-to-a-mcp3008>
* <http://raspberrypihobbyist.blogspot.com/2012/12/analog-interface.html>

![01](http://patriciogonzalezvivo.com/2013/ofxpulsesensor/01.jpg)
![02](http://patriciogonzalezvivo.com/2013/ofxpulsesensor/02.jpg)
![03](http://patriciogonzalezvivo.com/2013/ofxpulsesensor/03.jpg)

