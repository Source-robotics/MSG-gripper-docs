# **About the gripper**


<p align="left"> <img src="../assets/GRIP_CVR.png" alt="drawing" width="5000"/> <br /> </p>  

MSG  electric gripper is a gripper based on **STEPFOC stepper drivers**. It is a gripper capable of controlling its gripping force, making it perfect for assembly tasks and human-robot collaboration. Gripping force can be adjusted allowing you to grasp a wide range of items; from delicate and soft to rigid and sturdy.<br /> 

STL and STEP files are **open source** allowing you to add a custom griping tool and attach it to any robotic arm or robot. 

SSG-48 adaptive electric gripper is available as a fully assembled gripper or you can build your own by following assembly manual.

The gripper has a single actuator for opening  both of its jaws. A system works like rack and pinion where motor is a pinion and jaws are on rack.


If you plan to build SSG-48 adaptive electric gripper by yourself you will need to source all the parts from [this BOM](https://github.com/PCrnjak/SSG-48-adaptive-electric-gripper/tree/main/BOM).<br />
After that you can follow the [assembly manual](https://github.com/PCrnjak/SSG-48-adaptive-electric-gripper/tree/main/Assembly%20manual) to assemble your gripper.


## **General specs:**

* Power supply: 24V
* Idle power: 0.5W
* Weight: 400 g
* Maximum gripping force: 80N
* Minimum gripping force: 5N
* Operating temperature -5 to 65 deg
* Communication interface: CAN bus
* CAN baud rate: 1Mbit
* Material: PETG plastic
* Stroke: 0 - 48 mm


## **Gripper stroke**

<p align="left"> <img src="../assets/gripper_stroke.png" alt="drawing" width="650"/> <br /> </p> 


## **Grasps**

Gripper can perform 2 types of graps:

* External grasp – Used to hold objects by applying pressure from the outside.
* Internal grasp - Allows you to grasp hollow objects by applying pressure from the inside.

## **Pinout and connection**
<p align="left"> <img src="../assets/GRPCON.png" alt="drawing" width="650"/> <br /> </p> 

The gripper is powered and controlled with single cable that carries CAN bus communication and 24V power supply.

!!! Tip annotate "Voltages" 
    To power the gripper you need to use 24V. <br />
    You can send commands to the gripper using **5V** CAN bus. 


## **Dimensions**


<p align="left"> <img src="../assets/DIM2.PNG" alt="drawing" width="700"/> <br /> </p> | 
<p align="left"> <img src="../assets/DIM3.PNG" alt="drawing" width="700"/> <br /> </p> 
<p align="left"> <img src="../assets/DIM4.PNG" alt="drawing" width="700"/> <br /> </p> 


## **Dimensions with PAROL6 adapter**

<p align="left"> <img src="../assets/DIM1.PNG" alt="drawing" width="700"/> <br /> </p> 



## **3D model**

[Link to the STEP model](https://github.com/PCrnjak/SSG-48-adaptive-electric-gripper/tree/main/STEPS)
<p align="left"> <img src="../assets/GRIP_MODEL.PNG" alt="drawing" width="900"/> <br /> </p> 


## **Torque curves**

<p align="left"> <img src="../assets/Grip_force.PNG" alt="drawing" width="1000"/> <br /> </p> 

As you can see from the plot relationship between current and applied force is linear.  Unit of current is Ampere [A] and unit of Force is Newton [N].

!!! Note annotate "Torque curve" 
    Note that this plot only applies to the grippers bought from source robotics that use BLDC motors with fine tuned Kt of 0.325. If you are building your own gripper this value might be different.

## **CAN bus termination**

!!! Tip annotate "**By default SSG48 gripper has terminated can bus with 120 ohm resistor!**" 
This can be adjusted by opening the gripper to access the Spectral Micro BLDC driver inside and flipping its termination resistor switch.

## **Spectral driver config**


!!! Note annotate "Config" 
    If you bought the gripper it comes preconfigured and calibrated!

If you are building the gripper you will need to send the following commands to it over serial to place the BLDC controller in the gripper mode and enable the thermistor: <br />

    #Gripper 1
    #Term 1
    #Save

## **Gripper linear speed**

Gripper min and max speed is commanded and returned in 0-255 format. <br /> </p> 
In the Spectral Micro firmware these values are maped to ticks/s 255 = 80000 ticks/s while 0 = 40 ticks/s <br /> </p> 
To calculate linear speed of the gripper jaws use this formula v[m/s] = () <br /> </p> 
r = 0.006m

$$
 \text{ticks_per_s} = 40 + \left(\frac{80000 - 40}{255}\right) \times C 
$$

$$ \omega = \frac{\text{ticks_per_s}}{2^{14}} \times 2\pi $$

$$ v = \omega \times r $$