# Create a Night Light

This is an example of using an input \(sensor\) component to change an output of an output component.

## Supplies

![](../../.gitbook/assets/image%20%28521%29.png)

![](../../.gitbook/assets/image%20%28522%29.png)

## Diagram

![](../../.gitbook/assets/image%20%28520%29.png)

The photoresistor data \(yellow\) is connected to pin A0 \(analog\) and the LED data \(orange\) is connected to pin 2 \(digital\).

## Code

This code gets the amount of light coming in via the sensor and if it's dark enough, the LED will light up.

```c
// Sensor pin is connected to pin A0 (analog) on the Arduino circuit board
int sensorPin = 0;

// LED pin is connected to pin 2 (digital)
int LEDpin = 2;

// Define variables
int lightValue;

void setup() {
  // Establish the component connection and its type (output/input)
  pinMode(sensorPin, INPUT);
  pinMode(LEDpin, OUTPUT);
  
  // Start Serial connection
  Serial.begin(9600);
}

void loop() {
  // Reads and stores the data coming in from the sensor
  lightValue = analogRead(sensorPin);

  // Lights up if dark enough
  if (lightValue <= 5) {
    digitalWrite(LEDpin, HIGH);
  }
  else {
    digitalWrite(LEDpin, LOW);
  }
  
  delay(100);

  // Sends information to the Serial Monitor
  Serial.print("Light Value: ");
  Serial.print(lightValue);
  delay(100);
}
```

