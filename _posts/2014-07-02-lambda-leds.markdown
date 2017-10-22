---
layout: post
title:  "Java 8 Lambdas and LEDs"
date:   2014-07-02 19:37:56 +1100
categories: article
---



Why settle for embedded programming when the Raspberry Pi brings the full power of JavaSE into the embedded world.

Settup Pi according to taste, for me the base setup from scratch is:

    Expand FS, SSH on, password change, host-name change (raspi-config).

Setup avahi/zeroconf

    sudo apt-get install avahi-daemon
    sudo insserv avahi-daemon
    (I had to "apt-get remove wolfram-engine" here on model A)
    sudo wget -O /etc/avahi/services/multiple.service puzzleduck.org/DevAdventures/multiple.service
    sudo /etc/init.d/avahi-daemon
    sudo reboot

Any sane operating system made in the last decade should know about ssh, so were good to go (I hear on windows "bonjour" and "putty" setup is required).

Now we can ssh into the pi as long as we are on the same network:

    ssh pi@<pi-hostname>.local

Now we need to install Wiring Pi and Pi4J.

    git clone git://git.drogon.net/wiringPi
    cd wiringPi
    ./build
    cd ..

    mkdir Pi4J
    cd Pi4J
    wget http://pi4j.googlecode.com/files/pi4j-0.0.5.deb
    sudo dpkg -i pi4j-0.0.5.deb


Following here is the talk as I intend to give it at the Melbourne JUG:

good evening everyone, tonight I'll be going through how to make your own LED strip and a couple of other handy hardware mods to make working on the raspberry pi with a breadboard a little bit easier for us. and we've got a few live demos for things to go wrong too, so hang in there.

the real basics shopping list for knocking up some cool home made LED circuits I'd reccomend in this order are heatshrink, header pins, LEDs, and resistors... thats right header pins and heatshrink and header pins are more important than the LEDs at least if you want something that looks great and is easy to use. Don't worry about wire, like I did, as you've already got tons of it locked up in ide cables and atx power supplies, and we'll start cutting them up shortly. Usually the ribbon cable looks better and takes less space than cutting your own wires.

to hook up all our GPIO & 3v pins we can utilise an old ide ribbon cable and a row of header pins to create a home made raspberry cobbler, just trim out the unused wires (or leave them in, it won't hurt), that's really all there is to that one, solder pins to wires and your good to go. one important piece of advice on making your own cobbler is to test and label the wires before soldering so you get the orderings and groupings correct, and then remember to leave the labels on, or you'll regret it later like me. The other plugs on the IDE cable can be used as 'micro breadboards' or power rails by solering each side of the strip together.

now we'll take care of the power supply. using an old atx power supply, a breadboard and a handfull of header pins we can get reliable 3-12 volt supplies on our prototyping area, I'm taking my 3 volt supply from the pi and the 5 and 12 volts come from the atx power supply. One of the cables on the atx supply will be header pin friendly, this is the venerable old floppy disk drive power supply, with this and a set of four header pins and two sets of two we can power the rails of our breadboard. The only other wire we'll need to know about today is the green one on the main ATX connector, this is the 'power switch' for the main output voltages and turns on the power supply when shorted to ground, so here I've added a switch to allow us to power off the pi and accompanying test circuit without having to unplug anything, but it's just as easy to short the green wire to ground with a loose bit of wire like I'm doing now and like I did for about a year.

Now just with another 2 header pins and half an old usb cable (you know the ones with unreliable data connections, they're great for this) we get reliable 5v supply for the pi and an easy to work with stand alone pi and prototype area, just ignore the green and white wires, the pi does not read data fom this port.

for testing and just good practice I recommend making an led strip and/or equivalent button panel or d-a-c. starting with three or four units, making sure it works then go for the bigger version. the last thing you want is to do a big project without realizing a simple flaw in your initial circuit that would have shown up in a smaller test circuit on a breadboard or small soldered demo. often I'll "sketch out a circuit" on a breadboard and leave it connected and running while I solder together a set of two to eight of them, or in this case 17.

for our LED strip again I'd recommend breadboard friendly header pins, and other than that we just need resistors and LEDs for the Lambda LED project, it's a nice simple one. So lest start with resistor selection, I'm no expert here but neither are a lot of the people on the internet. I recomend just searching for LED resistor calculators there's plenty out there, some with handy info like 'what is my voltage drop on a cheap standard LED likely to be'. Also handy to understand is that these values are quite flexible, the is no simple linear formula but for example I had a circuit where I wanted the LEDs extra bright and I wasn't concerned with the lifespan of the LEDs, but they were only lit about one eighth of the time and I dropped the resistance to about a third of the recommended value and running that circuit for over a couple of months resulted in no dead LEDs. If you take into consideration what your doing with it.

So first we'll solder the resistors onto the header pins, then cover up to the resistors with heat shrink, this helps make sure they don't short and adds a bit of rigidity ... another bonus is hiding any bodgy work we've done solering. Unfortunatly heat-shrink can also make fixing any serious error difficult and/or messy, so if in doubt test before shrink wrapping.

then we bend all the earth wires on the LEDs to 90 degrees and trim the positive (or in reverse if you want to sink current rather than source it, usually you want to source) and then solder them to the tops of the resistors being careful to point all the earths wires in the same direction. then bend the earths 90 degrees about a centimeter away from the LEDs into a neat row, it'd probably be ok to trim them back to make a thinner ground plane, there's not many amps running around this one, I was being way over cautious. then solder the end of that strip too a wire with a pin. Quite a simple hardware project even us software geeks can get right once in a while. My first four 8xLEDs were a 50% success rate for having one dead LED.

Now we've done the hardware, we're up to the part we're really interested in, the software. Now we will log into a terminal using ssh.

we'll need to install wiring/pi4j to access gpio pins in java, I'll assume we've covered that last month, but we'll also install java 8 to access the juicy new features, unfortunately they are ones we've already covered at the group so we don't get to cross any more topics off our list, maybe I'll try to flash LEDs with annotations during compilation once I get this settled.

Finally we get to Install Java 8... We need to download the arm java8 release from the JavaSE 8 download page, it's a bit of a moving terget at the moment and you might want the latest version.

    unzip to the /opt directory

then we can simply move into a working project directory and compile and run java8 programs with /opt/java8/bin/javac and the associated java command for running. There are also options for overtaking the default java and javac commands and there are links on how to do that on the online version

So heres a few I've prepared earlier...

the first version we'll run here uses a stream and lambda expression to run the sequence forward and an iterative sequence to go backward. The next five loops use two seperate streams and I'm actually happy with that althought I was aiming for something more like the infinate sequence. I'm using a make file here we'll have a look at if we get time a bit later, for now just take my word that it's magical pixie dust that works every time.

so we see it running almost identically in both cases, kind of boring but a nice contrast of functional and iterative styles. So I also wanted to be able to test these things when I didn't have the hardware avaliable so the next demo demonstrates the ascii version and the power of the display abstraction. Idealy I'd like to now extend this to accomodate leds on shift registers or i2c interfaces.

So now if we have time we'll have a look at the make file and the scheduled version. This version uses cron to run a background task every 2 minutes. using the capabilities of Linux running on the raspberry pi we can also setup cron jobs for any task we want triggered on a regular basis as long as our timing requirements aren't more frequent than one a minute or more accurate than about ten seconds. In a very informal test the most variation I've noticed was about six seconds after the minute the event would trigger, two or three was the norm. So here the LED chaser runs every two minutes.

Unfortunatly I kept getting this nagging feeling that something was wrong and it wasn't untill I was trying to explain the significance of the code to my Dad that it finally clicked. So I'm trying to think of an example of why functional programing might be usefull in a way that relates to this circuit. So I think "It means it's easier to verify the correctness of the program", no that's not going to impress anyone, how about "It means I'm using all that logic stuff I did at uni", no that's not going to impress Dad. and so I stumble into "It's good for distribuited computation so if this was driven by four seperate CPUs or cores then it should still work" ... "that is" ... "if it's written correctly".

Well, that got me thinking and after a bit of head scratching I realised I could test this using the paralell stream. Want to see what happens? All we are doing here is replacing the stream() function with parallel stream.

Anyway we can use forEachOrdered to fix that back up but thats really chickening out... I'm currently thinking about doing something along the lines of a TimerTask to trigger the pulses rather than a delay, but if anyone has any ideas about the functional way to trigger sequenced events I'm all ears, otherwise I'm all answers if anyone has any questions.

This is all online at puzzleduck.org under the Java Development Adventures section if you ever want to go back and check something.

Demonstration code avaliable at Google Code: https://code.google.com/p/lambda-leds/source/browse/

To compile (if using a pc, projects 4 & 5 will run, you do however need the pi4j libraries installed):

    make

To run:

    make run

To run every 2 minutes:

    make runSchedule


Other usefull long term resources:

Also a good resourse: (http://www.adafruit.com/blog/2014/03/28/how-to-install-oracle-jdk-8-on-raspberry-pi-piday-raspberrypi-raspberry_pi/)
