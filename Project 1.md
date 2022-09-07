## Team  _'Lamborghini'_ made it!_

There was an continous error today.
We found that, joypad and rasberry pi was connected, 
but no matter what happens RC car and joypad didn't response.

Savior 'Avir' helped us.

He said that, it could be the cause of not connecting with the part corresponding to each circuit diagram in the code.
As a result of checking the youtube video, it was confirmed that even those who connected in the same way as ours were working normally.

Therefore, tomorrow, I decided to explore the method of modifying the code rather than solving the problem of the circuit connection method.



--------------------------------------------------------------------------------------------------------------------------------------------------------------

2022.09.07

![1](https://user-images.githubusercontent.com/81306023/188978782-2fbd44d1-cc72-4eab-a2fb-841dd2d4e82b.png)
Like yesterday, Joypad was well connected with RB Pi, but It didn't work with servo or motor in Jetracer.

we assume that problem was not software, but hardware.
we reassembled the jet racer, but motor still doesn't work at all.

After that, we found code from rasberrypi / config.py
which is 
```
Joystick_mode = 'xbox'
```

I've follow the guidline in jetracer wiki again.
.
![4](https://user-images.githubusercontent.com/81306023/188978874-905d92ec-5740-4c68-bc5b-d38bc846f860.PNG)
.
![5](https://user-images.githubusercontent.com/81306023/188978888-7e889309-eaf2-4043-adce-6f3481513ff4.PNG)
Or, just use the xbox gamepad in the lobby, but there was no special things.

![3](https://user-images.githubusercontent.com/81306023/188978834-728736bd-f2f7-44d2-9051-1e8b0302b4fc.png)

After that, we found that Error about 'PCA9685' which there is no driver for 'servo' 

to solve, we codded below.

![2](https://user-images.githubusercontent.com/81306023/188978818-c4ed193f-ed97-48e4-8539-7bd4284d3abe.png)
