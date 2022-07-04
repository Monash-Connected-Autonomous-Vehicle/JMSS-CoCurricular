# Tutorial 3 - Motor Driver

Continuing on from the last tutorial, next we will explore the "act" portion of the robotics loop. 
The act operation involves sending information to physical hardware that moves the robot. As you can imagine, 
when the robot moves, all of its sensor information will change which triggers the loop again.

![](TinkerSS/MCAV/Capture2.PNG)

## Role of H-Bridges in Driving Motors
***
A DC motor (Direct Current motor) is a motor which rotates when a voltage is applied at its terminals. 
The speed of the motor is proportional to the voltage and direction is dependent on the polarity (direction of current).
Simply put, a DC motor spins when you connect it to a DC power source (like a battery). 
The greater the voltage, the faster it will spin. If the power source is connected in reverse, the motor will spin in the opposite direction, but with the same speed as before. This is exactly how the speed and direction of a DC motor are controlled.
While the speed control can be done fairly easily by a microcontroller (using Pulse Width Modulation), DC motors usually require more current than most microcontrollers can provide. 
This is where H-Bridges step in. H-Bridges act as intermediary circuits which allow bi-directional current amplification, allowing the microcontroller to drive the motor in both directions while not getting damaged. 
Some H-Bridges (Like the L293D) also provide additional pins for more convenient speed control.

![](TinkerSS/MCAV/Capture1.PNG)

A H-Bridge is a circuit which can be used to control the direction of a DC motor. It contains four switching elements (usually transistors) which together with a motor form a H-like configuration. The switching elements form "complementary" pairs which allows the direction of current flow to the motor to be reversed if desired. In other words, the H-Bridge acts as a set of digitally controlled switches which can be used to control the voltage across a motor.


![](TinkerSS/MCAV/Capture3.PNG)

The L293D is a very popular H Bridge IC. Internally, it contains two H Bridges allowing you to individually drive 2 motors bidirectionally up to 36V at 0.6A each (1A for short spurts). It also contains two additional pins for more convenient speed control (explained in detail later).

![](TinkerSS/MCAV/Capture4.PNG)
![](TinkerSS/MCAV/Capture5.PNG)

| Name | Function |
| --- | --- |
| Vcc 1/2 | Pins 16 (VSS) and 8 (VS) need to be connected to the positive terminal of your power supply which will be used to drive the load. |
| GND | Common ground for all power supplies. Pins 4, 5, 12 or 13 (all are GND) need to be connected to the negative terminal. |
| Input 1/2/3/4 | The state of each input pin reflects the state of its respective output pin. For example, setting the state of pin 2 (INPUT 1) and 7 (INPUT 2) to high and low respectively will cause pins 3 (OUTPUT 1) and 6 (OUTPUT 2) to be set to high and low respectively and vice-versa. In other words, current can flow in either direction by reversing the states of the INPUT pins. These pins are the alternating switches of the H-Bridge. Similarly, pins 10 and 15 (INPUT 3 and 4) are used for controlling pins 11 and 14 (OUTPUT 3 and 4), allowing a second load to be connected and driven independent of the first. |
| Output 1/2/3/4 | These is where you will connect your motors. |
| Enable 1,2/3,4 | Setting an enable pin to high, switches on or “enables” its respective H Bridge circuit while setting it low, breaks the circuit. Enable 1,2 Corresponds to Input 1,2 and Output 1,2 and Enable 3,4 Corresponds to Input 3,4 and Output 3,4 |


## Task 1: Controlling Motors
***
In this section, We will assemble a test circuit to drive both motors using an Arduino UNO and the L293D. Here is a list of the components you will require-
* An Arduino UNO
* 2 DC motors
* The L293D H-Bridge
* A breadboard
* A suitable power supply to drive your motors (9V can be used)

### Connections:
Connect the H-Bridge to the breadboard as shown in the image below


Connect the pins on the breadboard to the Arduino UNO pins as shown in the table and the image below

| Name | Function |
| --- | --- |
| Vcc 1/2 | Connect to the Positive Terminal |
| GND | Connect all pins to the Negative Terminal (GND) |
| INPUT 1 | PIN 2 |
| INPUT 2 | PIN 3 |
| INPUT 3 | Pin 4 |
| INPUT 4 | PIN 5 |
| OUTPUT 1 | Positive Terminal of motor B |
| OUTPUT 2 | Negative Terminal of motor B |
| OUTPUT 3 | Positive Terminal of motor A |
| OUTPUT 4 | Negative Terminal of motor A |
| ENABLE 1,2 | PIN 10 |
| ENABLE 3,4 | PIN 11 |

### Code:

Copy the code below to your Arduino IDE, try to understand it and run it on your Arduino UNO set

```
//L293D
//Motor A
const int motorPin1  = 2;  // Pin 15 of L293
const int motorPin2  = 3;  // Pin 10 of L293
//Motor B
const int motorPin3  = 4; // Pin  7 of L293
const int motorPin4  = 5;  // Pin  2 of L293

//This will run only one time.
void setup(){
 
    //Set pins as outputs
    pinMode(motorPin1, OUTPUT);
    pinMode(motorPin2, OUTPUT);
    pinMode(motorPin3, OUTPUT);
    pinMode(motorPin4, OUTPUT);
    
    //Motor Control - Motor A: motorPin1,motorpin2 & Motor B: motorpin3,motorpin4

    //This code  will turn Motor A clockwise for 2 sec.
    digitalWrite(motorPin1, HIGH);
    digitalWrite(motorPin2, LOW);
    digitalWrite(motorPin3, LOW);
    digitalWrite(motorPin4, LOW);
    delay(2000); 
    //This code will turn Motor A counter-clockwise for 2 sec.
    digitalWrite(motorPin1, LOW);
    digitalWrite(motorPin2, HIGH);
    digitalWrite(motorPin3, LOW);
    digitalWrite(motorPin4, LOW);
    delay(2000);
    
    //This code will turn Motor B clockwise for 2 sec.
    digitalWrite(motorPin1, LOW);
    digitalWrite(motorPin2, LOW);
    digitalWrite(motorPin3, HIGH);
    digitalWrite(motorPin4, LOW);
    delay(2000); 
    //This code will turn Motor B counter-clockwise for 2 sec.
    digitalWrite(motorPin1, LOW);
    digitalWrite(motorPin2, LOW);
    digitalWrite(motorPin3, LOW);
    digitalWrite(motorPin4, HIGH);
    delay(2000);    
    
    //And this code will stop motors
    digitalWrite(motorPin1, LOW);
    digitalWrite(motorPin2, LOW);
    digitalWrite(motorPin3, LOW);
    digitalWrite(motorPin4, LOW);
  
}


void loop(){
}
  
```

* Note down the direction the motor is turning. Can you modify the code to make the motor turn the other way? Use the table below to help you. See if you can identify the function of each of the variations! (e.g turn motor clockwise, turn off motor etc.)

| ENABLE1 | INPUT1 | INPUT2 | Function |
| --- | --- | --- | --- |
| H | H | H |  |
| H | L | H |  |
| H | H | L |  |
| H | L | L |  |
| L | X | X |  |

** This is for One motor 

Try Changing the direction and duration of rotation of both motors.


