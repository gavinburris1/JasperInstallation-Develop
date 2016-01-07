# Jasper-Installation-Develop
How to install Jasper with a Google STT, create modules, and many more. Let's make you a talking robot.

<h2><b>Jasper Installation (WORK IN PROCESS</b></h2>

So, you’re ready to get your own personal assistant? Follow the instructions.

<b>Steps</b>
<ul>

  <li>Download jasper_pi2.img from https://mega.nz/#!T5VHXb4A!ZFaDDAUASswYb6Fi_-opDScBWOpNqmJMWS9KgPgn2nU </li><br>

<li>Open up package and expand it. </li><br>


<li>Burn jasper_pi2.img onto SD card.</li><br>


<li>Insert SD card into Raspberry pi 2, Plug in HDMI monitor (unless you want to go through the headless method), Ethernet or WiFi dongle, and Keyboard.</li><br>

<li>Once up and going login into your pi

Default login:pi Default password:raspberry</li><br>

<li>Type in sudo raspi-config and expand file system to OS (option 1)</li><br>
</ul>

<h2> <b> Now were ready to make a profile</b> </h2>
<ul>
<li>cd /jasper/client and type in python populate.py
Enter in your credintials
When you get to the part about stt engine type in google</li>
<b>For the API -</b> 
<br>
<b>Configuring the Google STT engine</b>
<ul>
  <li>You need an Google Speech API key to use this. To obtain an API key, join the Chromium Dev group and create a project through the Google Developers console.</li><br>
<li>
Then select your project. In the sidebar, navigate to “APIs & Auth.” and activate the Speech API. Under “APIs & Auth,” navigate to “Credentials.” Create a new key for public API access.</li><br>
<li>
When you python populate.py it asks for a STT engine (default PocketSphinx) type in google.
It will then ask for an API key, copy and paste the key you got from the developers console.
</li></ul><br>
<b> Jasper should now work </b>
It will sound like Steven Hawking at first because it defaults to espeak-tts (Text to Speech)
If you want to change that read on.<br>

<b> How to change jasper's voice </b>

Install SVOX Pico
(The following is adapted from http://rpihome.blogspot.com/2015/02/installing-pico-tts.html)

Pico is a text to speech program.  Unlike some of the other TTS programs, this one does not require an internet connection and has very good quality.

To install it, pull down the source code and compile:
<ul>
1.) In terminal, type:
<li>
sudo vim /etc/apt/sources.list
And make sure these two lines are not commented (commented lines start with a # character):

deb http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free rpi
deb-src http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian/ wheezy main contrib non-free rpi
If they are missing or commented, add them and save the file.
</li><br>
2.) We need to update our packages, so in terminal type:
<li>
sudo apt-get update
</li><br>
3.) Install the following dependencies:
<li>
sudo apt-get install fakeroot debhelper automake autoconf libtool help2man libpopt-dev hardening-wrapper
</li><br>
Next, you’ll need to create a place to put the sources, again in terminal, type:
<li>
mkdir pico_build
cd pico_build
apt-get source libttspico-utils
</li><br>
4.) After downloading the source files there will be a new directory similar to svox-1.0+git20110131 (the number at the end is a date stamp and may be different than at the time of this blog post.)

Navigate to it by typing:
<li>
cd svox-1.0+git20110131
</li><br>
5.) Compile the source.  This can take up to 20 minutes.

In Terminal, type:
<li>
dpkg-buildpackage -rfakeroot -us -uc
</li><br>
There should now be four .deb packages in your pico_build folder.

In terminal type:
<li>
cd ~/pico_build/
</li><br>
The following packages should be showing:
<br>
libttspico0_1.0+git20110131-2_armhf.deb
libttspico-data_1.0+git20110131-2_all.deb
libttspico-dev_1.0+git20110131-2_armhf.deb
libttspico-utils_1.0+git20110131-2_armhf.debsudo apt-get update
6.) Install the packages in the following order:
<li>
sudo dpkg -i libttspico-data_1.0+git20110131-2_all.deb
sudo dpkg -i libttspico0_1.0+git20110131-2_armhf.deb
sudo dpkg -i libttspico-utils_1.0+git20110131-2_armhf.deb</li>
<br><li>
Reboot the Raspberry Pi by typing “reboot.”</li></ul>
<br>
