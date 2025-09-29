1) Arduino UNO Bluetooth Car 🚗🔧:-
 "A simple and fun project to control a car using Arduino UNO, HC-05 Bluetooth module, and L298N Motor Driver. The car can be controlled wirelessly via a smartphone app."

2) Features :-
Control car wirelessly using Bluetooth.
Forward, backward, left, and right movement.
Powered by Arduino UNO.
Uses L298N/L293D motor driver.
Easy to assemble and beginner-friendly.

3) Components Required :-
Arduino UNO 
HC-05 Bluetooth Module
L298N / L293D Motor Driver
DC Motors (x4)
Car chassis
Wheels
Battery pack
Jumper wires

4) Circuit Diagram:- 
<img width="912" height="720" alt="image" src="https://github.com/user-attachments/assets/39074284-fc6c-4abd-b83b-1faa630a878c" />


5) Arduino Code :-

// Bluetooth Car using pins 0 and 1 for HC-05
// Commands: F=Forward, B=Backward, L=Left, R=Right, S=Stop

int IN1 = 7;
int IN2 = 6;
int IN3 = 5;
int IN4 = 4;
char command = 'S';
void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  Serial.begin(9600);  // communicate with HC-05
  stopCar();
}
void loop() {
  if (Serial.available() > 0) {
    command = Serial.read();
    if (command == 'F') forward();
    else if (command == 'B') backward();
    else if (command == 'L') left();
    else if (command == 'R') right();
    else if (command == 'S') stopCar();
  }
}
void forward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}
void backward() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}
void left() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}
void right() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}
void stopCar() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}


6) Smartphone App :-
You can use any Bluetooth terminal app (like Arduino Bluetooth Controller from Play Store).

Send F → Forward
Send B → Backward
Send L → Left
Send R → Right
Send S → Stop

## 📜 License
This project is open-source under the **MIT License**.  
You are free to use and modify it for learning purposes.  
