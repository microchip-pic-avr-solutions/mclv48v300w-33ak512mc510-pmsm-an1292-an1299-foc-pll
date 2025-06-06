# mclv48v300w-33ak512mc510-pmsm-an1292-an1299-foc-pll v1.0.0
### Release Highlights
This is the first version of code for sensorless field oriented control of PMSM using PLL estimator and Single-Shunt Current Reconstruction Algorithm on MCLV-48V-300W board[(EV18H47A)](https://www.microchip.com/en-us/development-tool/ev18h47a) with dsPIC33AK512MC510 MC DIM[(EV67N21A)](https://www.microchip.com/en-us/development-tool/ev67n21a). 

The code is set up for running the following motors,
- Hurst300 Motor(DMA0204024B101 - [AC300022](https://www.microchip.com/en-us/development-tool/AC300022)) (by default)
- Hurst075 Motor(DMB0224C10002 - [AC300020](https://www.microchip.com/en-us/development-tool/AC300020))
- Leadshine Servo Motor [(ELVM6020V24FH-B25-HD)](https://www.leadshine.com/product-detail/ELVM6020V24FH-B25-HD.html)

All the motors are tested under no load conditions. To achieve optimal performance under loaded conditions, the control parameters in the firmware may need additional tuning.

### Features Added\Updated
- Code flow is managed by State Machines to allow seamless integration of load-specific algorithms and application-specific communication interfaces
- Supports Dual-Shunt(phase shunts) and Single-Shunt(bus shunt) current measurement schemes
- Integrates two variants of flux weakening,
    1. PI controller based on voltage circle limit (less dependent on motor parameters)
    2. Reference speed feed-forward control based on PMSM steady state equations(Id reference is computed from motor parameters); can be used when motor parameters are accurately known
- DC bus voltage compensation
- Assigned functions of push buttons and potentiometer in the firmware:
	1. Push Button #1(SW1) starts and stops motor. The Speed of the motor can be controlled using potentiometer(POT) in its entire speed range. Please note that the motor operates in the flux-weakening region beyond its nominal speed.
	2. Push Button #2(SW2) changes the direction of rotation
- Supports forward and reverse rotation of motor
- Improved start-up and closed loop transition
- Over Current Fault
	1. Software limit on the phase current
	2. DC Bus current protection using dsPIC® features such as PWM PCI, comparator and DAC
