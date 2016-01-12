# Jasper-Installation-Develop
How to install Jasper with a Google STT, create modules, and many more. Let's make you a talking robot.

<h2><b>Jasper Installation (WORK IN PROCESS)</b></h2>

So, you’re ready to get your own personal assistant? Follow the instructions.

<b>Steps</b>
<ul>

  <li>Download jasper_pi2.img from https://mega.nz/#!T5VHXb4A!ZFaDDAUASswYb6Fi_-opDScBWOpNqmJMWS9KgPgn2nU </li><br>

<li>Open up package and expand it. </li><br>


<li>Burn jasper_pi2.img onto SD card.</li><br>


<li>Insert SD card into Raspberry pi 2, Plug in HDMI monitor (unless you want to go through the headless method), Ethernet or WiFi dongle, and Keyboard.</li><br><br>

<li>Once up and going login into your pi

Default login:pi Default password:raspberry</li><br><br>

<li>Type in </li><br><li><i> sudo raspi-config</i></li><br> and expand file system to OS (option 1)</li><br>
</ul>

<h2> <b> Now were ready to make a profile</b> </h2>
<ul>
<li><i>cd /jasper/client</i> <br><li>and type in</li><br><li><i> python populate.py</i></li><br>
Enter in your credintials
</li>
<br><br>
<b>Configuring the Google STT engine</b>
<ul>
  <li>You need an Google Speech API key to use this. To obtain an API key, join the Chromium Dev group and create a project through the Google Developers console.</li><br><br>
<li>
Create a project and name it JasperSTT, move into project JasperSTT and click "Enable APIs'", Search for Speech API and enable it. Now make some creditals (credintals tab found in left column) and copy the API key </li><br><br>
<li>
When you python populate.py it asks for a STT engine (default PocketSphinx) type in google.
It will then ask for an API key, copy and paste the key you got from the developers console.
</li></ul><br><br>
<b> Jasper should now work </b>
It will sound like Steven Hawking at first because it defaults to espeak-tts (Text to Speech) <br>
If you want to change that read on.<br>

<b> How to change jasper's voice </b>

Install SVOX Pico
(The following is adapted from http://rpihome.blogspot.com/2015/02/installing-pico-tts.html)
<br><br>
Pico is a text to speech program.  Unlike some of the other TTS programs, this one does not require an internet connection and has very good quality.
<br><br>
To install it, pull down the source code and compile: <br>
<ul>
1.) In terminal, type:
<li>
<center>sudo vim /etc/apt/sources.list</center> <br>
And make sure these two lines are not commented (commented lines start with a # character):<br><br><hr>
<br>
deb http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free rpi <br>
deb-src http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian/ wheezy main contrib non-free rpi <br>
<hr>
If they are missing or commented, add them and save the file. <br>
</li><br><br>
2.) We need to update our packages, so in terminal type:
<hr><li><br><br>
<center>sudo apt-get update</center>
</li><br><br><hr>
3.) Install the following dependencies:
<hr><li><br><br>
<center>sudo apt-get install fakeroot debhelper automake autoconf libtool help2man libpopt-dev hardening-wrapper<center>
</li><br><br><hr>
Next, you’ll need to create a place to put the sources, again in terminal, type:
<hr><li>
<center>mkdir pico_build
cd pico_build
apt-get source libttspico-utils</center>
</li><br><br><hr><br>
4.) After downloading the source files there will be a new directory similar to svox-1.0+git20110131 <br><br><br>

Navigate to it by typing:<br><br>
<hr><li>
<center>cd svox-1.0+git20110131<center>
</li><hr><br><br>
5.) Compile the source.  This can take up to 20 minutes.<br>

In Terminal, type:
<hr><li><br><br>
<center>dpkg-buildpackage -rfakeroot -us -uc </center>
</li><hr><br><br>
There should now be four .deb packages in your pico_build folder.<br><br>

In terminal type:
<hr><li><br><br>
<center>cd ~/pico_build/ </center>
</li><hr><br><br>
The following packages should be showing:
<br><hr>
libttspico0_1.0+git20110131-2_armhf.deb<br>
libttspico-data_1.0+git20110131-2_all.deb<br>
libttspico-dev_1.0+git20110131-2_armhf.deb<br>
libttspico-utils_1.0+git20110131-2_armhf.deb<hr>
<br><hr><li>sudo apt-get update</li><hr><br>
6.) Install the packages in the following order:
<hr><li><br><br>
<center> sudo dpkg -i libttspico-data_1.0+git20110131-2_all.deb<br>
sudo dpkg -i libttspico0_1.0+git20110131-2_armhf.deb<br>
sudo dpkg -i libttspico-utils_1.0+git20110131-2_armhf.deb<br></center></li><hr>
<br><li>
<li>
<center>
cd ~/.jasper/profile.yml</center> </li><br><br>
<li> Add in under the stt engine </li><br>
<li> <center>tts_engine: pico-tts</center>
</li><br><br>
<b>Reboot the Raspberry Pi by typing “reboot.”</b></li></ul>
<br>
