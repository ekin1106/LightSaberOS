# LightSaberOS
________________________________________________________________________________   

### FEATURES :

* Simple modular systems (you can choose to remove some systems from your final compilation)
* Swing detection
* Blade Clash detection  
* Wrist movement detection 
* Full gapless sound playing with "Hum Extended" soundfiles (see below)
* Blaster Shot deflect 
* Blade Lockup (long press on lockup button. Plays until release of the button)
* Accent LED
* Flash-on-Clash LEDString
* Multiple ignition/retractation/flickering effects
* Config Menu to modify some features without wiring the device to your PC/Mac 
* EEPROM load/save of your config preferences
* Soundfont adding supported (not automatic, you'll have little work to do ;) )
* Low battery level warnings
* Shutdown on critical battery level 
* Automatic Powersaving mode when idle

________________________________________________________________________________   

### WHAT YOU WILL NEED :
* [Java Runtime Environment 8](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) Download the right file for your architecture
* [Arduino Eclipse v.2016-03-11_03-29-38](http://www.baeyens.it/eclipse/download.php) Again, download the right file for your architecture
* my new DFPlayer library (Included in zip file)
* [I2Cdev and MPU6050 (Included in zip file)](https://codeload.github.com/jrowberg/i2cdevlib/zip/master) 
* [EEPROMex9.1 (Included in zip file)](http://thijs.elenbaas.net/wp-content/uploads/downloads/2013/12/EEPROMEx-9.1.zip)
* [OneButton (Included in zip file)] (https://github.com/mathertel/OneButton)
* [LinkedList (Included in zip file)] (https://github.com/ivanseidel/LinkedList)
* Wire (Included in Arduino Eclipse) 

________________________________________________________________________________   

### DEVICE CURRENTLY SUPPORTED :

Designed to be used on Arduino Nano (ATmega328 processors)

* IMU (accelerometer + gyroscope) modules :
	* MPU6050
* Soundplayer modules:
	* DFPlayer Mini
* Blade module:
	* homemade LEDstrings
	* RGB LEDs (Luxeon/Cree styled)
	* Single LED

I would be glad to see other modules added. If you're interested to make your device compatible, please contact me.
   
________________________________________________________________________________   

## SET UP YOUR PC:
1. Download and install [Java Runtime Environment 8](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)   
Download the right file for your OS   
2. Download [Arduino Eclipse v.2016-03-11_03-29-38](http://www.baeyens.it/eclipse/download.php)      
Again, download the right file for your OS   
3. Uncompress this archive inside c:\Program Files   
4. Start C:\Program Files\eclipseArduino\eclipseArduinoIDE.exe
On first start up you will be ask where to put your prject workspace.   
I advise you to put it there (off course replace "nesk" by your username) :   
![Set workspace destination](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse1.PNG)   
On first startup it will download a bunch of stuff related to Arduino Libraries.   
Wait until it finishes   
5. Go to Windows > Preferences      
6. Select Arduino and set "Build before upload ?" to "Yes" and press OK   
7. Plug in your Arduino device    
It would be best that you always use the same USB port for future use    
8. Go to File > New > Arduino sketch     
![Project Name](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse2.PNG)   
Then press next   
![Fill in your board Info](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse3.PNG)   
COM port may be different on your PC. It depends on USB port you plugged it in.   
Then press next   
![Optional Check AVaRICE](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse4.PNG)   
Here Checking AVaRICE is optional   
Then press Finish   
9. Delete LightSaberOS.ino file   

________________________________________________________________________________    

## IMPORT GITHUB FILES INSIDE ECLIPSE PROJECT:

1. Uncompress LightSaberOS-master.zip archive
2. If not already done create this directory : C:\Users\neskw\Arduino
3. Copy and Paste LightSaberOS-master\Libraries directory inside C:\Users\neskw\Arduino
4. Inside Eclipse Right click on LightSaberOS project  > Import
![Import source files](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse5.PNG)   
Then press Next  
![Select source directory](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse6.PNG)   
Then press Next   
In "Eclipse Project explorer" open the new created LightSaberOS-master and select those files :   
![Select source directory](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse7.PNG)   
Then drag and drop them to the root structure of the project   
5. Inside Eclipse Right click on LightSaberOS project  > Import
![Import Libraries](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse8.PNG)   
Then press Next 
Select those libraries :
![Select Libraries](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse9.PNG)   
Then press Finish 
6. Delete LightSaberOS-master directory from Eclipse Project explorer   
    
   
You should end up with this Project explorer structure :   
![Project structure](https://raw.githubusercontent.com/neskweek/LightSaberOS/master/README/eclipse10.PNG)   

If so, Then you're ready to rock !   

________________________________________________________________________________    
   
   
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________     
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________     

##10/03/2016 : The following my not be accurate since release of version 1.0  
##Modification of this Readme is a "work in progress"
##Thank you for your patience
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________     
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________    
________________________________________________________________________________     
## Install / Config

#### 1. IMU calibration 
 First, you'll need (if not already done) to calibrate your MPU6050.  
 [I recommend you use the AutoCalibration script you can find here](http://www.i2cdevlib.com/forums/topic/96-arduino-sketch-to-automatically-calculate-mpu6050-offsets/)  
 Note the offset values it will give you and replace those you'll find in my code : 
```c++
	/*
	 * Those offsets are specific to each MPU6050 device.
	 * they are found via calibration process.
	 * See this script http://www.i2cdevlib.com/forums/index.php?app=core&module=attach&section=attach&attach_id=27
	 */
	mpu.setXAccelOffset(-2645);
	mpu.setYAccelOffset(-5491);
	mpu.setZAccelOffset(3881);
	mpu.setXGyroOffset(27);
	mpu.setYGyroOffset(-135);
	mpu.setZGyroOffset(-38);
```

#### 2. Determine IMU orientation
 The way you physically installed the MPU6050 in your hilt will influence how swing detection works.  
 You'll have to determine which IMU's axis is parallel to blade axis and change it accordingly in the code :   
```c++
//#define BLADE_X
#define BLADE_Y
//#define BLADE_Z
```


#### 3. Prepare your SDCard
Then, put the content of SDCard.zip on your SDCard:  
Erase any directory that would be named like the ones you'll find in this archive.  
Formatting your SDCard would be even better !  

In this archive there's one soundfont example :
* 02: contains a Common Creative licensed soundfont with extended hum sound files : Barlow (Thanks to Joe Barlow)



#### 4. Check Wirings
Use of original Protonerd's wirings since 1.0RC3  
Don't forget to wire those ones which were added :  
* DFPLAYER TX to D7
* DFPLAYER SPK+ to A0
* DFPLAYER SPK- to A1     
![Schematics](http://i1073.photobucket.com/albums/w385/cest_bastien1/Lightsaber/AS2_LEDstringSaberArduino_NeskweekRevised_zpsu5k0ljck.png)    
Wiring of busy pin is optional since LightSaberOS doesn't use it.  

#### 5. Tweak your install (optionnal) 

###### A. RGB LEDs users
comment:
```c++
#define LEDSTRINGS 
``` 

###### B. Single LED users
* a) Wire your LED on pin D3
	
* b) Comment this line :
	
```c++ 
#define LEDSTRINGS 
```        
* c) Modify the following lines so all variables are set to 0 :    

```c++         
#ifdef LUXEON
		storage.mainColor = 0;
		storage.clashColor = 0;
		storage.soundFontColorPreset[2][0] = 0;
		storage.soundFontColorPreset[2][1] = 0;
		storage.soundFontColorPreset[3][0] = 0;
		storage.soundFontColorPreset[3][1] = 0;
#endif
```

###### C.Tweaks
* General tweaks :
```c++
#define CLICK				5    // ms you need to press a button to be a click
#define PRESS_ACTION		200  // ms you need to press a button to be a long press, in action mode
#define PRESS_CONFIG		400  // ms you need to press a button to be a long press, in config mode
/* MAX_BRIGHTNESS
 * Maximum output voltage to apply to LEDS
 * Default = 200 (78,4%) Max=255 Min=0(Off)
 * WARNING ! A too high value may burn your leds. Please make your maths !
 */
#define MAX_BRIGHTNESS		200
```

* To win some hex file size, or when you will want to use your saber in normal day to day use, comment this line: 
```c++
#define LS_INFO
```


#### 6. Upload the sketch to your arduino.
> ___Will only work with Arduino IDE v1.6.5 !!!___  
Arduino v1.6.7 will generate errors.

#### 7. Enjoy


## How it works :

###### _In standby mode (idle)_ :  
* Short press on main button : activate your saber
* Long press on lockup button : activate config mode


###### _In Action Mode_ :
* Long press lockup button : Lockup
* Short press lockup button : Clash
* Long press main button : shutdown saber


###### _In config Mode_ :  
* short press main button : Up the value
* short press lockup button : Down the value
* long press main button : Change menu :  
	* volume
	* soundfont 
	* swing sensitivity : adjust swing sensitivity.
	* [ONLY FOR RGB LED USERS] Main color : change the color of your saber
	* [ONLY FOR RGB LED USERS] Clash color: change the color displayed during clash effect 
	* [ONLY FOR RGB LED USERS] Assign colors to current soundfont ? : Allows you to save the colors you just defined to the selected soundfont
	* clash acceleration sensitivity : trigger clash detection algorythm. The higher the value, the less sensible it is
	* clash brake sensitivity : trigger clash sound.The higher the value, the more sensible it is
* Long press lockup button : update config to EEPROM and leave config mode


If you want to add a soundfont, create a new folder (named 004 for instance), put your soundfiles in it (__don't put gaps in numbering files__) and take a look at SoundFont.h file


## License:

This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.  
To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/]http://creativecommons.org/licenses/by-nc-sa/4.0/ .

## Notes :

1. __Only WAVs file !!!__ _NOOOO MP3, NOOOO WMA !!!_   :     
When encoding a sound to those format (MP3 and WMA) the encoder will automaticly put a silence at start.    
___WE DON'T WANT GAPS !!!___  
2. With soundfiles with hum extension (you edited a swing file and paste a hum sound repeated for some time), if you put 2 min of hum after your swing sound, if you don't move your saber for 2 min (higly unprobable in real situation) you'll notice a little gap in hum sound at that moment : You've just switch on a pure hum soundfile.
3. Don't put gaps in soundfile numbering ex.:001_Boot.wav,002.wav, 0010_Swing1.wav...    
The "folder play" command of the DFPlayer will see them as 001, 002, 003...    
That will generate unpredictable behaviour.
4. You can't put more than 255 folders numbered folder on your SDCard, including O1 (which contains config mode sounds)
5. You can't put more than 255 files in a folder on your SDCard.
6. You won't be able to have more than 65535 sound file on the wole SDCard (including config sounds).
7. Don't put names after folder number (ex.: 001_Config or 002_Sith). Your folder won't be detected (tested :( )
8. Since I've developped it on a breadboard, clash and swings settings may need some more tweaking.    
Still hopping that will not be the case  :P. I've developped those wanting to obtain "real life" saber feel.
9. Beware  the amount of debug settings you uncoment: they add significant amount of data to the compile.   
I've made them modular for this reason, so take advantage of it.

## TODO :
By priority :

* Better README.md (Work in progress)
* Find a way to remove delays function from (and induced by) DFPlayer lib.  
I think it's interferring with movements detection system (especially clash ones)
* Find a way to make hum relaunch unoticable   
_(not sure it will be possible with DFPlayer mini)_
* Try to reduce compiled hex file to be able to add  more functionnality and/or handling of more modules   
(IMU/Music players).
* Make powerOn/powerOff ledstring effect sync to soundfont soundfiles play time.
	* Add 2 time-variables to setup in soundfont.h
* Find a use to:
	* short press lockup button in standby mode 
	* double click on main button in action/config/standby mode
	* double clik on lockup button in action/config/standby mode.


## Videos
* [Quick tour (made under v1.0 RC4)] (https://youtu.be/mc8scn_qyFM)
* [Motion Detection Demo (made under v1.0 RC5)] (https://www.youtube.com/watch?v=wY8BSSEyYLY)


## Known Bug :
* In config mode, when chosing a new SoundFont, on some occasions, LSOS doesn't play the boot sound like it should... I can't find why


## Thanks

Thanks to __Protonerd__ from Arduino Forum for initiating this project.  
Thanks to __Jakesoft__ from Arduino Forum for is initial ideau of using Arduino device to build a lightsaber.  
Thanks to [__Joe Barlow__](https://www.freesound.org/people/joe93barlow/) for his excellent opensource soundfont that I did remix for our needs.  



I hope you'll like it.

Don't hesitate to reports bugs (I've made a lot of test but... hey !), or suggest new functionallity.  
If you want to contribute to this project, please contact me via mail or on the [thread of this project] (http://forum.arduino.cc/index.php?topic=361566.0)  
