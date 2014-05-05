# RTIMULib-Arduino - a versatile 9-dof IMU library for the Arduino

RTIMULib is the simplest way to connect a 9-dof IMU to an Arduino and obtain full fused quaternion or Euler angle pose data.

Check out www.richards-tech.com for more details, updates and news.

## Release history

### May 5 2014

Fixed bug in MPU-9150 compass initialization - changed incorrect writeBytes to readBytes to get fuse ROM data.

### April 22 2014 - 0.9.0

#### First release

This version supports the InvenSense MPU-9150 and STM LSM9DS0 single chip IMUs. The fusion filter is RTFusionRTQF.

The software will automatically discover the IMU type in use and also the address being used. This can be overridden in RTIMUSettings.cpp if desired.

Two sketches are included. ArduinoMagCal can be used to store magnetometer calibration data. Load the sketch and waggle the IMU around, making sure all axes reach their minima and maxima. The display will stop updating when this occurs. Then, enter 's' followed by enter into the IDE serial monitor to save the data.

ArduinoIMU is the main demo program. It configures the IMU based on settings in RTIMUSettings.cpp. Change these to alter any of the parameters. By default, it runs at 50 (MPU-9150) or 95 (LSM9DS0) gyro and accel samples per second. The display is updated only 3 times per second regardless of IMU sample rate.

Note that the gyro bias is being calculated during the first 5 seconds. If the IMU is moved during this period, the bias calculation may be incorrect and the code will need to be restarted.
