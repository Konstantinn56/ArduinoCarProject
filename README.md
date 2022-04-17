# ArduinoCarProject
This is our first attempt in building a bluetooth controlled car with Arduino. Once we get down all the parts we wanted to build it and test it. But there was a problem with our 3D Printed chassis. The Motors didn't want to work propertly, because the chasisis chains were to tight. So we didn't have enough time to find new chassis, that's why we decided to just make it work. For the power supply we used a 9V battery.

STEP 1:

![picture_2 1](https://user-images.githubusercontent.com/75718282/163690567-b3c3713a-85c5-4857-826a-12aaf83b955e.jpg)

STEP 2:

![picture_2 2](https://user-images.githubusercontent.com/75718282/163690577-007896b4-e5e0-434a-bc85-398164c7c684.jpg)

STEP 3:

![picture_2 3](https://user-images.githubusercontent.com/75718282/163690581-a5b46820-f500-4269-b5f4-0cd2bc435059.jpg)

STEP 4:

![picture_2 4](https://user-images.githubusercontent.com/75718282/163690588-df07213f-40e1-4daa-b36e-3ff98b79761b.jpg)

STEP 5:

![picture_2 5](https://user-images.githubusercontent.com/75718282/163690593-2d9df961-47fe-4221-ba24-7e34a481cd1b.jpg)

STEP 6:

![picture_2 7](https://user-images.githubusercontent.com/75718282/163690598-08c16b96-0ebb-4fc8-a078-0b2ddf497177.jpg)

--------------------------------------------------------------------------------
# SCHEMATICS:
![unknown](https://user-images.githubusercontent.com/75718282/163690910-88c3df38-b91c-430e-9ed6-1b0e583c3cf4.png)
--------------------------------------------------------------------------------
# COMPONENTS AND SUPPLIES:
Arduino UNO - x1
9V Battery - x1
DC Motor - x2
Jumper wires (generic) - x1
Bluetooth module HC-05 - x1
Mini Motor Drive 2ch Shield L293D - x1

--------------------------------------------------------------------------------
# CODE:
```
// Control 2 DC motors with Smartphone via bluetooth
int state = 0;
int flag = 0;    
 
int motor1Pin1 = 6; 
int motor1Pin2 = 5; 
int motor2Pin1 = 9; 
int motor2Pin2 = 10; 

void setup() 
{
    // sets the pins as outputs:
    pinMode(motor1Pin1, OUTPUT);
    pinMode(motor1Pin2, OUTPUT);
    pinMode(motor2Pin1, OUTPUT);
    pinMode(motor2Pin2, OUTPUT);  
    // initialize serial communication at 9600 bits per second:
    Serial.begin(9600);
}

void stop()
{
	      digitalWrite(motor1Pin1, LOW); 
  	      digitalWrite(motor1Pin2, LOW); 
  	      digitalWrite(motor2Pin1, LOW);
  	      digitalWrite(motor2Pin2, LOW);
}

void loop() 
{
    // if some date is sent, reads it and saves in state
    if(Serial.available() > 0)
    {     
      state = Serial.read();   
      flag = 1;
      if(flag == 1) Serial.println(state);
    }  
  
     // Forward
  	  if (state == 'F') 
  	  {
  	      digitalWrite(motor1Pin1, HIGH);
  	      digitalWrite(motor1Pin2, LOW); 
  	      digitalWrite(motor2Pin1, LOW);
  	      digitalWrite(motor2Pin2, HIGH);
  	      if(flag == 1) Serial.println("FORWARD");
  	  }
  	  // Backward
  	  else if (state == 'B') 
  	  {
  	      digitalWrite(motor1Pin1, LOW); 
  	      digitalWrite(motor1Pin2, HIGH);
  	      digitalWrite(motor2Pin1, HIGH);
  	      digitalWrite(motor2Pin2, LOW);
  	      if(flag == 1) Serial.println("BACKWARD");
  	  }
  	  // Stop
  	  else if (state == 'S') 
  	  {
  	      digitalWrite(motor1Pin1, LOW); 
  	      digitalWrite(motor1Pin2, LOW); 
  	      digitalWrite(motor2Pin1, LOW);
  	      digitalWrite(motor2Pin2, LOW);
  	      if(flag == 1) Serial.println("STOP");
  	  }
  	  // Right
  	  else if (state == 'R') 
  	  {
  	      digitalWrite(motor1Pin1, LOW); 
  	      digitalWrite(motor1Pin2, LOW); 
  	      digitalWrite(motor2Pin1, LOW);
  	      digitalWrite(motor2Pin2, HIGH);
  	      if(flag == 1) Serial.println("RIGHT");
  	      delay(1500);
  	  }
  	  // Left
  	  else if (state == 'L') 
  	  {
  	      digitalWrite(motor1Pin1, HIGH); 
  	      digitalWrite(motor1Pin2, LOW); 
  	      digitalWrite(motor2Pin1, LOW);
  	      digitalWrite(motor2Pin2, LOW);
  	      if(flag == 1) Serial.println("LEFT");
  	      delay(1500);
  	  }
    flag = 0;
}
```
--------------------------------------------------------------------------------
We had a lot of problems with the project, and we couldn't finish it completely with all its functionalities. If we had just a little more time, we could have done it successfully.



