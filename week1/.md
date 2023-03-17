# Project 1_The Mediated Extensions of Self


## 1. Brief
Sensor: Felx Sensor<br>
Function: Collect data on the range of hand extension and visualize it<br>
Considerations: I'll set a time interval of 5 seconds at which the sensor value will be read and sent to the feed and record all the values. Also translation of the raw value into meaningful data after the recording


## 2. Process
![image](https://github.com/ychen77jojo/AC-CT2-Spring23/blob/main/week1/1.jpg?raw=true)

## 4. Code
```
#include "config.h"

#define flexPin A2

AdafruitIO_Feed *myFlexFeed = io.feed("flex_feed");

int interval = 5000;                  //equal to 10s
int prevTimestamp, currTimestamp = 0;

void setup() {
  Serial.begin(115200);

  while (! Serial);
  
  Serial.print("Connecting to Adafruit IO");
  io.connect();

  while (io.status() < AIO_CONNECTED) {
    Serial.print(".");
    delay(500);
  }

  Serial.println();
  Serial.println(io.statusText());
}

void loop() {
  io.run();

  currTimestamp = millis();

  int value = analogRead(flexPin);

  Serial.print("Readding Flex Value: ");
  Serial.println(value);
  
  if(currTimestamp % interval < prevTimestamp % interval){   //the measurment could never presicely to 0, so we need to compare
  Serial.print("Sending Flex Value: ");
  Serial.println(value);
  myFlexFeed->save(value);
  }

  prevTimestamp = currTimestamp;
  //delay(5000);
}
```

