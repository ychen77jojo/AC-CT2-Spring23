# Build for Play

## Name
Spaceship Dodge Obstacle Game

## Final Video
https://youtube.com/shorts/YDEFOoxriwY

## Instructions
- In this project, the player to overhead view to control a spacecraft in interstellar space adventure, the player needs to control the ship to dodge the various meteorites that constantly appear in front of them, to avoid collisions and make the ship explode.
- Players can control the protagonist's forward, backward, left and right movement through buttons.

## Game Interface
![interface](https://github.com/ychen77jojo/AC-CT2-Spring23/blob/main/Build%20for%20play/Interface.jpg?raw=true)

## ESP32

### Connection
![controller](https://github.com/ychen77jojo/AC-CT2-Spring23/blob/main/Build%20for%20play/ESP32.jpg?raw=true)

### ESP Code
```
#define BUTTON1 12
#define BUTTON2 27
#define BUTTON3 33
#define BUTTON4 15

void setup() {
  pinMode(BUTTON1,INPUT);
  pinMode(BUTTON2,INPUT);
  pinMode(BUTTON3,INPUT);
  pinMode(BUTTON4,INPUT);
  
  Serial.begin(115200);
  while (! Serial);

}

void loop() {
   Serial.print(digitalRead(BUTTON1));
   Serial.print(',');
   Serial.print(digitalRead(BUTTON2));
   Serial.print(',');
   Serial.print(digitalRead(BUTTON3));
   Serial.print(',');
   Serial.println(digitalRead(BUTTON4));

   delay(50);


}
```
## Reflection
This unity homework let me know that all Assets should have only one unique version, when unity3d encounter the sudden death of unsaved scenes, you can find the Temp folder in the project file directory, double-click the folder, find the -Backupscenes folder, change the file suffix to unity. Then drag it into the project interface of unity3d, so that you can restore the last situation of the scene before the crash.

