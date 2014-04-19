# RTIMULib-Arduino - a versatile 9-dof IMU library for the Arduino

RTIMULib is the simplest way to connect a 9-dof IMU to an Arduino and obtain full fused quaternion or Euler angle pose data. Basically, two simple function calls (IMUInit() and IMURead()) are pretty much all that's need to integrate RTIMULib-Arduino.

Check out www.richards-tech.com for more details, updates and news.

## Release history

### Current

#### Initial test code

This version supports only the MPU-9150. Support for STM chips coming soon.

The fusion filter is RTFusionRTQF.

Two sketches are included. ArduinoMagCal can be used to store magnetometer calibration data. Load the sketch and waggle the IMU around, making sure all axes reach their minima and maxima. The display will stop updating when this occurs. Then, enter 's' followed by enter into the IDE serial monitor to save the data.

ArduinoIMU is the main demo program. It configures the MPU-9150 based on settings in RTSettings.cpp. Change these to alter any of the parameters. By default, it runs at 50 gyro and accel samples per second. The display is updated only 5 times per second regardless of IMU sample rate.

Note that the gyro bias is being calculated during the first 5 seconds. If the IMU is moved during this period, the bias calculation may be incorrect and the code will need to be restarted.
