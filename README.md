#include <DHT.h>

#define DHTPIN ___ //ขา Pin ที่ต่อ DHT22
#define DHT_TYPE DHT22

DHT dht(DHTPIN, DHT_TYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  delay(2000); 

  float humi = dht.readHumidity();
  float temp = dht.readTemperature();

  if (isnan(humi) || isnan(temp)) {
    Serial.println("Failed to read from DHT22 sensor");
    return;
  }

  Serial.print("Temperature: ");
  Serial.print(___, 1); //ตัวแปร เก็บค่าอุณหภูมิ
  
  Serial.print(" C, Humidity: ");
  Serial.print(___, 1); //ตัวแปร เก็บค่าความชื้น
  Serial.println(" %");
}
