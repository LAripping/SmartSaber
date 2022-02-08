*A LabVIEW project that lets you swing a 3D lightsaber using only your smartphone*



<video controls="controls" style="display:block; margin:auto; height:30em">
  <source src="https://github.com/LAripping/SmartSaber/raw/master/videos/smaller-demo_patrec-sidebyside-rec4.mp4" type="video/mp4">
</video>





# Setup Instructions

1. Download and Install [LabVIEW](https://www.ni.com/en-us/support/downloads/software-products/download.labview.html) 

2. Clone the [SmartSaber code](https://github.com/laripping/smartsaber)

3. Install the [fonts](https://github.com/LAripping/SmartSaber/tree/master/src/SmartSaber/fonts)

4. Run the [main VI](https://github.com/LAripping/SmartSaber/tree/master/src/SmartSaber/SmartSaber.vi)

5. Pair your smartphone and LabVIEW computer using Bluetooth and install the [AndroView app](https://m.apkpure.com/androview-free-labview-vi/com.heightdev.androviewbluetooth)

6. Calibrate the relative north to channel the Force and...

7. Start swinging

`May the force be with you`






# Features 

### Lightsaber Customisation

Choose your weapon, from a set of four iconic options:

  * <span style="color:blue">Luke's Training Lightsaber</span>
  * <span style="color:green">Luke's Jedi Lightsaber</span>
  * <span style="color:red">Darth Maul's Lightsaber</span>
  * <span style="color:fuchsia">Mace Windu's Lightsaber</span>

### Attack Training

The Jedi Master first records three lightsaber moves and saves the waveforms using the UI buttons.
Then, when the young padawan successfully replays any of these moves, SmartSaber will let them know through the relevant indicator **and** play a cool sound effect

An example "triple-threat" of moves that can be loaded to the program are:   
  
| Downward Slash                           | Overhead Block                           | Reflector Spin                           |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| <img src="https://github.com/LAripping/SmartSaber/raw/master/initial%20resources/DownwardSlash.png"/> | <img src="https://github.com/LAripping/SmartSaber/raw/master/initial%20resources/OverheadBlock.png"/> | <img src="https://github.com/LAripping/SmartSaber/raw/master/initial%20resources/ReflectorSpin.png"/>|

> This feature is actually demonstrated near the end of the video above





### Proximity Activation

Tap your smartphone's proximity sensor to enable / disable the light beam <sup>1</sup>




* * *
  
# More Info

Experiencing issues? Bedazzled and seeking more info? Wanna hack this even cooler?? 
You'll find everything you desire in the project's repo by clicking the "View on GitHub" button on top


<sup>1</sup> Might not work as intended in modern smartphones
