## Team  _'Lamborghini'_ made it!_

First, Assemble our piracer with wiki guide.
![스크린샷 2022-09-08 오전 5 59 45](https://user-images.githubusercontent.com/81483791/188978196-0c487b01-6736-46ed-85b9-2523e3f3639a.png)
<img src="https://user-images.githubusercontent.com/81483791/188978196-0c487b01-6736-46ed-85b9-2523e3f3639a.png  width="200" height="400"/>

Second, Install Raspberry pi imager to program in to the SD card.

Insert SD card in the laptop, and execute Raspberry pi imager.

- Choose operating system.
- Choose storage (our SD card)
- Choose advanced options to use SSH, Wifi

(we can use VNC viewer to SSH)

- Set id, passward for using SSH
- Connect Wifi
- Choose Wireless LAN country : DE (Germany)
- Write

Third, setup workspace with wiki guide.

Follow guide of Donkeycar.

1. Setup Raspberry pi

We have problem installing libraries for OpenCV 

We can’t install `libqtgui4 libqt4-test`

Because we got this error message.

**E: Package 'libqtgui4' has no installation candidate**

**E: Unable to locate package libqt4-test**

Also, we have problem installing tensorflow.

For this reason, We did install the other version. (tensorflow-1.9.0)

`pip3 install --upgrade [https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.9.0-py3-none-any.whl](https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.9.0-py3-none-any.whl)`

1. VNC viewer

If we want to use raspberry pi, we needed a moniter.

Each team can’t get one moniter so we connect VNC viewer.

- Download VNC viewer.
- Install putty

sudo apt install putty

putty —version

- Execute putty client.
- Fill IP address & choose SSH.
- Change fonts server:fixed → Ubuntu mono.
- Login raspberry pi (we set id, passward for using SSH before).
- Execute VNC viewer.

We got this error "The connection was refused by the host computer”

It can be solved VNC → Enable (for using VNC viewer).

1. WEB control

For WEB control to Donkeycar, we have to change interface options.

`sudo raspi-config`

- Legacy Camera  → Enable
- SSH → Enable
- VNC → Enable (for using VNC viewer)

If you have picamera error, change Legacy Camera → enable .

But we also have other problem to using Donkeycar.

For solve this problem, I tried next things.

- Change Adafruit_GPIO script.

one workaround is edit this file:

/usr/local/lib/python3.9/dist-packages/Adafruit_GPIO/Platform.py

Search:

elif match.group(1) == '**BCM2835**':

replace it with:

elif match.group(1) == '**BCM2711**':

- uninstall Adafruit_GPIO & re install Adafruit_GPIO

`sudo pip3 uninstall Adafruit-PureIO
sudo pip3 install Adafruit-PureIO`

But we can’t solve this problem.

And also we can connect web control **https://<our raspberry pi ip>:8887**
