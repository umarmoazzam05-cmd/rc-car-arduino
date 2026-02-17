# Arduino RC Car 🚗
This is a Bluetooth-controlled RC car using Arduino.

## Features
- Wireless control
- Speed control
- Easy setup

## Components
- Arduino Uno
- Motor Driver
- Bluetooth Module
- Battery
- Chassis
- Tyres
- Motors
- Connecting wires

## How to Use
1. Upload code
2. Connect circuit
3. Pair Bluetooth
4. Run car

## Arduino Code:
// Motor driver input pins connected to Arduino
#define in1 12   // Motor 1 direction pin
#define in2 11   // Motor 1 direction pin
#define in3 10   // Motor 2 direction pin
#define in4 9    // Motor 2 direction pin

void setup() {
  // Start serial communication at 9600 baud rate
  // Used to receive commands from Bluetooth / PC
  Serial.begin(9600);

  // Set motor pins as output
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(in3, OUTPUT);
  pinMode(in4, OUTPUT);
}

void loop() {

  // Check if any data is available on Serial
  if (Serial.available() > 0) {

    // Read one character from Serial
    char inputvalue = Serial.read();

    // Move Right
    if (inputvalue == 'R') {
      digitalWrite(in1, HIGH);
      digitalWrite(in2, LOW);
      digitalWrite(in3, HIGH);
      digitalWrite(in4, LOW);
    }

    // Move Forward
    else if (inputvalue == 'F') {
      digitalWrite(in1, LOW);
      digitalWrite(in2, HIGH);
      digitalWrite(in3, LOW);
      digitalWrite(in4, HIGH);
    }

    // Move Backward
    else if (inputvalue == 'B') {
      digitalWrite(in1, LOW);
      digitalWrite(in2, LOW);
      digitalWrite(in3, HIGH);
      digitalWrite(in4, LOW);
    }

    // Turn Left
    else if (inputvalue == 'L') {
      digitalWrite(in1, HIGH);
      digitalWrite(in2, LOW);
      digitalWrite(in3, LOW);
      digitalWrite(in4, LOW);
    }

    // Rotate / Special Movement
    else if (inputvalue == 'A') {
      digitalWrite(in1, HIGH);
      digitalWrite(in2, LOW);
      digitalWrite(in3, LOW);
      digitalWrite(in4, HIGH);
    }

    // Stop all motors
    else if (inputvalue == 'S') {
      digitalWrite(in1, LOW);
      digitalWrite(in2, LOW);
      digitalWrite(in3, LOW);
      digitalWrite(in4, LOW);
    }
  }
}
