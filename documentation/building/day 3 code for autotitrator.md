int resetPin=3;// Assign pin 3 to the reset button
int colourPin= A2; //assign A2 as colour sensor pin
int tapPin = 1; //assign pin 1 tap pin 
int beepPin = 2;//assign pin 2 as beep as beep pin
int const flowRate = 2; //set flow rate to 2 mls/second
float colourValue;// defined as reading from colourPin
long startTime;//time titration begins
long endTime;//time titration ends
double endPointVolume;//storess calculated endpoint volume
String finalVolume;// converts double to string variables


void setup() {
pinMode (tapPin, OUTPUT); //open tap
pinMode (beepPin, OUTPUT);//turn buzzer on
pinMode (colourPin, INPUT);//read A2
Serial.begin(9600);//iniatialize serial monitor
pinMode(resetPin,INPUT);
}

void loop() {
digitalWrite (tapPin, HIGH); //open the tap
startTime = millis(); //record the startTime

colourValue = analogRead(colourPin); //read values on colourpin 

while (colourValue !=5) {
  colourValue = analogRead(colourPin);//continue analogue reading 
}

endTime = millis(); //record the endTime}
digitalWrite(tapPin, LOW);//close tap

endPointVolume=(((endTime-startTime)/1000)*flowRate);// calculate
finalVolume=String (endPointVolume);//convert double endpoint volume value to string
Serial.println(finalVolume);//print final volume

digitalWrite(beepPin, HIGH);//indicate end of process
while (resetPin==LOW) {
  digitalWrite(beepPin, HIGH);

  }
  digitalWrite(beepPin, LOW);
}
