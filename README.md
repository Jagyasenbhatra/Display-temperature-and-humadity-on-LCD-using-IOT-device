# To interface 16 x 2 LCD  with  Arduino/Respberry pi and write a program to print the Temperature and Humadity on LCD 

## Device Required
1. Arduino Uno
2. Bread Board
3. Jumper Wires
4. DHT11 Sensor 
5. 16 x 2 LCD 
6. Potentiometer  
   
**Arduino IDE** : [Downlaod](https://www.arduino.cc/en/software)


## Connection
- Circuit Connection
   - LCD display Arduino
      - Vss = Arduino
      - VDD = Arduino
      - V0 = Potentiometer center pin
      - RS = Digital pin 3
      - RW = Arduino Ground
      - E = Digital pin 4
      - D4 = Arduino digital pin 5
      - D5 = Arduino digital pin 6
      - D6 = Arduino digital pin 7
      - D7 = Arduino digital pin 8
      - A = Arduino 5V
      - K = Arduino GND
   - DH11 to Arduino
      - VCC = Arduino 5V
      - GND Arduino GND
      - OUT = Arduino A0
   - Potentiometer
      - left = Arduino 5V
      - Right = Arduino GND
      - Center = LCD V0
  
  


   
## Program
```cpp

#include <LiquidCrystal.h>
#include <DHT.h>

// Initialize the LCD
LiquidCrystal lcd(3, 4, 5, 6, 7, 8);

// Initialize the DHT sensor
#define DHTPIN A0
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

void setup() {
  lcd.begin(16, 2); // Initialize the LCD with 16 columns and 2 rows
  dht.begin();      // Initialize the DHT sensor
}

void loop() {
  // Read temperature and humidity from the DHT sensor
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  // Display temperature and humidity on the LCD
  lcd.clear();
  lcd.print("Temp: ");
  lcd.print(temperature);
  lcd.print((char)223); // Degree symbol
  lcd.print("C");

  lcd.setCursor(0, 1);
  lcd.print("Humidity: ");
  lcd.print(humidity);
  lcd.print("%");

  delay(2000); // Wait for 2 seconds before updating readings
}




```


# Screenshots

![fig](/exp1.jpg)
**fig-1**
![fig](/exp92.jpg)
**fig-2**
