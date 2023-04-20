# Arduino Weather Station

## Introduction

Weather stations are useful for monitoring local weather conditions, whether you're a hobbyist or a professional meteorologist. In this tutorial, we'll show you how to build a basic weather station using an Arduino board, sensors, and other components. We'll also use GitHub to store and share the sensor data, making it easy to access and analyze from anywhere.

## Materials

For this project, you will need:

- Arduino Uno board
- DHT11 temperature and humidity sensor
- BMP180 barometric pressure sensor
- Anemometer and wind vane (optional)
- 16x2 LCD display
- Breadboard and jumper wires
- 9V battery or USB cable for power
- Weatherproof enclosure (optional)

## Wiring

Follow these steps to wire up your weather station:

- Connect the DHT11 sensor to the Arduino's digital pin 2.
- Connect the BMP180 sensor to the Arduino's I2C pins (A4 and A5).
- Connect the anemometer to the Arduino's digital pin 3, and the wind vane to digital pin 4.
- Connect the LCD display to the Arduino's I2C pins (A4 and A5).

Refer to the documentation for each sensor and component for more specific instructions.

## Programming

Next, you'll need to write the code to read the sensor data and display it on the LCD screen. Here's some example code to get you started:

```arduino
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <Adafruit_BMP085.h>
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);
Adafruit_BMP085 bmp;

LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  Serial.begin(9600);
  lcd.init();
  lcd.backlight();
  dht.begin();
  bmp.begin();
}

void loop() {
  float temp = dht.readTemperature();
  float humidity = dht.readHumidity();
  float pressure = bmp.readPressure() / 100.0F;
  
  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temp);
  lcd.print("C");
  
  lcd.setCursor(0, 1);
  lcd.print("Humidity: ");
  lcd.print(humidity);
  lcd.print("%");

  lcd.setCursor(9, 0);
  lcd.print("Press: ");
  lcd.print(pressure);
  lcd.print("hPa");

  Serial.print(temp);
  Serial.print(",");
  Serial.print(humidity);
  Serial.print(",");
  Serial.println(pressure);

  delay(2000);
}
```
This code reads the temperature, humidity, and pressure data from the sensors, and displays it on the LCD screen. It also sends the data to the serial monitor for debugging purposes. You can modify this code to add support for the anemometer and wind vane, as well as other features.

## Testing

To test your weather station, connect it to your computer using a USB cable and open the Arduino IDE's serial monitor. You should see the sensor data being printed to the monitor every 2 seconds. If the data looks correct, you can disconnect the weather station from your computer and test it outside.

## Deployment

To deploy your weather station outside, mount the sensors and enclosure in a suitable location, such as on a roof or pole. You may need to use longer cables to connect the sensors to the Arduino board if the sensors are located far away from the board. Once your weather station is set up, you can start collecting and analyzing weather data from your local area. You can also consider adding more sensors, such as a UV sensor or a rain gauge, to expand the functionality of your weather station. Finally, you can store the data on GitHub to share it with others or to use it for your own analysis.
