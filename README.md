# Modified the MPU9250 firmware to adapt to the SlimeVR Tracker firmware for ESP of the MPU6500/6050 + QMC5883L sensor solution!

If you need to use other sensors, please use [the official repository](https://github.com/SlimeVR/SlimeVR-Tracker-ESP) directly to get the latest version.

## Configuration

Firmware configuration is located in the `defines.h` file, just use MPU9250. For more information on how to configure your firmware, refer to the [Configuring the firmware project section of SlimeVR documentation](https://docs.slimevr.dev/firmware/configuring-project.html).

## Compatibility

The following IMUs and their corresponding `IMU` values are supported by the firmware:
* MPU6500/6050 + QMC5883L (IMU_MPU9250)
  * A more cost-effective solution, due to the use of a magnetometer, the sustainable use time will be greatly extended..  
  However, you still need to be careful not to buy inferior MPU sensors. Please test whether the data of each axis is accurate before completely welding (a more effective way to check is to rotate 90° in each direction. Once the deviation exceeds 3°, the sensor will not be able to work on the sensor. Full body tracking will not provide a good experience, it is recommended to return and exchange directly)

Firmware can work with both ESP8266 and ESP32. Please edit `defines.h` and set your pinout properly according to how you connected the IMU.

## Sensor calibration

*It is generally recommended to turn trackers on and let them lay down on a flat surface for a few seconds.** This will calibrate them better.

**Some trackers require special calibration steps on startup:**
* MPU-9250, BMI160
  * Turn them on with chip facing down. Flip up and put on a surface for a couple of seconds, the LED will light up.
  * After a few blinks, the LED will light up again
  * Slowly rotate the tracker in an 8-motion facing different directions for about 30 seconds, while LED is blinking
  * LED will turn off when calibration is complete
  * You don't have to calibrate next time you power it off, calibration values will be saved for the next use

## Infos about ESP32-C3 with direct connection to USB

The ESP32-C3 has two ways to connect the serial port. One is directly via the onboard USB CDC or via the onboard UART.
When the chip is connected to the USB CDC, the serial port shows as `USB Serial Port` in Device Manager. The SlimeVR server will currently not connect to this port.
If you want to set your WiFi credentials, you can use the PlatformIO serial console.
There you have to enter the following: `SET WIFI "SSID" "PASSWORD"`

## Uploading On Linux

Follow the instructions in this link [PlatformIO](https://docs.platformio.org/en/latest//faq.html#platformio-udev-rules), this should solve any permission denied errors

## Contributions

By contributing to this project you are placing all your code under MIT or less restricting licenses, and you certify that the code you have used is compatible with those licenses or is authored by you. If you're doing so on your work time, you certify that your employer is okay with this.

For an explanation on how to contribute, see [`CONTRIBUTING.md`](CONTRIBUTING.md)
