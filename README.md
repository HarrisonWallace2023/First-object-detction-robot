#include <Servo.h>
int button = 8;
int motor = 3;
int trigpin = 11;
int echopin = 10;

void setup() {
 pinMode(button, INPUT); //pin mode tells something to act as an input or an out put
 pinMode(motor, OUTPUT);
 pinMode(trigpin, OUTPUT);
 Serial.begin(9600); // sends out commands to USB  

}

void loop() {
 long duration, inches, cm; // extneded size varables for numbers



 int buttonstate = digitalRead(button); // reads the value from a specified dital pin, either HIGH or LOW

   inches = microsecondsToInches(duration); //microseconds must be difined in another function
   delay(10);
   Serial.print("Inches="); // prints data to serial port to be read as data  
   Serial.println(inches);
   if (inches >= 10)
   {
     digitalWrite(motor, 0); // makes pin 13 an out put and switches it between high and low at one second pace

   }
   else
   {
     digitalWrite(motor,1);
   }





}
double microsecondsToInches(long duration)
{
 digitalWrite(trigpin, LOW);
 delayMicroseconds(2);
 digitalWrite(trigpin, HIGH);
 delayMicroseconds(10);
 digitalWrite(trigpin, LOW);
 duration = pulseIn(echopin, HIGH);
 return duration / 74 / 2;
}
