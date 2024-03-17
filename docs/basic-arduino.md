

As an Electrical and Electronic Engineering student, I have always found the world of electronics to be captivating. 
I have dedicated myself to cultivating proficiency in both programming and hardware integration,using  Arduino and ESP8266/ESP32 microcontrollers.
### **1. Three LED Blinking Using Arduino**

To achieve the desired sequence, connect three LEDs to pins 5, 8, and 10 of the Arduino board. Then, sequentially turn on each LED, starting with pin 5, followed by pin 8, and finally pin 10, with a delay of 1.5 seconds between each LED activation.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Y-yEaXvTZJg?si=QdTtdQ8vJif_PlaC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
void setup() {

// put your setup code here, to run once:
pinMode (5, OUTPUT);
pinMode (8,OUTPUT);
pinMode (10, OUTPUT);
}
void loop() {
// put your main code here, to run repeatedly:
digitalWrite(5, HIGH);
digitalWrite(8, LOW);
digitalWrite(10, LOW);
delay(1500);

digitalWrite(5, LOW);
digitalWrite(8, HIGH);
digitalWrite(10, LOW);
delay(1500);

digitalWrite(5, LOW);
digitalWrite(8, LOW); 
digitalWrite(10, HIGH); 
delay (1500);

digitalWrite(5, LOW);
digitalWrite(8, LOW);
digitalWrite(10, LOW);
delay(1500);
}

```

### **2. Write Your Name on LCD display Using Arduino**

Write your name on the first line of the LCD and your department name on the second line. 

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/2OtRVJWY2bY?si=whmRu_quOEKvyKkC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
#include<LiquidCrystal.h>
LiquidCrystal lcd (12,11,5,4,3,2); void setup() {
lcd.begin(16,2);
lcd.print ("Nusrat Jahan");
}
void loop() {

lcd.setCursor (0,1); 
lcd.print ("Dept. of EEE");
}

```

### **3. StopWatch using Arduino**
 
Create a clock on the LCD that counts from 0 to 60, restarting after one minute like a stopwatch.

**Implementation Video:** 

<iframe width="560" height="315" src="https://www.youtube.com/embed/R1V5hbS7TyU?si=CTzoAU4jHC5ahZKc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Code:**

```C++
#include<LiquidCrystal.h>
LiquidCrystal lcd (12,11,5,4,3,2);
void setup() {
lcd.begin(16,2);
}
void loop() {

for (int i=0;i<=60;i++)
{
lcd.print (i);
delay(1000);
lcd.clear();
}
}

```

### **4. Show LED Status on LCD Display using Arduino**

Connect an LED to pin 13 of the Arduino and display "LED is ON" on the LCD when the LED is turned on, and "LED is OFF" when the LED is turned off with a 2-second delay between each blink.

 **Implementation Video:** 

<iframe width="560" height="315" src="https://www.youtube.com/embed/8m2YmNGVnF8?si=aW4cmAsTXw-E-TAX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Code:**

```C++
#include<LiquidCrystal.h>
LiquidCrystal lcd (12,11,5,4,3,2);
void setup()
{
lcd.begin(16,2);
pinMode (6, OUTPUT);
pinMode (13, OUTPUT);
}
void loop()
{
analogWrite (6,110);
digitalWrite(13, HIGH);
lcd.setCursor (0,0);
lcd.print ("LED is ON");
delay(1500);
lcd.clear();

digitalWrite(13, LOW);
lcd.setCursor (0,1);
lcd.print ("LED is OFF");
delay(1500);
lcd.clear();
}

```

### **5. Height Measurement with Ultrasonic sensor and Arduino**

Create a cap equipped with Ultrasonic sensors capable of accurately measuring a person's height in feet and inches, allowing for precise comparison between the measured height and the actual height.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/ulgYCemmyas?si=ZDtmhB23dlKy05jO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
#include <NewPing.h>
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2); //Creates the LCD object parameter

#define TRIGGER_PIN 9
#define ECHO_PIN 10
#define MAX_DISTANCE 300 //Maximum distance we want to measure(in centimeters)

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); //NewPing setup of pins and maximum distance
//defines all variables
int distance;
int distance_ft;
int distance_in;

void setup() {
    lcd.begin(16, 2); //Intiatizes the interface to the LCD screen
    pinMode(6, OUTPUT); //set pwm pin for backlight of the LCD

    Serial.begin(115200);//starts the serial communication
}

void loop() {
    // put your main code here, to run repeatedly:
    analogWrite(6, 80);

    ultrasonic();
    lcd_print();
    delay(1000);
}

//calculate the Height by using Ultrasonic sensor
void ultrasonic() {
    delay(50);//Wait 50ms between pings (about 20 pings/sec)

    //finds the distance in feet and inches
    distance = sonar.ping_in();
    distance_ft = distance / 12;
    distance_in = distance % 12;
}

//Print the Height in the LCD display
void lcd_print() {
    lcd.setCursor(0, 0); //sets the location at which subsequent text write

    lcd.print("Height: ");
    lcd.print(distance_ft);
    lcd.print("ft ");
    lcd.print(distance_in);
    lcd.print("in");
}

```

### **6. Water Level Indicator**

Utilizing an ultrasonic sensor, design a water level detector with red LED activation for low water levels and green LED indication for full tank status,, while integrating an LCD to provide immediate feedback by displaying "Tank is full" or "Medium Amount water," and "Tank is Empty" or "Turn on Motor!" messages, ensuring accurate monitoring and control of water levels.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/QCu6mtEtcdQ?si=laTCc5i9ZVGkDvcv" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
#include <NewPing.h>
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2); //Creates the LCD object parameter

#define TRIGGER_PIN 9
#define ECHO_PIN 10
#define MAX_DISTANCE 300 //Maximum distance we want to measure (in centimeters)

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); //NewPing setup of pins and maximum distance

int distance;

void setup() {
    lcd.begin(16, 2); //Intiatizes the interface to the LCD screen
    pinMode(6, OUTPUT); // set PWM pin for backlight of the LCD
    pinMode(8, OUTPUT); // Set Arduino pin for LED
    pinMode(13, OUTPUT);

    Serial.begin(115200); // starts the serial communication
}

void loop() {
    analogWrite(6, 90); // set PWM pin's voltage for backlight of the LCD

    ultrasonic();
    lcd_print();
}

// Find the water level by using Ultrasonic sensor
void ultrasonic() {
    delay(50); // Wait 50ms between pings (about 20 pings/sec)
    distance = sonar.ping_cm(); // finds the water level in centimeter
}

// LED on and off control and Print the status of water level and Tank in the LCD display
void lcd_print() {
    // Make decision about the status of water level
    if (distance <= 2) {
        lcd.clear();
        lcd.setCursor(0, 0); // sets the location at which subsequent text write
        lcd.print("Tank is Full");
        digitalWrite(13, HIGH); // Green LED on
        digitalWrite(8, LOW);
        delay(1000);
    }
    else if (distance >= 4 && distance <= 7) {
        lcd.clear();
        lcd.setCursor(0, 0); // sets the location at which subsequent text write
        lcd.print("Medium Amount");
        lcd.setCursor(0, 1);
        lcd.print("Water");
        digitalWrite(8, LOW); // Red LED off
        digitalWrite(13, LOW); // Green LED off
        delay(1000);
    }
    else {
        lcd.clear();
        lcd.setCursor(0, 0);
        lcd.print("Tank is Empty");
        lcd.setCursor(0, 1); // sets the location at which subsequent text write
        lcd.print("Turn on Motor");
        digitalWrite(8, HIGH); // Red LED on
        digitalWrite(13, LOW);
        delay(1000);
    }
}

```

### **7. Automatic street light using LDR sensor**

Utilize a photoresistor(LDR) to accurately detect ambient light intensity, promptly initiating LED illumination upon exceeding a specific resistance threshold, and ensuring optimal control over lighting conditions by promptly deactivating the LED when the resistance surpasses the designated limit.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/G3sq4rUcDHs?si=PLQRhR8igebZ4gOe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
//Include all necessary library
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x20, 16, 2); // set the LCD address to 0x20 for a 16 chars and 2 line display

int resistance = 0; //declaring the variable that will store the value of photoresistor

void setup() {
    Serial.begin(9600); //baud rate for serial communication
    pinMode(10, OUTPUT); // assigning mode to LED pin
}

void loop() {
    resistance = analogRead(A0); //getting the value of photoresistor

    //when the value of resistance is less than 50
    if (resistance < 50) {
        Serial.println(" HIGH intensity ");
        digitalWrite(10, HIGH); //keep the LED ON
    }
    // otherwise turn the light OFF
    else {
        digitalWrite(10, LOW); // turn the LED OFF
    }
    delay(1000);
}

```


### **8. Measuring Velocity of Sound and Distance mesurement using DHT-11 and Ultrasonic Sensor**

Utilize a DHT11 or DHT22 sensor to measure temperature and humidity, then calculate the velocity of sound based on these parameters, subsequently determining the distance using an ultrasonic sensor, and display both the velocity of sound and distance on an LCD screen for monitoring purposes.

**Implementation Video:** 
   
<iframe width="560" height="315" src="https://www.youtube.com/embed/r3HDciuE11Q?si=tXngRHHr-pyIsbMy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
#include "DHT.h"
#include<Wire.h>
#include<LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x3F, 16, 2);

#define DHTPIN 8
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

int trig = 9;
int echo = 10;

long duration;
int distance;
float T;
float RH;
float velocity;

void setup() {
    pinMode(trig, OUTPUT);//Sets trigPin as an output
    pinMode(echo, INPUT);//sets echoPin as an input

    dht.begin();

    lcd.init(); //initialize the I2C_lcd display
    lcd.backlight(); //use the backlight of lcd display

    Serial.begin(9600);//starts the serial communication
}

void loop() {
    dht_speed();
    ultrasonic();
    lcd_print();
}

void dht_speed() {
    RH = dht.readHumidity();//Gets temperature value
    T = dht.readTemperature();//Gets Humidity value

    velocity = 331.4 + (0.6 * T) + (0.0124 * RH);//Calculate the speed of sound
}

void ultrasonic() {
    //Clears the trigpin
    digitalWrite(trig, LOW);
    delayMicroseconds(2);

    //Sets the trigPin on HIGH state for 10 microseconds
    digitalWrite(trig, HIGH);
    delayMicroseconds(10);
    digitalWrite(trig, LOW);

    // Reads the echoPin, returns the sound wave travel time in microseconds
    duration = pulseIn(echo, HIGH);

    //calculating the distance using velocity and duration
    distance = (velocity * 0.0001 * duration) / 2;
    delay(100);
}

void lcd_print() {
    //show velocity in m/s on LCD in first line
    lcd.setCursor(0, 0); //sets the location at which subsequent text write
    lcd.print("Velocity:");
    lcd.print(int(velocity));
    lcd.setCursor(13, 0);
    lcd.print("m/s");

    //show distance in cm on LCD in second line
    lcd.setCursor(0, 1);
    lcd.print("Distance: ");
    lcd.print(distance);
    lcd.setCursor(14, 1);
    lcd.print("CM");
}

```

### **9. BPM and SPO2 with PulseOximeter and Arduino**
   
Create a pulse oximeter system integrated with an LCD display, featuring prompts such as "Place your finger to Measure" when no finger is detected,,,and displaying real-time BPM and SPO2 readings when a finger is placed. 
Depending on the heart rate range, comments such as "Average Heart Rate" will be displayed in the second line of the LCD.

**Implementation Video:** 

<iframe width="560" height="315" src="https://www.youtube.com/embed/1RzdnMSoRrM?si=ifuwf51MDdAi0luW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Code:**

```C++
#include<Wire.h>  // Library for I2C communication
#include<LiquidCrystal_I2C.h>  // Library for I2C LCD
#include "MAX30100_PulseOximeter.h"  // Library for MAX30100 Pulse Oximeter sensor

LiquidCrystal_I2C lcd(0x3F, 16, 2);  // LCD object with I2C address and dimensions

PulseOximeter pox;  // Pulse Oximeter object

uint32_t last_check = 0;  // Variable to store the last check time
int Reporting_Time = 800;  // Time interval for reporting
float BPM;  // Variable to store heart rate
float SPO2;  // Variable to store blood oxygen level

void setup() {
    Serial.begin(9600);  // Initialize serial communication

    lcd.init();  // Initialize the I2C LCD display
    lcd.backlight();  // Turn on the backlight of the LCD display

    pox.begin();  // Initialize the PulseOximeter sensor
}

void loop() {
    PulseOximeter();  // Call the function to handle Pulse Oximeter readings
}

void PulseOximeter() {
    pox.update();  // Update Pulse Oximeter readings

    if (millis() - last_check > Reporting_Time) {
        BPM = pox.getHeartRate();  // Get the heart rate
        SPO2 = pox.getSpO2();  // Get the blood oxygen level

        if (BPM == 0 && SPO2 == 0) {  // If no valid readings
            lcd.clear();
            lcd.setCursor(0, 0);
            lcd.print("Place Finger");  // Prompt to place finger
        } else {  // Display heart rate and blood oxygen level
            lcd.clear();
            lcd.setCursor(0, 0);
            lcd.print("BPM:");
            lcd.print(int(BPM));  // Display heart rate
            lcd.setCursor(7, 0);
            lcd.print(" SPO2:");
            lcd.print(int(SPO2));  // Display blood oxygen level
        }
        lcd_print();  // Print the condition of heart rate
        last_check = millis();  // Update last check time
    }
}

// Check and print the condition of heart rate
void lcd_print() {
    // Conditions for heart rate classification
    if (BPM >= 61 && BPM <= 65) {
        lcd.setCursor(0, 1);
        lcd.print("Excellent Heart Rate");
    } else if (BPM >= 66 && BPM <= 69) {
        lcd.setCursor(0, 1);
        lcd.print("Good Heart Rate");
    } else if (BPM >= 70 && BPM <= 73) {
        lcd.setCursor(0, 1);
        lcd.print("Above Average");
    } else if (BPM >= 74 && BPM <= 78) {
        lcd.setCursor(0, 1);
        lcd.print("Average Heart Rate");
    } else if (BPM >= 79 && BPM <= 84) {
        lcd.setCursor(0, 1);
        lcd.print("Below Average");
    } else if (BPM >= 85) {
        lcd.setCursor(0, 1);
        lcd.print("Poor Heart Rate");
    }
}

```


### **10. Proteus Simulation for Automatic Street Light**

**Simulation Video using Arduino:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/EzdpMeve7j4?si=Ob6bva-PyS6N_UAm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Simulation Video using Atmega328p Microcontroller:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/SpFPMF2f60U?si=Brco_06QG2IlTOpf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
#include <Wire.h>  // Library for I2C communication
#include <LiquidCrystal_I2C.h>  // Library for I2C LCD

LiquidCrystal_I2C lcd(0x20, 16, 2); // set the LCD address to 0x20 for a 16 chars and 2 line display

int resistance = 0; // declaring the variable that will store the value of photoresistor

void setup() {
    lcd.init(); // initialize the lcd
    lcd.backlight();

    pinMode(10, OUTPUT); // assigning mode to LED pin
}

void loop() {
    resistance = analogRead(A0); // getting the value of photoresistor

    lcd.clear();
    // when the value of resistance is less than 341
    if (resistance > 1 && resistance <= 341) {
        digitalWrite(10, LOW); // keep the LED OFF
        lcd.print("Day Time");
        lcd.setCursor(0, 1);
        lcd.print("Light Off");
    }
    // otherwise turn the light OFF
    else {
        digitalWrite(10, HIGH); // turn the LED ON

        lcd.print("Now Night");
        lcd.setCursor(0, 1);
        lcd.print("Light On");
    }
    delay(800);
}

```

### **11. Automatic Dino Game with Servo motor and Arduino**

Develop an automatic dino game system where a black cactus is detected by a light-dependent resistor (LDR).
Prompt a servo motor to rotate between 30-50° to simulate hitting the space bar on the keyboard,,followed by a reverse rotation to return to its initial position for seamless gameplay.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/BZay714EkuM?si=d7wqBQUJ5QCrGF9v" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Code:**

```C++
#include <Servo.h>

Servo myservo; // create servo object to control a servo

int pos = 0; // variable to store the servo position
int ldr;

void setup() {
    myservo.attach(9); // attaches the servo on pin 9 to the servo object
    Serial.begin(9600);
}

void loop() {
    ldr = analogRead(A0); // find the resistance value by LDR
    delay(8);

    if (ldr < 20) {
        // goes from 30 degrees to 50 degrees
        myservo.write(30); // tell servo to go to position in variable 'pos'
        delay(100); // waits 100ms for the servo to reach the position
        myservo.write(50); // tell servo to go to position in variable 'pos'
        delay(100);

        // goes from 50 degrees to 30 degrees
        myservo.write(30); // tell servo to go to position in variable 'pos'
        delay(50); // waits 50ms for the servo to reach the position
    }
}

```


### **12. 1-Proteus Simulation for Motor Speed Control**

Operate the DC motor in forward motion for 5 seconds before reversing its direction for 3 seconds, while simultaneously incrementing the motor speed gradually from 0 to its maximum. Employ an LCD to continuously exhibit the percentage of speed for both motors.

**Simulation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/P773e0EoZeA?si=ghY2iTBmHo7gpBYG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
   
**Code:**

```C++
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x20, 16, 2); // set the LCD address to 0x20 for a 16 chars and 2 line display

// Motor A connections
int enA = 9;
int in1 = 8;
int in2 = 7;
// Motor B connections
int enB = 3;
int in3 = 5;
int in4 = 4;

int pwm_A;
int pwm_B;
float speed_lcd;

void setup() {
    lcd.init(); // initialize the lcd
    lcd.backlight();

    pinMode(enA, OUTPUT);
    pinMode(enB, OUTPUT);
    pinMode(in1, OUTPUT);
    pinMode(in2, OUTPUT);
    pinMode(in3, OUTPUT);
    pinMode(in4, OUTPUT);

    // Turn off Motors- Initial state
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
    digitalWrite(in3, LOW);
    digitalWrite(in4, LOW);
}

void loop() {
    lcd_print();
    directionControl();
    delay(400);
    speedControl();
    delay(400);
}

void lcd_print() {
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Speed A: ");
    lcd.setCursor(15, 0);
    lcd.print("%");
    lcd.setCursor(0, 1);
    lcd.print("Speed B: ");
    lcd.setCursor(15, 1);
    lcd.print("%");
}

// This function lets you control spinning direction of motors
void directionControl() {
    // Set motors to different speed
    pwm_A = 255;
    pwm_B = 220;
    analogWrite(enA, pwm_A);
    analogWrite(enB, pwm_B);

    lcd.setCursor(9, 0);
    speed_percen(pwm_A);
    lcd.setCursor(9, 1);
    speed_percen(pwm_B);

    // Turn on and rotate clockwise direction for 5 sec for motor A
    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);

    // Turn on Motor B
    digitalWrite(in3, HIGH);
    digitalWrite(in4, LOW);
    delay(5000);

    // Now change motor directions and rotate for 3 seconds
    digitalWrite(in1, LOW);
    digitalWrite(in2, HIGH);

    // Motor B
    digitalWrite(in3, LOW);
    digitalWrite(in4, HIGH);
    delay(3000);

    // Turn off motors
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
    digitalWrite(in3, LOW);
    digitalWrite(in4, LOW);
}

// This function lets you find the percentage of speed
void speed_percen(int value) {
    // Calculate percentage of speed
    speed_lcd = 0.3922 * value;
    lcd.print(speed_lcd);
}

// This function lets you control speed of the motors
void speedControl() {
    // Turn on motors
    // Motor A
    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);

    // Motor B
    digitalWrite(in3, HIGH);
    digitalWrite(in4, LOW);

    // Accelerate from Zero to maximum speed
    for (int i = 0; i < 256; i++) {
        analogWrite(enA, i);
        analogWrite(enB, i);

        lcd.setCursor(9, 0);
        speed_percen(i);
        lcd.setCursor(9, 1);
        speed_percen(i);
        delay(5);
    }

    // Decelerate from maximum speed to zero
    for (int j = 255; j >= 0; j--) {
        analogWrite(enA, j);
        analogWrite(enB, j);

        lcd.setCursor(9, 0);
        speed_percen(j);
        lcd.setCursor(9, 1);
        speed_percen(j);
        delay(5);
    }

    // Turn off motors
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
    digitalWrite(in3, LOW);
    digitalWrite(in4, LOW);
}

```
### **12. 2-Motor Speed Control**

**Implementation Video:** 

<iframe width="560" height="315" src="https://www.youtube.com/embed/WDMYkpExvtU?si=rpnZJEMpzpUcQotQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
 
**Code:**

```C++
// Include all necessary library
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Set the LCD address to 0x3F for a 16 chars and 2 line display
LiquidCrystal_I2C lcd(0x3F, 16, 2);

// Motor A connections
int enA = 9;
int in1 = 8;
int in2 = 7;

int pwm_A;
float speed_lcd;

void setup() {
    lcd.init(); // Initialize the lcd
    lcd.backlight();

    pinMode(enA, OUTPUT);
    pinMode(in1, OUTPUT);
    pinMode(in2, OUTPUT);

    // Turn off Motors- Initial state
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
}

void loop() {
    lcd_print();
    directionControl();
    delay(1000);
    speedControl();
    delay(1000);
}

void lcd_print() {
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Speed A: ");
    lcd.setCursor(15, 0);
    lcd.print("%");
}

// This function lets you control spinning direction of motors
void directionControl() {
    // Set motors to different speed
    pwm_A = 255;

    analogWrite(enA, pwm_A);

    lcd.setCursor(9, 0);
    speed_percen(pwm_A);

    // Turn on and rotate clockwise direction for 5 sec for motor A
    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);
    delay(5000);

    // Now change motor directions and rotate for 3 seconds
    digitalWrite(in1, LOW);
    digitalWrite(in2, HIGH);
    delay(3000);

    // Turn off motors
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
}

// This function lets you find the percentage of speed
void speed_percen(int value) {
    // Calculate percentage of speed
    speed_lcd = 0.3922 * value;
    lcd.print(speed_lcd);
}

// This function lets you control speed of the motors
void speedControl() {
    // Turn on motors
    // Motor A
    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);

    // Accelerate from Zero to maximum speed
    for (int i = 0; i < 256; i++) {
        analogWrite(enA, i);
        lcd.setCursor(9, 0);
        speed_percen(i);
        delay(90);
    }

    // Decelerate from maximum speed to zero
    for (int j = 255; j >= 0; j--) {
        analogWrite(enA, j);
        lcd.setCursor(9, 0);
        speed_percen(j);
        delay(50);
    }

    // Turn off motors
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
}

```

   
### **13. Three LED control with ESP8266 and  'Blynk IoT' server.**

Utilize an ESP8266 or ESP32 microcontroller to manage the blinking of three LEDs via the Blynk IoT server,, while updating an LCD display to reflect the real-time status of each LED, showing "LED 1 ON" when the first LED is activated and accurately reflecting the state changes of the remaining LEDs.

**Implementation Video:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/eWhTrznRwS0?si=w8b9BZjtqMNJZiT-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Code:**

```C++
// Include all necessary library
// for i2c_LCD
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Set the LCD address to 0x3F for a 16 chars and 2 line display
LiquidCrystal_I2C lcd(0x3F, 16, 2);

#define BLYNK_TEMPLATE_ID "TMPL6bhWfwb6k"
#define BLYNK_TEMPLATE_NAME "three led control"
#define BLYNK_AUTH_TOKEN "c-_xoSIoZjRLyKxPhXBruH_iZtQbfl5m"

// Blynk Things
#include <ESP8266WiFi.h> // ESPWiFi
#include <BlynkSimpleEsp8266.h> // for Blynk

char ssid[] = "Nusrat";
char pass[] = "abc123789";

// All variables
int pinValue_1;
int pinValue_2;
int pinValue_3;

// Writing to pin D0 from V0
BLYNK_WRITE(V0) {
    pinValue_1 = param.asInt(); // Assigning incoming value from pin V0 to a variable
    digitalWrite(D0, pinValue_1);
    // Process received value
}

// Writing to pin D5 from V1
BLYNK_WRITE(V1) {
    pinValue_2 = param.asInt(); // Assigning incoming value from pin V1 to a variable
    digitalWrite(D5, pinValue_2);
    // Process received value
}

// Writing to pin D6 from V2
BLYNK_WRITE(V2) {
    pinValue_3 = param.asInt(); // Assigning incoming value from pin V2 to a variable
    digitalWrite(D6, pinValue_3);
    // Process received value
}

void setup() {
    lcd.init(); // Initialize the lcd
    lcd.backlight();

    Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
    pinMode(D0, OUTPUT);
    pinMode(D5, OUTPUT);
    pinMode(D6, OUTPUT);

    Serial.begin(9600);
}

void loop() {
    lcd.clear();
    LED_state();
    delay(500);
    Blynk.run();
}

// Print the LED state on I2C LCD display
void LED_state() {
    // Red LED state on LCD display
    if (pinValue_1 == 1) {
        lcd.setCursor(0, 0);
        lcd.print("LED 1 ON");
    } else if (pinValue_1 == 0) {
        lcd.setCursor(0, 0);
        lcd.print("LED 1 OFF");
    }

    // Green LED state on LCD display
    if (pinValue_2 == 1) {
        lcd.setCursor(11, 0);
        lcd.print("LED 2");
        lcd.setCursor(0, 1);
        lcd.print("ON");
    } else if (pinValue_2 == 0) {
        lcd.setCursor(11, 0);
        lcd.print("LED 2");
        lcd.setCursor(0, 1);
        lcd.print("OFF");
    }

    // Yellow LED state on LCD display
    if (pinValue_3 == 1) {
        lcd.setCursor(5, 1);
        lcd.print("LED 3 ON");
    } else if (pinValue_3 == 0) {
        lcd.setCursor(5, 1);
        lcd.print("LED 3 OFF");
    }
}

```



