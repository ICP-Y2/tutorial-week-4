# Tutorial-week-4

**For this tutorial**, 
`Simulate the following system with the specified resources as per the given circuit diagram and the source code in TinkerCad.`,
you will be working with the following simulation and make some observations in the simulation. So, your task is to provide answers to `What are the observations you have made in the simulation?` and `What is your conclusion from the observations made in the simulation?`

## 1.	Simulate the discrete Input/Sensor and Output/Actuator
> Resources Required
-	Arduino UNO
-	LED
-	Button
-	Resistors `330 ohm` for Led and `1 Kohm` for button

 <figure>
   <img width="498" height="496" alt="image" src="https://github.com/user-attachments/assets/a25c0376-e176-4943-b08a-d33e0f583680" /></br>
  <figcaption>Fig 1: Simulation Circuit Diagram: Discrete Input/Sensor and Output/Actuator</figcaption>
 </figure>

> ### Steps
> #### 1. Find and the required components from the resources tab in tinker cad (right of the screen)
> #### 2. Connect the LED (Output/Actuator)
>  - Connect the **LONG LEG (anode)** to ``digital pin number 8``
>  - Connect the **SHORT LEG (cathode)** to ground `GND` of led in the arduino. Make sure to use the resistor in led (Cathode).
> #### 3. Connect the Push Button (Input/Sensor)
> - Place the push button on the breadboard (across the middle gap).
> - Connect one leg of the button to **5V** on the Arduino.
> - Connect the opposite leg to **digital pin 2** on Arduino.
> - Connect that same leg (the one going to pin 7) to **GND** through a **1kΩ resistor** (pull-down resistor).
#### Write the Arduino Code
Click on **“Code” → “Text”** mode and enter the following code:

```
int ledPin = 8; // LED connected to digital pin 8
int buttonPin = 7; // push button connected to digital pin 7
int buttonState = 0; // to store the read value

void setup() {
  pinMode(ledPin, OUTPUT); // sets the digital pin 8 as output
  pinMode(buttonPin, INPUT); // sets the digital pin  as input
}

void loop() {
  buttonState = digitalRead(buttonPin); // read the input pin
  if (buttonState == HIGH) {
    digitalWrite(ledPin, HIGH); // sets the LED to the button's value
  } else {
    digitalWrite(ledPin, LOW); // sets the LED to the buttons' value
  }
}
```
**`Submit the simulation video`**

**Learning Reflection 1**
```


```

## 2.	Simulate Ultrasonic Sensor with Arduino
> Resources Required
-	Arduino UNO
-	LED
-	Ultrasonic Sensor (HC-SR04)
-	Resistors `220 ohm`
-	M-M Jumper Wires

 <figure>
  <img width="947" height="457" alt="image" src="https://github.com/user-attachments/assets/f3fac4e2-aa6d-49f8-8b9c-71633c165258" /></br>
  <figcaption>Fig 2: Simulation Circuit Diagram: Ultrasonic Sensor with Arduino</figcaption>
 </figure>
 
> ### Steps
> #### 1. Find and the required components from the resources tab in tinker cad (right of the screen)
> #### 2. Connect the Ultrasonic Sensor (HC-SR04)
> - **VCC** → **5V** on Arduino  
> - **GND** → **GND** on Arduino  
> - **Trig** → **Digital Pin 9**  
> - **Echo** → **Digital Pin 10**
> #### 3. Connect the LED (Output Indicator)
> - Place the LED on the breadboard.  
> - Connect the **short leg (cathode)** to **GND** on Arduino.  
> - Connect the **long leg (anode)** to **digital pin 13** through a **220Ω resistor**.
#### Write the Arduino Code
Click on **“Code” → “Text”** mode and enter the following code:

```
int trigPin = 9; // trig pin of ultrasonic sensor
int echoPin = 10; // echo pin of ultrasonic sensor
int ledPin = 13; // LED pin
long duration; // variable to store time duration of ultrasonic wave to transmit and receive sound
int distance; // variable to store the distance after calculation

void setup() {
// put your setup code here, to run once
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600); // initialize the serial monitor
}

void loop() {
  // put your main code here, to run repeatedly
  // Send ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Read echo time
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate distance in cm
  distance = duration * 0.034 / 2; // formula to convert the ultrasonic time into centimeters
  
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  // Turn on LED if object is close
  if (distance < 10) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
  
  delay(500);
}
```
**`Submit the simulation video`**

**Learning Reflection 2**
```


```
