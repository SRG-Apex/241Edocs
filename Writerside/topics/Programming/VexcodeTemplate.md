# Vexcode Template 

```C++
/*----------------------------------------------------------------------------*/
/*                                                                            */
/*    Module:       main.cpp                                                  */
/*    Program:      RoboticsCode                                              */
/*    Author:       John Smith                                                */
/*    Created:      3/20/2024                                                 */
/*    Modified:     3/20/2024                                                 */
/*    Description:  Template Code from Eclipse Docs                           */
/*                                                                            */
/*----------------------------------------------------------------------------*/

#include "vex.h"
using namespace vex;

// Definitions for essentials
competition Competition;
brain Brain;
controller Controller1 = controller(primary);
// controller Controller2 = controller(partner); // In case if Needed 

//Drivetrain elements (Assuming 6 motor 257) (see eclipse docs for more info)
motor driveFR = motor(PORT1, ratio6_1, false);
motor driveBR = motor(PORT2, ratio6_1, false);
motor driveMR = motor(PORT3, ratio6_1, false);
motor driveFL = motor(PORT4, ratio6_1, true);
motor driveBL = motor(PORT5, ratio6_1, true);
motor driveML = motor(PORT6, ratio6_1, true);
motor_group rightDrive = motor_group(driveFR, driveBR, driveMR);
motor_group leftDrive = motor_group(driveFL, driveBL, driveML);

// Not necessarily needed but useful if you need to control the drive all at once through something like a PID
motor_group dt = motor_group(driveFR, driveBR, driveMR, driveFL, driveBL, driveML);

// Drivetrain element specific initializations
inertial IMU = inertial(PORT7);

//Specific Definitions based on your drive, see Eclipse docs for more Info
double wheelTravel = 320; // 4 in wheels
double trackWidth = 320; // length between the center of the wheels (width wise) in mm
double wheelBase = 40;  // length between the center of front and back wheels (length wise)
double gearRatio = (36/84); // Gear Driven By Motor / Gear Driving Wheel 
smartdrive Drivetrain = smartdrive(leftDrive, rightDrive, IMU, wheelTravel, trackWidth, wheelBase, mm, gearRatio); // Drivetrain Element 

// define your global instances of motors 
motor smartMotor = motor(PORT8, ratio36_1, false); 

// define other sensors here
rotation smartMotorRotation = rotation(PORT9);
distance smartMotorDistance = distance(PORT10);
vision Vision = vision(PORT11); // Note, you will have to configure the vision sensor, see Eclipse Docs for more info

// Define Pistons here 
pneumatics pistonA = pneumatics(Brain.ThreeWirePort.A);

// motor bools for DC motor Controllers 
bool drivetrainLeftBool = true;
bool drivetrainRightBool = true;
bool smartMotorBool = true;



/*---------------------------------------------------------------------------*/
/*                          Pre-Autonomous Functions                         */
/*                                                                           */
/*  You may want to perform some actions before the competition starts.      */
/*  Do them in the following function.  You must return from this function   */
/*  or the autonomous and usercontrol tasks will not be started.  This       */
/*  function is only called once after the V5 has been powered on and        */
/*  not every time that the robot is disabled.                               */
/*---------------------------------------------------------------------------*/

void pre_auton(void) {

}


/*---------------------------------------------------------------------------*/
/*                          Autonomous Functions                             */
/*                                                                           */
/*  Use This space to define functions to be used in autonomous,             */
/*  This includes control loops like PID, or Odomtry                         */
/*                                                                           */
/*  See Eclipse Docs for More Info                                           */
/*---------------------------------------------------------------------------*/                                                                           

// ..........................................................................
// Insert autonomous Fuction code here.
// ..........................................................................


/*---------------------------------------------------------------------------*/
/*                              Autonomous Task                              */
/*                                                                           */
/*  This task is used to control your robot during the autonomous phase of   */
/*  a VEX Competition.                                                       */
/*                                                                           */
/*  You must modify the code to add your own robot specific commands here.   */
/*---------------------------------------------------------------------------*/

void autonomous(void) {
  // ..........................................................................
  // Insert autonomous user code here.
  // ..........................................................................
}

/*---------------------------------------------------------------------------*/
/*                                                                           */
/*                              User Control Task                            */
/*                                                                           */
/*  This task is used to control your robot during the user control phase of */
/*  a VEX Competition.                                                       */
/*                                                                           */
/*  You must modify the code to add your own robot specific commands here.   */
/*---------------------------------------------------------------------------*/

void usercontrol(void) {
  // User control code here, inside the loop
  while (1) {
    // This is the main execution loop for the user control program.
    // Each time through the loop your program should update motor + servo
    // values based on feedback from the joysticks.

    // ........................................................................
    // Insert usercontrol user code here.
    // ........................................................................

    wait(20, msec); // Sleep the task for a short amount of time to
                    // prevent wasted resources.
  }
}

//
// Main will set up the competition functions and callbacks.
//
int main() {
  // Set up callbacks for autonomous and driver control periods.
  Competition.autonomous(autonomous);
  Competition.drivercontrol(usercontrol);

  // Run the pre-autonomous function.
  pre_auton();

  // Prevent main from exiting with an infinite loop.
  while (true) {
    wait(100, msec);
  }
}
```

I Included so basic definitions for Elements, you may need to modify and or remove some depending on if you use certain parts or not