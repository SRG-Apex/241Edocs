# Motor Controllers

Motor Controllers are used in Driver Control code

it is an efficient way of controlling a motor, there are many ways of creating motor controllers, 

```C++

// 241E Motor Controller
if (Controller.ButtonR1.pressing()){
    Motor.spin(forward);
    MotorBool=false;
    } else if (Controller.ButtonR2.pressing()){
        Motor.spin(reverse);
        MotorBool=false;
        } else if (!MotorBool){
        Motor.stop();
        MotorBool = true;
        }

```

This was the motor controller we had used for SU, and OU 

it works based on a boolean to tell the motor to only stop your motor once, while still being able to listen to other controls

Another type of controller is the 2 button toggle which will start a motor until another button is pressed

```C++

// 241E 2 Button Toggle 
if (Controller.ButtonR1.pressing()){
    Motor.spin(forward);
}
else if (Controller.ButtonR2.pressing()){
    Motor.stop();
}

```





