# arduino-due-qt-creator
## Qt template wizard for Arduino Due
Templates wizards (XML-based, porting to the new JSON format in progress)  for creating C++ Qt projects targeting the [Arduino DUE board](https://www.arduino.cc/en/Guide/ArduinoDue) (based on an ARM CortexM3 ATSAM3X8E controller) using the Qt Creator.
Wizards for both bare metal and [FreeRTOS](https://github.com/greiman) [^FreeRTOSv].
The templates are based on the [QBS](https://github.com/qbs/qbs).

Setup instructions:

*  install [Arduino IDE](https://www.arduino.cc/en/Main/Software) with support Arduino DUE [^ArduVersion]
*  install Qt Creator [^QtVersion]
*  connect your Arduino board in the Programming port [^ProgPort]
*  copy the templates folders in this repository (`arduino_arm_with_qbs` and `arduino_arm_free_rtos_with_qbs`) in: `(path-to-qt)/Contents/Resources/templates/wizards`

If you work with FreeRTOS, download the FreeRTOS port for Arduino DUE and copy dir `FreeRTOS-ARM` in `(usr)/Documents/Arduino/libraries`.

Then:

*  Copy (or move) contents `(home-dir)/.arduino15/packages/arduino/hardware/sam/1.6.4/` in `(path-to-arduino)/hardware/arduino/sam`

* Copy (or move) contents `(home-dir)/.arduino15/packages/arduino/tools/` in `(path-to-arduino)/hardware/tools`

After that run QtCreator, choose **New File or Project**. You should see in the **Projects** list a new **Arduino ARM** templates category. Click on it and select the **Project Location**. Presso on **Continue**.

Insert the **Project Parameters**:

*  Board: *Arduino DUE*
*  Microcontroller: *ATSAM3X8E*
*  Libraries:  
*  Arduino Path: 
*  Serial port: *for example `/dev/ttyACM0`*






Delete (or rename) file main.cpp in the folder `(path-to-arduino)/hardware/arduino/sam/cores/arduino/`

This templates containts blink project.

Press "Run" for generate %yourProjectName%.bin file.

If You will send the .bin file to the Arduino DUE, write into the Qt project *install settings* the command `stty -F %Your-Arduino-port% cs8 1200 hupcl` and write to Qt progect run settings `(path-to-arduino)/hardware/tools/bossac/1.3a-arduino/bossac -U false -e -w -v -b %yourProjectName%.bin -R`

This templates make with using github/pauldreik/arduino-due-makefile project and github/cleitonsouza01/qt-creator-arduino project

[^FreeRTOSv]: Tested wtith FreeRTOS **8.2.3**
[^ArduVersion]: Tested with Arduino IDE **1.8.5**
[^QtVersion]: Tested with Qt Creator **4.5.0** based on Qt **5.10.0**
[^ProgPort]: if you used *Native* port instead, you need to clear the Arduino board status, resetting your device manually
