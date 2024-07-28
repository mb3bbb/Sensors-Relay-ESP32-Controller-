//Step 1 Libraries and Pin Definitions.
#include <WiFi.h>
#define LIGHT_SENSOR_PIN  35  // ESP32 pin GPIO36 (ADC0) connected to light sensor
#define LED_PIN           22  // ESP32 pin GPIO22 connected to LED
#define ANALOG_THRESHOLD  1000
const char* ssid = "Murtadha";
const char* password = "012345678";
const int relayPin = T4; // Pin connected to the relay module
const int motionSensorPin = T4; // Pin connected to the motion sensor

//Step 2 The setup() function initializes the pins, starts the Serial monitor, and connects the ESP32 to the Wi-Fi network.
void setup() {
  pinMode(LED_PIN, OUTPUT); // set ESP32 pin to output mode
  Serial.begin(115200);
  pinMode(relayPin, OUTPUT);
  pinMode(motionSensorPin, INPUT);
  
//Step 3 Processing Wi-Fi Connection.
  Serial.println();
  Serial.println("Connecting to WiFi");
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  
  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

 //Step 4 Setting Loop Function for LDR And Motion Sensor
void loop() {

  int analogValue = analogRead(LIGHT_SENSOR_PIN); // read the value on analog pin
  if (analogValue > ANALOG_THRESHOLD)
    digitalWrite(LED_PIN, LOW); // turn off LED
  else
    digitalWrite(LED_PIN, LOW);  // turn off LED

  bool motionDetected = digitalRead(motionSensorPin);
  if (motionDetected) {
    // Turn on the relay to activate home automation
    digitalWrite(relayPin, HIGH);
    Serial.println("Motion detected! Turning on lights.");
    delay(5000); // Simulate lights being on for 5 seconds
    digitalWrite(relayPin, LOW);
    Serial.println("Lights turned off.");
  }
  
  delay(1000); // Check for motion every second
}
