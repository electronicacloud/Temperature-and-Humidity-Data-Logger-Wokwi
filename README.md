# Temperature-and-Humidity-Data-Logger-Wokwi simulation
This project simulates a Temperature & Humidity Data Logger using an Arduino UNO and a DHT22 sensor on Wokwi (online simulator).
The Arduino reads temperature and humidity every 2 seconds and prints the results in CSV format, which can be exported and analyzed in Excel, Python, or MATLAB.

Click below to view or run the simulation:

https://wokwi.com/projects/449297698215384065

Code used:

#include <DHT.h>  //include  the DHT library

#define DHTPIN 7   //the datapin of DHT22 is connected to arduino digital pin2

#define DHTTYPE DHT22

DHT dht(DHTPIN , DHTTYPE);  //create a DHT sensor object named dht

float hum;   

float temp;

unsigned long int currentTime;

void setup() {

  // put your setup code here, to run once:
  
Serial.begin(9600);

dht.begin();  //initialize communication with DHT22

Serial.println("Time,Temperature,Humidity");

}

void loop() {

  // put your main code here, to run repeatedly:
  
hum = dht.readHumidity();

temp = dht.readTemperature();

if (isnan(hum) || isnan(temp)) {

    Serial.println("Error reading sensor data!");
    
    return;}
    
currentTime = millis() / 1000;

Serial.print(currentTime);

Serial.print(" , ");

Serial.print(temp);

Serial.print(" C, ");

Serial.print(hum);

Serial.println(" %");

delay(2000);

}

PROJECT FILES:

Temperature and Humidity Data Logger (Arduino + DHT22) Copy (2).zip – Contains all Wokwi simulation files, including the Arduino sketch and circuit configuration.

data.csv – Sample temperature and humidity output in CSV format.
