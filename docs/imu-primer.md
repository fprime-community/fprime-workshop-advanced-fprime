# IMU Primer

This document serves as a primer for working with the **MPU-6050 Inertial Measurement Unit (IMU)**. It is *not* intended to replace the official datasheet, but rather to help engineers quickly understand key concepts and the basic initialization flow.

## IMU Basics

The **MPU-6050** is a **6-degree-of-freedom (6-DoF)** IMU that combines:

* A **3-axis accelerometer**
* A **3-axis gyroscope**
* An integrated **temperature sensor**

It communicates over the **I²C** bus (7-bit device address `0x68` by default, or `0x69` if AD0 is pulled high).

## IMU Data Flow

A typical MPU-6050 startup and configuration sequence is as follows:

1. **Reset the device**

   * Write `0x80` to the **Power Management 1 (PWR_MGMT_1, 0x6B)** register to initiate a full reset.
   * Wait briefly, then read back `PWR_MGMT_1` until the reset bit clears.

2. **Wake up the IMU**
   * Clear the sleep bit (bit 6) in **PWR_MGMT_1** to enable the sensor.

3. **Configure measurement ranges**

   * **Accelerometer**: write desired range to **ACCEL_CONFIG (0x1C)**

     * ±2 g → `0x00`
     * ±4 g → `0x08`
     * ±8 g → `0x10`
     * ±16 g → `0x18`
   * **Gyroscope**: write desired range to **GYRO_CONFIG (0x1B)**

     * ±250 °/s → `0x00`
     * ±500 °/s → `0x08`
     * ±1000 °/s → `0x10`
     * ±2000 °/s → `0x18`

4. **Read sensor data**

   * Accelerometer data: registers **0x3B–0x40**
   * Temperature data: registers **0x41–0x42**
   * Gyroscope data: registers **0x43–0x48**

## Notes and Tips

* All sensor outputs are **16-bit signed integers** in big-endian format.
* Temperature output can be converted to °C using:

  ```
  Temp (°C) = (raw_temp / 340) + 36.53
  ```

## References

* [MPU-6000/6050 Register Map](https://cdn.sparkfun.com/datasheets/Sensors/Accelerometers/RM-MPU-6000A.pdf)
* [MPU-6000/6050 Product Datasheet](https://cdn.sparkfun.com/datasheets/Components/General%20IC/PS-MPU-6000A.pdf)
