## Team  _'Lamborghini'_ made it!_

First, Assemble our piracer with wiki guide.

<img src="https://user-images.githubusercontent.com/81483791/188978196-0c487b01-6736-46ed-85b9-2523e3f3639a.png"  width="500" height="300"/>

Second, Install Raspberry pi imager to program in to the SD card.

Insert SD card in the laptop, and execute Raspberry pi imager.
   
<img src="https://user-images.githubusercontent.com/81483791/188979960-53b5cfd6-bd87-42ee-a382-2fe20cc5a659.png"  width="400" height="200"/>
- Choose operating system.
<img src="https://user-images.githubusercontent.com/81483791/188980652-91443fb2-d10d-45b6-9a14-1ca0fe84e210.png"  width="400" height="200"/>
- Choose storage (our SD card)
<img src="https://user-images.githubusercontent.com/81483791/188980909-5347dffc-f018-4355-adef-6498aea1b3d0.png"  width="400" height="200"/>
- Choose advanced options to use SSH, Wifi
<img src="https://user-images.githubusercontent.com/81483791/188980846-23f2c5a4-dada-4551-a28d-3f662efbe534.png"  width="400" height="200"/>

(we can use VNC viewer to SSH)

- Set id, passward for using SSH
<img src="https://user-images.githubusercontent.com/81483791/188980846-23f2c5a4-dada-4551-a28d-3f662efbe534.png"  width="400" height="200"/>
- Connect Wifi
<img src="https://user-images.githubusercontent.com/81483791/188981071-cb382ede-25f8-4fe2-8da4-6c35cb3cccdd.png)"  width="400" height="200"/>
- Choose Wireless LAN country : DE (Germany)
<img src="https://user-images.githubusercontent.com/81483791/188981256-8ebe1f13-6f3c-4c61-bbc0-2515abd12a57.png"  width="400" height="200"/>
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
<img src="https://user-images.githubusercontent.com/81483791/188981372-11d40a39-0d69-45a7-a3dd-e10887918754.png"  width="400" height="200"/>   
- Fill IP address & choose SSH.
<img src="https://user-images.githubusercontent.com/81483791/188981476-e44bca19-8750-4200-a799-ccce8a42eb4d.png"  width="400" height="200"/>
- Change fonts server:fixed → Ubuntu mono.
<img src="https://user-images.githubusercontent.com/81483791/188981617-56ff8db4-d28e-4f6d-96ef-1bae3741f3e8.png"  width="400" height="200"/>
- Login raspberry pi (we set id, passward for using SSH before).
<img src="https://user-images.githubusercontent.com/81483791/188982070-ff022595-18c6-4a7a-8090-12c4f5ec2d60.png"  width="400" height="200"/>
- Execute VNC viewer.

We got this error "The connection was refused by the host computer”

It can be solved VNC → Enable (for using VNC viewer).

1. WEB control

For WEB control to Donkeycar, we have to change interface options.

`sudo raspi-config`
<img src="https://user-images.githubusercontent.com/81483791/188982658-c4d246f0-c232-4fcd-b4d5-585ee1f20e8a.png"  width="400" height="200"/>
<img src="https://user-images.githubusercontent.com/81483791/188982723-51f834f4-b2db-4736-a63a-034f4f7b6e4e.png"  width="400" height="200"/>
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
