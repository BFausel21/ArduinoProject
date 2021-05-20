// Ben Fausel
// Works Cited
// https://www.instructables.com/Servo-Button-Blink/
#include <Servo.h>
int x = 8;
int y = 9;
int z = 10;
int led1 = 3;
int led2 = 4;
int led3 = 6;
int led4 = 13;
int led5 = 12;
int led6 = 11;
#include <Servo.h>
Servo myservo;  
int pos = 0;
void setup() {
  // put your setup code here, to run once:
    Serial.begin(9600);
    pinMode(z, INPUT);
    pinMode(x, INPUT);
    pinMode(y, INPUT);
    pinMode(led1, OUTPUT);
    pinMode(led2, OUTPUT);
    pinMode(led3, OUTPUT);
    pinMode(led4, OUTPUT);
    pinMode(led5, OUTPUT);
    pinMode(led6, OUTPUT);
    myservo.attach(5);
}
void loop() {
  // put your main code here, to run repeatedly:
   if (digitalRead(x) == 1){
      digitalWrite(led1, HIGH);
    }else {
      digitalWrite(led1, LOW);
    }
      if (digitalRead(y) == 1){
      digitalWrite(led2, HIGH);
    }else {
      digitalWrite(led2, LOW);
    }
        if (digitalRead(z) == 1){
      digitalWrite(led3, HIGH);
    }else {
      digitalWrite(led3, LOW);
    }
    if (digitalRead(z) == 1 && digitalRead(x)== 1 ){
      digitalWrite(led4, HIGH);
    }else if (digitalRead(z) == 1 && digitalRead(y)== 1){
      digitalWrite (led5, HIGH);
    }else if (digitalRead(x) == 1 && digitalRead(y)== 1){
      digitalWrite(led6, HIGH);
    } else { 
      digitalWrite(led4, LOW);
      digitalWrite(led5, LOW);
      digitalWrite(led6, LOW);
      
    }
    if (digitalRead(x) == 1 && digitalRead(z) == 1 && digitalRead(y) == 1){
      for (pos = 0; pos <= 180; pos += 1) { 
    myservo.write(pos);              
    delay(15);                       
  }
  for (pos = 180; pos >= 0; pos -= 1) { 
    myservo.write(pos);             
    delay(15);                       
  }
    
}else {
  Serial.println("Servo is not spinning");
}
}
