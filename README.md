# obstacle-avoid-robot
obstacle avoiding robot using ultrasonic sensor
/*Obstacle avoidance Robot car.
  created by the SriTu Tech team.
  Read the code below and use it for any of your creation
*/

#include <Servo.h>
#define Speed 180
#define Trig A0
#define Echo A1
#define spoint 90
#define m1 7  //Right Motor MA1
#define m2 6  //Right Motor MA2
#define m3 5  //Left Motor MB1
#define m4 4  //Left Motor MB2
#define e1 9  //Right Motor Enable Pin EA
#define e2 10 //Left Motor Enable Pin EB

int distance;
int Left;
int Right;
int L = 0;
int R = 0;
Servo servo;

 
void setup() {
  Serial.begin(9600);
  pinMode(Trig, OUTPUT);
  pinMode(Echo, INPUT);
  servo.attach(11);
  start();
  pinMode(m1, OUTPUT);
  pinMode(m2, OUTPUT);
  pinMode(m3, OUTPUT);
  pinMode(m4, OUTPUT);
  pinMode(e1, OUTPUT);
  pinMode(e2, OUTPUT);
  
 
}
 
void loop() {
  
  distance = ultrasonic();
  Serial.println(distance);
  if (distance > 15){
    forward();

  }
  if(distance=0){
    forward();
  }
  else if (distance <= 15 && distance >1) {
    Stop();
    delay(100);
    backward();
    delay(200);
    Stop();
    L = leftsee();
    servo.write(spoint);
    delay(500);
    R = rightsee();
    servo.write(spoint);
    if (L < R) {
      turnleft();
      delay(500);
      Stop();
      delay(200);
    } else if (L > R) {
      turnright();
      delay(500);
      Stop();
      delay(200);
    }
  } 
}
 
void forward() {
  digitalWrite(m1, HIGH);
  digitalWrite(m2, LOW);
  digitalWrite(m3, HIGH);
  digitalWrite(m4, LOW);
  
}
void backward() {
  digitalWrite(m1, LOW);
  digitalWrite(m2, HIGH);
  digitalWrite(m3, LOW);
  digitalWrite(m4, HIGH);

}
void turnleft() {
  digitalWrite(m1, LOW);
  digitalWrite(m2, HIGH);
  digitalWrite(m3, HIGH);
  digitalWrite(m4, LOW);
  
}
void turnright() {
  digitalWrite(m1, HIGH);
  digitalWrite(m2, LOW);
  digitalWrite(m3, LOW);
  digitalWrite(m4, HIGH);
  

}
void Stop() {
   digitalWrite(m1, LOW);
   digitalWrite(m2, LOW);
   digitalWrite(m3, LOW);
   digitalWrite(m4, LOW);
  

}
int leftsee() {
  servo.write(20);
  delay(800);
  Left = ultrasonic();
  return Left;
}
 
int rightsee() {
  servo.write(150);
  delay(800);
  Right = ultrasonic();
  return Right;
}
 
int ultrasonic() {
  digitalWrite(Trig, LOW);
  delayMicroseconds(2);

  digitalWrite(Trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(Trig, LOW);

  unsigned long duration = pulseIn(Echo, HIGH);
  float distance = duration * 0.034 / 2;

  return distance;
  
}
void start() {
  delay(3000);
  for (int a = 0; a < 4; a++) {
    servo.write(spoint);
    delay(50);
    servo.write(40);
    delay(50);
    servo.write(90);
    delay(50);
    servo.write(spoint);
  }
}
