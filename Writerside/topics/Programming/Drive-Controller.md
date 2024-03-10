# Drive Controller

The Drive Controller is used to control your drivetrain during the driver control period, there are multiple different control methods including 

- Tank Drive: Where the left stick controls the left drive and the right stick controls the right drive
- Arcade Stick: One stick controls Forward and backward movement, and the other controls turning 
- Single Stick: One stick controls both forward, backwards movement and left, right turning 

The Drive Controller starts by getting the power to be sent to the drive train used by taking the values from the Analogue Sticks 

```C++
// Tank Drive Power Equations 
int drivetrainRightSideSpeed = ControllerMain.Axis2.position();
int drivetrainLeftSideSpeed = ControllerMain.Axis3.position();
```

```C++
// Arcade stick power equations 
int drivetrainRightSideSpeed = ControllerMain.Axis3.position() - ControllerMain.Axis1.position();
int drivetrainLeftSideSpeed = ControllerMain.Axis3.position() + ControllerMain.Axis1.position();
```

```C++
// Single stick power equations
int drivetrainRightSideSpeed = ControllerMain.Axis3.position() - ControllerMain.Axis4.position();
int drivetrainLeftSideSpeed = ControllerMain.Axis3.position() + ControllerMain.Axis4.position();
```


The rest of the drivetrain contoller code will be the same

```C++
    // Deadzone Controller
    if (drivetrainLeftSideSpeed < 5 && drivetrainLeftSideSpeed > -5) {
        if (drivetrainLeftBool) {
          leftDrive.stop();
          drivetrainLeftBool = false;
        }
      } else {
        drivetrainLeftBool = true;
      }
      // Deadzone Controller
      if (drivetrainRightSideSpeed < 5 && drivetrainRightSideSpeed > -5) {
        if (drivetrainRightBool) {
          rightDrive.stop();
          drivetrainRightBool = false;
        }
      } else {
        drivetrainRightBool = true;
      }
      
      if (drivetrainLeftBool) {
        leftDrive.setVelocity(drivetrainLeftSideSpeed, percent);
        leftDrive.spin(forward);
      }

      if (drivetrainRightBool) {
        rightDrive.setVelocity(drivetrainRightSideSpeed, percent);
        rightDrive.spin(forward);
      }
```

You may want to change the values in the Deadzone Contollers if you notice the drive moving without moving the sticks 




