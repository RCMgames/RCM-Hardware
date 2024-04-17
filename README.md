# RCM-Hardware-BYTE
v2.2

UNDER DEVELOPMENT

* 1.25x1.25 inches
* 8 motors
* 8 servos
* battery monitoring
* I2C connector on QT PY
* runs on 3-11 volts

Tested with the following types of ESP32 QT Py:
| Type of Qt Py | PlatformIO name | link to Adafruit |
| ------ | -------- | -------- |
| S3 with 2MB PSRAM |  adafruit_qtpy_esp32s3_n4r2   |  https://www.adafruit.com/product/5700   |
| S3 with 8Mb Flash |  adafruit_qtpy_esp32s3_nopsram   |  https://www.adafruit.com/product/5426   |
| S2 |  adafruit_qtpy_esp32s2   |  https://www.adafruit.com/product/5325  |

Look here for how to program it: https://github.com/RCMgames/RCMv2

Look here for more information and examples of robots: https://github.com/rcmgames

Want slightly smaller with a built in IMU? Look at the [Nibble](https://github.com/RCMgames/RCM-Hardware-Nibble)

![image of computer model of the board from the top](https://github.com/RCMgames/RCM-Hardware-BYTE/blob/067e820301f93f17813f3cc500efb27105b1fbe3/pictures/render%203.jpg)
![image of computer model of the board from the bottom](https://github.com/RCMgames/RCM-Hardware-BYTE/blob/067e820301f93f17813f3cc500efb27105b1fbe3/pictures/render%202.jpg)

To get boards made, send the "gerbers rcm hardware byte v2.1.zip" "RCMhardwareByte-all.pos" and "RCMhardwareByteBOM.csv" to a company like PCBWay.

Starting in fall 2023 I started thinking about making a smaller [RCM board](https://github.com/RCMgames/RCM_hardware_documentation_and_user_guide/tree/v1/Robot%20Control%20Module/circuit%20diagram%20and%20fritzing%20design).
I wanted to find a microcontroller board that includes an esp32 chip instead of using an esp32 chip directly, in order to keep the project simpler and more likely to work – I didn’t want to have to design a circuit with an antenna.
I found the Adafruit QT Py esp32 board that’s tiny (about the size of lots of bare esp32 modules) and still has 13 GPIO pins.
That’s a large decrease from the 20 GPIO pins from the ESP32 boards used in the previous design. I didn’t want to reduce the number of motors and servos that can be connected.
The L293D h-bridge chips in the old design take a lot of pins, if I used a motor driver chip with a serial interface, I could save pins for controlling servos.
After looking at a few options I found the Trinamic TMC7300. https://www.analog.com/en/products/tmc7300.html
Each driver can control 2 motors, and up to 4 drivers can be controlled from just two pins from the QT Py.
This means the new design can control 8 motors and still have enough pins to also run 8 servos. Because 8 bits is a byte and the boards are small and bite sized I named these boards RCM BYTE.

