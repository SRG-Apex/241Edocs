# Driver Control

The "usercontrol" Section of code is used during the Driver Control Section of the match 

this is the section to put how your controller interacts with the robot, you may have 2 different controller defined as your primary or partner

```C++ 
controller Controller = controller(primary);
```
or
```C++
controller Controller = controller(partner); 
```

The way you read the controller's state (Essentially if something is happening) is through the Axis or the Buttons 

there are 12 usable buttons on the controller
```C++
controller.ButtonR1
controller.ButtonR2
controller.ButtonL1
controller.ButtonL2
controller.ButtonA
controller.ButtonB
controller.ButtonX
controller.ButtonY
controller.ButtonUp
controller.ButtonDown
controller.ButtonLeft
controller.ButtonRight
```
To read the state of the buttons use the .pressing() method. This will return a boolean depending on if the button was being pressed at the moment of code execution.

Example 
```C++
ControllerMain.ButtonR1.pressing();
```

there are also the 4 Axis on the controller, normally onl used for drivetrain
```C++
controller.Axis1
controller.Axis2
controller.Axis3
controller.Axis4
```
to read the value from the axis use the .position() method, this returns a value from 0 to 100 depending on how far the axis is pushed 
```C++
Controller1.Axis3.position()
```

you can use some math to get a value to be passed to the drive, for example Arcade Stick drive control gets the value like this...

```C++
int drivetrainRightSideSpeed = ControllerMain.Axis3.position() - ControllerMain.Axis1.position();
int drivetrainLeftSideSpeed = ControllerMain.Axis3.position() + ControllerMain.Axis1.position();
```

Too see in depth uses and controllers goto [Drive Controller](Drive-Controller.md) or [Motor Controllers](Motor-Controllers.md)

