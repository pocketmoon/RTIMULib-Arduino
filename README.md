# RTIMULib-Arduino - a versatile 9-dof IMU library for the Arduino

RTIMULib is the simplest way to connect a 9-dof IMU to an Arduino and obtain full fused quaternion or Euler angle pose data.

Check out www.richards-tech.com for more details, updates and news.

## Release history

### September 26 2014 - 2.1.0

Added a new sketch - ArduinoAccel. This shows how to subtract a rotated gravity vector using quaternions
in order to obtain the residual accelerations. It's basically used in exactly the same way as ArduinoIMU but
displays the residual accelerations instead. Note that there's no accel calibration at the moment so there 
will be some residual accelerations indicated that aren't real. Also, as usual (!), it's essential to perform
magnetometer calibration or else results will be useless.

### September 26 2014 - 2.0.0

There have been significant changes in this version (V2) to reduce the memory footprint. Instead of the previous
autodetection system, the IMU and address is now selected using a #define in RTIMULibDefs.h in the libraries
subdirectory. By default it looks like this:

	#define MPU9150_68                      // MPU9150 at address 0x68
	//#define MPU9150_69                      // MPU9150 at address 0x69
	//#define LSM9DS0_6a                      // LSM9DS0 at address 0x6a
	//#define LSM9DS0_6b                      // LSM9DS0 at address 0x6b

Change the commenting as required to select the device and address. All other functionality has remained the same. V1 is still available via the GitHub repo release tab.

### May 5 2014 - 1.0.0

Fixed bug in MPU-9150 compass initialization - changed incorrect writeBytes to readBytes to get fuse ROM data.

### April 22 2014 - 0.9.0

#### First release

This version supports the InvenSense MPU-9150 and STM LSM9DS0 single chip IMUs. The fusion filter is RTFusionRTQF.

(Pre-V2 only) The software will automatically discover the IMU type in use and also the address being used. This can be overridden in RTIMUSettings.cpp if desired.

Two sketches are included. ArduinoMagCal can be used to store magnetometer calibration data. Load the sketch and waggle the IMU around, making sure all axes reach their minima and maxima. The display will stop updating when this occurs. Then, enter 's' followed by enter into the IDE serial monitor to save the data.

ArduinoIMU is the main demo program. It configures the IMU based on settings in RTIMUSettings.cpp. Change these to alter any of the parameters. By default, it runs at 50 (MPU-9150) or 95 (LSM9DS0) gyro and accel samples per second. The display is updated only 3 times per second regardless of IMU sample rate.

Note that the gyro bias is being calculated during the first 5 seconds. If the IMU is moved during this period, the bias calculation may be incorrect and the code will need to be restarted.
