/*
* Author: Evan Kilburn
*
* Setup: a photoresistor facing an LED that is on.
* a voltage divider of +5V to 51K to photoresistor to GND
* A14 = photoresistor
*/
int state;
const int Roam = 1;
const int Forwards = 2;
const int Left = 3;
const int Right = 4;
const int Avoid = 5;
const int Rest = 6;
const int M1 = 3;
const int M2 = 5;
const int M3 = 6;
const int M4 = 11;
volatile int wheel = LOW;
void setup(){
 pinMode(52,INPUT_PULLUP);
 pinMode(32,OUTPUT);
 pinMode(30,OUTPUT);
 Serial.begin(9600);
 pinMode(2,INPUT);//encodedr wheel
 attachInterrupt(0,blink,CHANGE);
 state = Roam;
}

void loop(){
 long target;
 int count;
 int LeftLight = analogRead(A10);
 int RightLight = analogRead(A9);
 digitalWrite(31,wheel);
 Serial.println(wheel);
 delay(25);
  switch(state){
    if (LeftLight > 60 and RightLight > 60){ //straight
      digitalWrite(30,LOW);//right
      digitalWrite(32,LOW);//left
      delay(10); 
      state = Roam;
    }
    if (LeftLight < 60 and RightLight < 60){//stop
      digitalWrite(30,LOW);
      digitalWrite(32,LOW);
      delay(10);
      state = Rest;
    }
    if (LeftLight > 60 and RightLight < 60){//right
      digitalWrite(30,LOW); //left
      digitalWrite(32,HIGH); //right
      delay(2000);
      digitalWrite(30,LOW);
      digitalWrite(32,LOW);
      delay(10);
      state = Right; 
    }
    if (LeftLight < 60 and RightLight > 60){//left
      digitalWrite(30,HIGH); //left
      digitalWrite(32,LOW); //right
      delay(2000);
      digitalWrite(30,LOW);
      digitalWrite(32,LOW);
      delay(10); 
      state = Left;
    }
 if (state = Roam){
  digitalWrite(M1,HIGH);
  digitalWrite(M2,LOW);
  digitalWrite(M3,LOW);
  digitalWrite(M4,HIGH);
  delay(1500);
  
 }
 if (state = Rest){
  digitalWrite(M1,LOW);
  digitalWrite(M2,LOW);
  digitalWrite(M3,LOW);
  digitalWrite(M4,LOW);
 }
}
}
void blink(){
  wheel =! wheel;
}



 
 
