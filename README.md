# arduino-due-qt-creator
## Qt template wizard for Arduino Due
Templates wizards (XML-based, porting to the new JSON formt in progress)  for creating C++ Qt projects targeting the [Arduino DUE board](https://www.arduino.cc/en/Guide/ArduinoDue) (on ARM CortexM3 ATSAM3X8E controller based) with using the Qt Creator.
Wizards for both bare metal and FreeRTOS.
The templates are based on the [QBS](https://github.com/qbs/qbs).

Setup instructions:

*  install Arduino IDE with support Arduino DUE
*  install Qt Creator
*  connect your Arduino board in the Programming port (if you use Native port you needed clear and reset your device manually)
*  copy this templates in (path-to-qt)/Tools/QtCreator/share/qtcreator/templates/wizards/

If you work with FreeRTOS, download port FreeRTOS for Arduino DUE and copy dir FreeRTOS-ARM in (path-to-arduino)/libraries

Copy(or move) contents (home-dir)/.arduino15/packages/arduino/hardware/sam/1.6.4/ in (path-to-arduino)/hardware/arduino/sam

Copy(or move) contents (home-dir)/.arduino15/packages/arduino/tools/ in (path-to-arduino)/hardware/tools

After that run QtCreator, choose newFile>ARM

Delete(or rename) file main.cpp in the folder (path-to-arduino)/hardware/arduino/sam/cores/arduino/

Choose string with needed configuration and press Choose

After that write the path whith Arduino IDE, Arduino libraries and Arduino port (for example "/dev/ttyACM0")

This templates containts blink project.

Press "Run" for generate %yourProjectName%.bin file.

If You will send .bin file to Arduino DUE, write to Qt progect install settings command "stty -F %Your-Arduino-port% cs8 1200 hupcl" and write to Qt progect run settings (path-to-arduino)/hardware/tools/bossac/1.3a-arduino/bossac -U false -e -w -v -b %yourProjectName%.bin -R

This templates make with using github/pauldreik/arduino-due-makefile project and github/cleitonsouza01/qt-creator-arduino project

Tested in Arduino IDE 1.6.4 with Qt Creator 3.3.1
