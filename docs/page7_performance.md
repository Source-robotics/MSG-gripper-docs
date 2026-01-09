# **Performance and tests**

These tests represent termal performance of the MSG gripper under different conditions. The default value for termal error is 75 degrees.

!!! Note annotate "Errors" 
    If you built SSG48 gripper by yourself and did not place thermistor in the motor coils you risk destroying your gripper during normal operation.

## **Performance over multiple days**

* Testing: cycle open and close every 2.5s
* No load present; current/torque applied is near 0
* Continous testing for 7 days
* Motor temperature: 42
* Ambient temperature:  33 

## **Max constant current over some time**

* Testing: Hold object
* Max current setpoint: 300mA
* Tested for 24h
* Stable motor temperature during testing: 62 degree
* Ambient temperature:  33 

## **Max current to trigger termal error**

* Testing: Hold object
* Max current setpoint: 1600mA
* Time to trigger termal error under 1600mA load: 4 min
* Ambient temperature:  33 