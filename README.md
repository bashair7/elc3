# Electric Task 3 : Designing A Sensor


**there are two types of sensors:**
* Analog Sensor
* Digital Sensor

# Analog Sensor

**measure the external parameters and give an analog voltage as an output. They produce a continuous output signal or voltage which is proportional to the quantity being measured. The output voltage may be from the range of 0 to 5V. Low logic 0 (0V-3.5V) and High logic (3.5V-5V).**

![analoge](https://user-images.githubusercontent.com/81494917/183263777-ef2480ba-0992-47f1-9bb9-616a24b7cdbd.PNG)

# Component List :

* Breadboard Small
* Arduino Uno R3
* Led
* Resistor
* potentiometer
* wire
```
int ledPin = 9;
int ledVal = 0;

int potPin = A0;
int potVal = 0;

void setup()
{
  pinMode(ledPin, OUTPUT);
  pinMode(potPin, INPUT);
  
  Serial.begin(9600);
}

void loop()
{
 potVal = analogRead(potPin);
   Serial.print(potVal);
   Serial.print(", ");
   
   ledVal = map(potVal, 0, 1019, 0, 255);
   Serial.println(ledVal);
   analogWrite(ledPin, ledVal);
   
}
```






https://user-images.githubusercontent.com/81494917/183264522-590a6aad-9bee-4906-b17e-30f683cb352c.mp4



# Digital Sensor

act as electronic sensors where data is digitally converted and transmitted. Digital sensors produce discrete values (0s and 1s) or ‘binary’ signals.


![digital](https://user-images.githubusercontent.com/81494917/183263735-a0bae82d-d423-4b67-976e-ab0575f185f7.PNG)

# Component List :

* Breadboard Small
* Breadboard Mini
* Arduino Uno R3
* Led
* Resistor
* IR sensor
* IR remote
* wire

```
#include <IRremote.h>
//Define Pins
int redLed = 5;
int GrayLed = 4;
int greenLed = 3;
int blueLed = 2;
int RECV_PIN = 11;
//IR Library stuff
IRrecv irrecv(RECV_PIN);
decode_results results;


void setup()
{
  //Set Led Pins
  pinMode(redLed, OUTPUT);
  pinMode(GrayLed, OUTPUT);
  pinMode(greenLed, OUTPUT);
  pinMode(blueLed, OUTPUT);
  
  //Enable serial usage and IR signal in
  Serial.begin(9600);
  Serial.println("Enabling IRin");
  irrecv.enableIRIn(); 
  Serial.println("Enabled IRin");
}

void loop() {
  if (irrecv.decode(&results)) {//irrecv.decode(&results) returns true if anything is recieved, and stores info in varible results
    unsigned int value = results.value; //Get the value of results as an unsigned int, so we can use switch case
    Serial.println(value);
    switch (value) {
      case 2295: 
        digitalWrite(redLed, HIGH);
        delay(500);
        digitalWrite(redLed, LOW);
        break;
      
```



https://user-images.githubusercontent.com/81494917/183265223-3425a20e-af75-42e7-bad3-33de6ad0bc0a.mp4

