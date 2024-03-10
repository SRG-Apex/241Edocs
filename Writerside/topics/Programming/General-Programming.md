# General Programming

When programming your robot your program is **required** to use the competition template, the competition template must have the following topology which should be setup when creating the program.



```C++

//Code Header

#include "vex.h"
using namespace vex;

competition Competition;
brain Brain;
controller Controller1 = controller(primary);

//Enter the definition for your motors and sensors here 

void pre_auton(void){

// Enter your pre-auton function here

}

// Enter your Autonomous Functions here


void autonomous(void){

// Enter your Autonomous Code Here

}

void usercontrol(void){

    while(1){

// Enter your driver contol code here 

    wait(20,msec);
    }
}

int main(){
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