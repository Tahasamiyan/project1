#include <Wire.h>
#include <LiquidCrystal_I2C.h>


LiquidCrystal_I2C lcd(0x27, 16, 2);

const int sensor1Pin = A0;
const int sensor2Pin = A1;
const int sensor3Pin = A2;

void setup() {

  lcd.init();
  lcd.backlight();
  
  
  lcd.setCursor(0, 0);
  lcd.print("Temp Monitoring");
  delay(2000);
}

void loop() {
 
  float temp1 = analogRead(sensor1Pin) * 5.0 / 1023.0 * 100.0; 
  float temp2 = analogRead(sensor2Pin) * 5.0 / 1023.0 * 100.0;
  float temp3 = analogRead(sensor3Pin) * 5.0 / 1023.0 * 100.0;

 
  lcd.clear();

 
  lcd.setCursor(0, 0);
  lcd.print("T1:");
  lcd.print(temp1, 1);
  lcd.print("C ");

  lcd.setCursor(0, 1);
  lcd.print("T2:");
  lcd.print(temp2, 1);
  lcd.print("C T3:");
  lcd.print(temp3, 1);
  lcd.print("C");


  delay(1000);
}
