<img src="SmartSaber.ico" align="right"/>

# SmartSaber

A long time ago in a galaxy far far away, the final assignment for my Real Time Digital Signal Processing (RT-DSP) [Uni course](https://www.di.uoa.gr/en/studies/undergraduate/303) was to create a [LabVIEW](https://www.ni.com/en-us/shop/labview.html) project that would somehow -you guessed it- capture, process and *visualise* digital signals produced in real time. 

Going through the Star Wars phase at the time, the idea was to somehow animate a  ***lightsaber*** in 3D space that would mirror one's hand movements. How? Using a smartphone, by running a motion-capturing app that would send the data to a computer to get 3D-rendered. 

In 2022 I decided to revive this gem, and open-source it to share the fun! 

And here's what it looks like:

|  |  |
|--|--|
| ![](screenshots/screen1.png) | ![](screenshots/screen2.png)

*Take a look at the demo [video](videos/smaller-demo_patrec-sidebyside-rec4.mp4) too (including kick-ass sound effects! 🔊)*

The original final deliverable for the 2016 assignment can be found in the [RT-DSP Project Spec.pdf](https://github.com/LAripping/SmartSaber/files/8016090/RT-DSP.Project.Spec.pdf) doc but it's in Greek &#x1F535; so you can find most of it's content in the following sections in english &#x1F534;.

You can start practicing the Jedi tradecraft in your own dojo, by following the [step-by-step guide](#usage-instructions). 







## Features

The main feature of SmartSaber is to collect hand movement data (elevation, rotation, acceleration etc.) from the sensors on the smartphone and depict it graphically in real time, by animating a 3D model of a lightsaber.

Schematically:

![](main-feature.png)

Additionally, some extra features have been implemented:

* **Lightsaber Switch On/Off**

  by tapping the device's proximity sensor to enable / disable the light beam

* **Lightsaber Customisation**

  Allowing the user to choose their weapon, from a set of four iconic options:

  * <span style=color:blue>Luke's Training Lightsaber</span>
  * <span style=color:green>Luke's Jedi Lightsaber</span>
  * <span style=color:red>Darth Maul's Lightsaber</span>
  * <span style=color:fuchsia>Mace Windu's Lightsaber</span>

* **Pattern Recognition**

  Allowing the Jedi Master to record three lightsaber moves which the instrument will "learn". 

  Then, when the young padawan successfully replays any of them, the program will let them know they nailed it, with visual and sound effects.

  An example "triple-threat" of moves that can be loaded to the program are:   
  
  | Downward Slash                           | Overhead Block                           | Reflector Spin                           |
  | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
  | ![](initial%20resources/DownwardSlash.png) | ![](initial%20resources/OverheadBlock.png) | ![](initial%20resources/ReflectorSpin.png) |
  
  You can see this feature in action in the [demo video](videos/smaller-demo_patrec-sidebyside-rec4.mp4). 





## Usage Instructions

1. Download and Install LabVIEW from [here](https://www.ni.com/en-us/support/downloads/software-products/download.labview.html) 

   > NI offers a free 1year trial of LabVIEW's Community edition, which should be more than enough for practicing this project.

2. Clone this repo

3. Install the embedded fonts for extra coolness.

   Double-click the TTF files under `src/SmartSaber/fonts`

3. Double-click the `src/SmartSaber/SmartSaber.vi` file

   it should open in LabVIEW showing you this screen:

   ![](screenshots/launch-fonts-bg.png)

4. Click "Operate > Run" to start the program.

   This will activate the computer's BT adapters and populate the "Device Name" field to pair the smartphone, blocking execution until it's connected.

6. On the smartphone, pair it with the computer as usual through BT settings, then launch the AndroView app (ignore the VI download prompt, this project already includes it) and connect with the computer by entering the provided device name 

6. Once the lightsaber beam appears, calibrate the relative north using the UI knob while holding the device in an upright position, until the lightsaber is oriented appropriately

   ![](screenshots/relnorth-fonts-bg.png)

7. Start swinging! - ***MAY THE FORCE BE WITH YOU***
  

> Visual type? Follow along the relevant video [here](videos/smaller-intro-sidebyside-rec3.mp4)



## How it works

### LabVIEW: A whistle-stop tour

**L**aboratory **V**irtual **I**nstrument **E**ngineering **W**orkbench, in short "LabVIEW" is a platform distributed by [National Instruments](https://ni.com/) (NI) which allows engineers to develop applications for data-acquisition, instrument control, industrial automation and other purposes. It runs on Windows, Linux, macOS, and even on the [cloud](https://lumen.ni.com/nicif/US/EVALLVONLINE/content.xhtml)! and is highly extensible. 

LabVIEW apps are called Virtual Instruments (VIs) and are written in "G", a visual programming language. A VI, such as a simple Thermometer, consists of 2 basic components:

1. The **Block Diagram** where the developer "codes" the data-flow by arranging things like wires, gates and functions. For our thermometer app, it would look like this: 

   ![](screenshots/thermometer-bd.png)

   > Looks easy? Take a look at the block diagram of the SmartSaber VI, consisting of 13 custom subVIs. You'll find it [here](exports/justBlockDiagram/SmartSaberd.png). 

2. The **Front Panel** where the end-user interacts with the final "instrument" using things like dials, knobs, switches and text input fields. For our simple thermometer, it looks something like this:

   ![](screenshots/thermometer-fp.png)



### SmartSaber Components

On a high level, our project consists of the following components:

* A **smartphone**, collecting sensor data and transmitting to the computer over Bluetooth using the AndroView **app**

* A computer running the VI in **LabVIEW**, receiving the data in real time and rendering the animated lightsaber

  

In detail, here's what was used for a working setup, both originally and for the 2022 reboot 

| Smartphone (2016) - LG Google Nexus 5                        | Computer (2016) - HP Pavilion dv7 2030ev |
| ------------------------------------------------------------ | ---------------------------------------- |
| OS: Android 6.0 "Marshmallow"                                | OS: Windows XP (32-bit)                  |
| Bluetooth: 4.0                                               | Bluetooth: 4.0                           |
| WiFi: 802.11 a/b/g/n/ac                                      | WiFi: 802.11 b/g                         |
| USB port: micro 2.0                                          | CPU: Intel Core 2 Duo 2.40 GHz           |
| Sensors: InvenSense MPU 6515 / Parallax QTI / Avago APDS 9930 | Memory: 2 GB                             |
| "AndroView Free" version 2.4.1, downloaded from [Play Store](https://play.google.com/store/apps/details?id=com.heightdev.androviewbluetooth) <sup>1</sup> | Graphics Card: AMD Radeon HD 4650        |
| "Sensor Network for LabVIEW" version 1.1.2, downloaded from [Play Store](https://play.google.com/store/apps/details?id=com.heightdev.androviewbluetooth) <sup>1</sup> | LabVIEW version: 8.5                     |

>  <sup>1</sup> Application no longer available



| Smartphone (2022) - Google Pixel 2                           | Computer (2022) - Dell Precision M4600        |
| ------------------------------------------------------------ | --------------------------------------------- |
| OS: Android 11.0 "Red Velvet Cake"                           | OS: Windows 10 Pro (64-bit)                   |
| Bluetooth: 5.0                                               | Bluetooth: 4.0                                |
| WiFi: 802.11 a/b/g/n/ac                                      | WiFi: 802.11n                                 |
| USB port: micro 3.1, Type-C                                  | CPU: Intel Core i7 2.80 GHz                   |
| Sensors: OEM Accelerometer / Compass / Gyroscope / Proximity | Memory: 16 GB                                 |
| "AndroView Free" version 2.4.1, downloaded from [ApkPure](https://m.apkpure.com/androview-free-labview-vi/com.heightdev.androviewbluetooth/versions) | Graphics Card: AMD FirePro M5950 Mobility Pro |
|                                                              | LabVIEW version: 21.0                         |



### Notes on the Internals

The SmartSaber LabVIEW project (`src/SmartSaber/`) is structured as follows:

* Main VI, the project's entry-point: `SmartSaber.vi` : 

* Supporting VIs
  * `subVIs/`
  * `subVIs/sensors/` 
  * `globals/`
  
* Audiovisual FX Resources
  * `images/`
  * `sfx/`
  * `fonts/`
  
* Pattern Recognition data:

  > The following directories are the locations where the waveforms and data streams for each recorded move are saved on runtime, and are thus not maintained. 
  >
  > Although the program is shipped with actual data populated in those places, it is  probably impossible to imitate them since every wrist and smartphone is different. Instead, the user is encouraged to record their own moves and then try to match them.

  * The raw data streams (`patterns/`)

  * The resulting charts for these sequences (`waveforms/`)

    


The VI's code revolves around 2 loops:

1. **The Main Loop:**

   ...responsible for signal processing and 3D rendering. The AndroView mobile application continuously captures sensor data and encodes them in a byte stream, which is sent to the computer over Bluetooth on regular intervals. The stream has the following format:

   `...yXXz`**`aXXbXXcXXdXX...wXXxXXyXXz`**`aXXb...`

   Each lowercase letter matches to a sensor and the XX part following (of varying length) holds the respective value read, according to this matrix: 

   | a       | b       | c       | ...  | f     | g     | h     | ...  | o         | p        | q      | r      | s      | ...  |
   | ------- | ------- | ------- | ---- | ----- | ----- | ----- | ---- | --------- | -------- | ------ | ------ | ------ | ---- |
   | accel_x | accel_y | accel_z |      | ori_x | ori_y | ori_z |      | prox_dist | prox_max | gyro_x | gyro_y | gyro_z |      |

   This project only leverages the following sensors:

   * Orientation vector
   * Level Data
   * Gyroscopes
   * Accelerometers
   * Proximity Sensors

   > Ellipsis (...) values are of no interest to our project and involves other irrelevant sensors such as the thermometer, magnet, pressure-sensor etc.   

   The motion sensor data-stream received is also continuously plotted in the Front Panel in scrolling charts for all X, Y and Z axes.

   ![](screenshots/charts-fonts-bg.png)

   The main loop is also responsible for detecting the recorded patterns,  by continuously checking the received byte stream of a fixed time window, and comparing it point-to-point with all three recorded waveforms (tolerant to a certain error margin)

2. **The Event-Handling Loop**

   This is purely responsible for the UI buttons corresponding to the move record feature, which allow the user to save their motion of a certain time window.   

The program can be fully stopped through the "Operate > Stop" button in the LabVIEW menus. When the Bluetooth connection with the device is lost the program doesn't fully stop but the processing loop is ceased, lighting the blue "Auto-stop" indicator. 

![](screenshots/autostop-bg.png)



## Future Work

> Both original TODOs envisioned from 2016 and fresh ones from the 2022 reboot.

- [ ] Replace that horrible, 8bit-looking icon 

- [x] Change 3D Background to a picture of the galaxy far far Away

  Maybe need to do this [programmatically](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z000000kHejSAE&l=en-GR)? 

  From the failed exe/installer attempts it appears we don't need to do this programmatically and the BG is saved within the project

- [x] ~~Auto-install fonts ("Star Jedi")~~

  Since we can't build working executable / installer, we'll just ask the user politely to install them first

- [ ] Investigate if it's possible to use "LabVIEW Online" to quick-demo the project

- [ ] Lightsaber handle decals, not just beam ones

- [ ] Code our own Android app?

- [x] ~~Create Installer and EXE app to abstract LabVIEW details.~~

  Tried and failed with unsatisfied reference errors, giving up, too much effort

