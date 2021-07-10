#Smart_Dustbin Internet Of Things_Project-BSE173120_BSE173047


Smart Dustbin using Arduino Uno
 
Introduction
In the recent decades, urbanization has increased tremendously. At the same phase there is an increase in waste production. Waste management has been a crucial issue to be considered. This   proposal is a way to achieve this good cause. In this project smart dustbin is built on a microcontroller-based platform Arduino Uno board which is interfaced with the Servo motor and ultrasonic sensor. Ultrasonic sensor is placed at the top of the dustbin which will measure the stature of the dustbin. The threshold stature is set at a particular level. Arduino will be programmed in such a way that when someone will come in front of dustbin the servo motor will come in action and open the lid for the person to put the waste material into the dustbin. Once these smart bins are implemented on a large scale, by replacing our traditional bins present today, waste can be managed efficiently as it avoids unnecessary lumping of wastes on roadside. Foul smell from these rotten wastes that remain untreated for a long time, due to negligence of authorities and carelessness of public may lead to long term problems. Breeding of insects and mosquitoes can create nuisance around promoting unclean environment. This may even cause dreadful diseases. Smart Dustbin as its name represents it works smartly or we can say that it is an automatic dustbin. it works like when you will come in front of this dustbin it will open automatically with the help of a servo motor. so, there is some sensor work to detect the object in front of the dustbin. smart Dustbin is a very good project from the Arduino board. it works likewise smart things. we can say that, it is a decent gadget to make your home clean and attractive. due to practically all offspring of home consistently make it grimy and spread trash to a great extent by paper, rappers and numerous different things.
Supplies
Smart dustbin having the sensor when it detects any object in front of it, it opens and closes it’s top. components required to make smart dustbin: -
•	Ultrasonic sensor
•	Arduino Uno
•	Servo motor
•	Jumper wires
Circuit Diagram 

 
Figure 1 circuit diagram
Steps
1.	Take a plastic sheet and cut a circle according to the size of the dustbin.
2.	Place the ultra-sonic sensor in the dustbin.
3.	Connect the Arduino and upload the given program on your Arduino uno and place the Arduino in the dustbin with the help of double tape.

#include <Servo.h>   //servo library
Servo servo;     
int trigPin = 5;    
int echoPin = 6;   
int servoPin = 7;
int led= 10;
long duration, dist, average;   
long aver[3];   //array for average


void setup() {       
    Serial.begin(9600);
    servo.attach(servoPin);  
    pinMode(trigPin, OUTPUT);  
    pinMode(echoPin, INPUT);  
    servo.write(0);         //close cap on power on
    delay(100);
    servo.detach(); 
} 

void measure() {  
 digitalWrite(10,HIGH);
digitalWrite(trigPin, LOW);
delayMicroseconds(5);
digitalWrite(trigPin, HIGH);
delayMicroseconds(15);
digitalWrite(trigPin, LOW);
pinMode(echoPin, INPUT);
duration = pulseIn(echoPin, HIGH);
dist = (duration/2) / 29.1;    //obtain distance
}
void loop() { 
  for (int i=0;i<=2;i++) {   //average distance
    measure();               
   aver[i]=dist;            
    delay(10);              //delay between measurements
  }
 dist=(aver[0]+aver[1]+aver[2])/3;    

if ( dist<50 ) {
//Change distance as per your need
 servo.attach(servoPin);
  delay(1);
 servo.write(0);  
 delay(3000);       
 servo.write(150);    
 delay(1000);
 servo.detach();      
}
Serial.print(dist);
}


4.	Place the 9 Volt Battery and Wire the circuit as shown in the figure 1.
5.	Now Place the Plastic circle that we had cut in the second step and glue the half circle on the dustbin and take the servo motor and place it on the circle with fix it with the help of some glue as shown in the pictures. Take a string and a metal Washer and tie a knot with the string as and make a hole and pass it through the plastic circle and again tie a not with servo motor.
6.	Now Wire the Servo Motor according to the above given diagram and you have completed the project.
