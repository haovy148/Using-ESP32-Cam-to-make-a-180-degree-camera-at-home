# Using-ESP32-Cam-to-make-a-180-degree-camera-at-home
This is an old project that I made to monitor my grandparents while I was studying far away from home. It basically uses an ESP32-CAM and a standard ESP32.

Basically you just need connect the esp32 camera to the local wifi and get photo from the telegram bot. Shout out to this youtuber for making the tutorial. https://m.youtube.com/watch?v=D0mCmRcsd7w&pp=ygUSZXNwMzIgY2FtIHRlbGVncmFt

And to rotate the esp32 cam, u just need to connect a esp32 to a servo using Blynk App. You can do this by youtube or chatgpt to guide.




https://github.com/user-attachments/assets/f748e2cf-ea06-4e74-8a94-9f13b33634c6























#include <WiFi.h>
#include <BlynkSimpleEsp32.h>
#include <Servo.h>

// Blynk Auth Token
char auth[] = "Your_Blynk_Auth_Token";

// Wi-Fi credentials
char ssid[] = "Your_WiFi_SSID";
char pass[] = "Your_WiFi_Password";

Servo myServo;   // Create servo object
int servoPin = 23;

BLYNK_WRITE(V1) {
  int angle = param.asInt();   // Get slider value from Blynk
  myServo.write(angle);        // Move servo to angle
}

void setup() {
  Serial.begin(115200);
  myServo.attach(servoPin);    // Attach servo
  Blynk.begin(auth, ssid, pass);
}

void loop() {
  Blynk.run();
}

