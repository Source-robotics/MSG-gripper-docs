# **Safety and Maintenance**

SSG48 gripper is not ment to be used with industrial robots. The gripper, robot and equipment used need to be evaluated with risk assessment and it is duty of the gripper integrator.

!!! Warning annotate "Warning" 
    The operator must read and understand all of the instructions noted in this manual before using and handling the gripper.

## **Warning**
!!! Danger annotate "Danger"
    The Gripper should not be used in disregard of these safety tips and warnings, as it may lead to injury or damage.

## **Temperature warning**

The gripper has built in termistor in motor coils that will stop it from reaching too high temperatures. That limit is 75 degrees. After it is reached the temperature error will be triggered and the gripper will go do idle mode. This temperature limit can be changed via UART commands-

## **Gripper force**

This gripper can exert large amount of force (80N) on top of that it reach really high speeds.
Those 2 combined can be dangerous for humans and other objects. It is recommneded to always keep current preset and speed at low values while testing. Those values could be:

* Current: 300
* Speed: 30

After you confirm your aplication works increase the values.

!!! Danger annotate "Danger" 
    **NEVER PLACE YOUR FINGER INSIDE THE GRIPPER.**

## **Pinching points**

!!! Danger annotate "Pinching points" 
    The gripper Jaws act as a pinching point and if current limit is set to a large value it can hurt you and others.

## **Estop**

The gripper will go do idle mode if it receives estop_status = 1 from Send_gripper_data_pack

## **Maintenance**

Note that gripper is not waterproof or dust proof. The jaws part has a large gaps that allow dust, water and particles to enter the gripper. Never use the gripper in dusty and moist environments. 

## **Gear lubrication**

You can apply lithium greese to lubricate the gears of the gripper. To do that remove 4 screw that hold linear track of the jaws and apply greese to the jaws.

## **Errors**

The gripper returns 4 bits related to errors with its **Respond_Gripper_data_pack**

* **General error bit** - This bit will be 1 if any other error is active
* **Temperature error bit** - If temperature of motor coils goes above some value this will go to 1
* **Timeout error bit** - Not implemented
* **Estop error bit** - Will go to 1 if we receive Estop status 1 from Send_gripper_data_pack

!!! Note annotate "Errors" 
    Note that errors will remain active until you call Send_Clear_Error
