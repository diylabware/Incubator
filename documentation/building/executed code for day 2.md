/*
  Analog Input
  Demonstrates analog input by reading an analog sensor on analog pin 0 and
  turning on and off a light emitting diode(LED) connected to digital pin 13.
  The amount of time the LED will be on and off depends on the value obtained
  by analogRead().
  The circuit:
  - potentiometer
    center pin of the potentiometer to the analog input 0
    one side pin (either one) to ground
    the other side pin to +5V
  - LED
    anode (long leg) attached to digital output 13
    cathode (short leg) attached to ground
  - Note: because most Arduinos have a built-in LED attached to pin 13 on the
    board, the LED is optional.
  created by David Cuartielles
  modified 30 Aug 2011
  By Tom Igoe
  This example code is in the public domain.
  http://www.arduino.cc/en/Tutorial/AnalogInput
*/
int sensorPin = A0;    // select the input pin for the potentiometer
int ledPin = 2;      // select the pin for the LED
int ledPid = 4;      // select the pin for the LED
int ledPiv = 6;      // select the pin for the LED
float sensorValue = 0;  // variable to store the value coming from the sensor
void setup() {
  // declare the ledPin, ledpid and ledpiv as OUTPUTS:
  pinMode(ledPin, OUTPUT);
  pinMode(ledPid, OUTPUT);
  pinMode(ledPiv, OUTPUT);
  pinMode(sensorPin, INPUT);
  Serial.begin(9600);
}
void loop() {
  // read the value from the sensor:
  Serial.println(sensorValue);
  sensorValue = analogRead(sensorPin);
  // check if the sensor value < 342. If it is, the ledpin is LOW, ledpid is LOW, ledpiv is LOW:
  if (sensorValue <10) {
  // turn the ledPin on
  digitalWrite(ledPin,LOW);
  // turn the ledPid on
  digitalWrite(ledPid, LOW);
  // turn the ledPiv on
  digitalWrite(ledPiv, LOW);
  }
  // check if the sensor value < 342. If it is, the ledpin is HIGH, ledpid is LOW, ledpiv is LOW:
  if ((sensorValue <342)&&(sensorValue >10)) {
  // turn the ledPin on
  digitalWrite(ledPin,HIGH);
  // turn the ledPid on
  digitalWrite(ledPid, LOW);
  // turn the ledPiv on
  digitalWrite(ledPiv, LOW);
  }
   // check if the sensor value < 683. If it is, the ledpin is HIGH, ledpid is HIGH, ledpiv is LOW:
  if ((sensorValue <683)&&(sensorValue >342)) {
  // turn the ledPin on
  digitalWrite(ledPin,HIGH);
  // turn the ledPid on
  digitalWrite(ledPid, HIGH);
  // turn the ledPiv on
  digitalWrite(ledPiv, LOW);
  }
  // check if the sensor value < 1023. If it is, the ledpin is HIGH, ledpid is HIGH, ledpiv is HIGH:
  if ((sensorValue < 1023)&&(sensorValue > 683)) {
  // turn the ledPin on
  digitalWrite(ledPin,HIGH);
  // turn the ledPid on
  digitalWrite(ledPid, HIGH);
  // turn the ledPiv on
  digitalWrite(ledPiv, HIGH);
  }
  
  // stop the program for <sensorValue> milliseconds:
  //delay(sensorValue);
  // turn the ledPin off:
 // digitalWrite(ledPin, LOW);
  // stop the program for for <sensorValue> milliseconds:
  //delay(sensorValue);
}
