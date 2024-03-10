# Defining Elements

Elements are what are globally defined at the beginning of your code, they are your Brain, Controller, Motors, Sensors, and Pneumatics

Vexcode is based on C++ so your definitions will follow the same template of 

```
DataType VarName = Value
```

Every Robot needs the following definitions, these do not vary based on the robot 

```C++
competition Competition; // Global instance of competition used for the Competition Template 
brain Brain;
contoller ControllerMain = controller(primary);
```
