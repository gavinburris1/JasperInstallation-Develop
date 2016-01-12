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

<li>Type in </li><br><li><i> sudo raspi-config</i></li><br> and expand file system to OS (option 1)</li><br>
</ul>

<h2> <b> Now were ready to make a profile</b> </h2>
<ul>
<li><i>cd /jasper/client</i> <br><li>and type in</li><br><li><i> python populate.py</i></li><br>
Enter in your credintials
</li>
<br>
<b>Configuring the Google STT engine</b>
<ul>
  <li>You need an Google Speech API key to use this. To obtain an API key, join the Chromium Dev group and create a project through the Google Developers console.</li><br>
<li>
Create a project and name it JasperSTT, move into project JasperSTT and click "Enable APIs'", Search for Speech API and enable it. Now make some creditals (credintals tab found in left column) and copy the API key </li><br>
<li>
When you python populate.py it asks for a STT engine (default PocketSphinx) type in google.
It will then ask for an API key, copy and paste the key you got from the developers console.
</li></ul><br>
<b> Jasper should now work </b>
It will sound like Steven Hawking at first because it defaults to espeak-tts (Text to Speech) <br>
If you want to change that read on.<br>

<b> How to change jasper's voice </b>

Install SVOX Pico
(The following is adapted from http://rpihome.blogspot.com/2015/02/installing-pico-tts.html)
<br>
Pico is a text to speech program.  Unlike some of the other TTS programs, this one does not require an internet connection and has very good quality.
<br>
To install it, pull down the source code and compile: <br>
<ul>
1.) In terminal, type:
<li>
<center>sudo vim /etc/apt/sources.list</center> <br>
And make sure these two lines are not commented (commented lines start with a # character):
<br>
deb http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free rpi
deb-src http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian/ wheezy main contrib non-free rpi
If they are missing or commented, add them and save the file.
</li><br>
2.) We need to update our packages, so in terminal type:
<li>
<center>sudo apt-get update</center>
</li><br>
3.) Install the following dependencies:
<li>
<center>sudo apt-get install fakeroot debhelper automake autoconf libtool help2man libpopt-dev hardening-wrapper<center>
</li><br>
Next, you’ll need to create a place to put the sources, again in terminal, type:
<li>
<center>mkdir pico_build
cd pico_build
apt-get source libttspico-utils</center>
</li><br>
4.) After downloading the source files there will be a new directory similar to svox-1.0+git20110131 (the number at the end is a date stamp and may be different than at the time of this blog post.)

Navigate to it by typing:
<li>
<center>cd svox-1.0+git20110131<center>
</li><br>
5.) Compile the source.  This can take up to 20 minutes.

In Terminal, type:
<li>
<center>dpkg-buildpackage -rfakeroot -us -uc </center>
</li><br>
There should now be four .deb packages in your pico_build folder.

In terminal type:
<li>
<center> cd ~/pico_build/ </center>
</li><br>
The following packages should be showing:
<br>
libttspico0_1.0+git20110131-2_armhf.deb
libttspico-data_1.0+git20110131-2_all.deb
libttspico-dev_1.0+git20110131-2_armhf.deb
libttspico-utils_1.0+git20110131-2_armhf.debsudo apt-get update
6.) Install the packages in the following order:
<li>
<center>sudo dpkg -i libttspico-data_1.0+git20110131-2_all.deb
sudo dpkg -i libttspico0_1.0+git20110131-2_armhf.deb
sudo dpkg -i libttspico-utils_1.0+git20110131-2_armhf.deb</center></li>
<br><li>
<li>
<center>
cd ~/.jasper/profile.yml</center> </li><br>
<li> Add in under the stt engine </li>
<li> <center>tts_engine: pico-tts</center>
</li><br>
<b>Reboot the Raspberry Pi by typing “reboot.”</b></li></ul>
<br>
