# IOT-Enabled-Smart-Electric-Meter-

**Aim**

This project aims to create a smart electric meter through IOT technology.The aim of IoT-based smart electricity meters is to revolutionize energy management, offering real-time consumption data, remote monitoring, and improved efficiency. By enabling informed decisions, optimizing grid operations, and supporting dynamic pricing, these meters enhance conservation efforts, reduce waste, and contribute to a more sustainable and responsive energy ecosystem.

**Objectives:**

•	Real-Time Monitoring: Provide users with instantaneous visibility into their electricity consumption.

•	Remote Management: Enable users, utility companies, or administrators to access and manage the meter remotely for efficient monitoring and control.

•	Energy Efficiency: Foster energy-conscious behaviour by offering insights to identify and address energy-intensive appliances or behaviours.

•	Automation and Control: Integrate with smart home systems to automate energy-consuming devices based on real-time data.

•	Data Analytics: Facilitate data-driven decision-making by offering detailed insights into energy usage patterns for optimization and efficiency.

•	Grid Optimization: Facilitate real-time monitoring for utilities to optimize grid operations, enhance reliability, and reduce peak loads.

•	Cost Savings: Improve billing accuracy, reduce operational costs, and support dynamic pricing models for cost-effective energy management.

•	User Empowerment: Provide consumers with insights into their energy consumption, fostering awareness and enabling proactive energy-saving measures.

•	Sustainability: Contribute to a more sustainable energy ecosystem by promoting responsible consumption and reducing environmental impact.

•	Technological Innovation: Foster ongoing technological advancements, ensuring adaptability, and promoting the continuous improvement of smart metering.

**Features**

Electronic energy meters, also known as smart meters, incorporate a range of features that enhance their functionality and utility in measuring electrical energy consumption. These meters typically boast a digital display for clear and precise readings, offering high accuracy in measuring energy usage with class ratings indicating their level of precision. Equipped with communication interfaces like RS-485 or Modbus, these meters enable remote reading and monitoring, reducing the need for physical inspections and facilitating efficient data collection. Advanced meters may support bi-directional measurement, accommodating scenarios where energy generation, such as from solar panels, needs to be tracked. Data logging capabilities, including load profile recording, allow for the analysis of consumption patterns over time, aiding in optimization. Tamper detection features are often included to ensure the integrity of measurements and alert authorities to any attempts at manipulation. Smart meters can also measure power factor, demand, and peak usage, providing valuable insights for both consumers and utilities. With compatibility for renewable energy sources and modular designs for easy upgrades, electronic energy meters play a crucial role in modern energy management systems, offering accurate and actionable data to promote efficient and sustainable energy usage.

**Mind Mapping**

![SMARTTTT (1)](https://github.com/SachithaCD2003/IoT-based-energy-meter/assets/149662267/4a66ad12-6fc3-4fbe-84c6-8bc7e6e7a3df)

**Working**

Smart energy meters operate through a sophisticated process that integrates advanced technology for precise measurement, real-time data collection, and secure communication. These meters employ solid-state electronics to accurately measure electrical energy consumption on an ongoing basis. The collected data, recorded in kilowatt-hours (kWh), is stored within the meter at frequent intervals. Equipped with communication modules, such as Zigbee, Wi-Fi, or cellular networks, smart meters facilitate the seamless transmission of this data to central systems.

Communication protocols, tailored to the specific needs of the meter and the utility infrastructure, ensure the efficient and secure transfer of energy consumption information. The central systems, typically managed by utility companies or third-party service providers, receive and process this data. This centralized hub serves as a nerve center for monitoring and control, allowing utility companies to remotely analyze consumption patterns, identify anomalies, and address issues without the need for physical access to the meters.

Consumers gain access to their real-time energy consumption data through user-friendly interfaces like web portals or mobile applications. This direct access empowers individuals to make informed decisions about their energy usage, fostering a culture of energy efficiency and conservation.

Moreover, smart meters play a pivotal role in billing accuracy by eliminating the reliance on estimated readings. Utility companies can generate bills based on actual consumption data, promoting fairness and transparency in billing practices. The two-way communication feature in many smart meters further enhances their functionality, enabling utilities to send signals to the meters for tasks such as remote service disconnection or reconnection. This capability also facilitates the implementation of demand response programs, contributing to grid stability and efficiency.

In essence, the detailed working of smart energy meters involves a seamless orchestration of measurement precision, real-time data collection, secure communication, remote monitoring, consumer engagement, and advanced features like two-way communication. This holistic approach to energy management positions smart meters as integral components in the modernization and optimization of electrical grid systems.

**Flow Chart**

![1234](https://github.com/SachithaCD2003/IoT-based-energy-meter/assets/149662267/d85c1945-19fe-4b58-8f5e-827b5a03fee3)

**Algorithm**

Step1: Start.

Step2: Initialization:
Initialize necessary libraries and components (e.g., EmonLib, Blynk, WiFi).
Define constants, including Blynk template ID, template name, and Wi-Fi credentials.

Step3: Connect to Cloud:
Set up and establish a connection to the cloud platform (e.g., Blynk).
Authenticate the device with the cloud platform using a unique authentication token.

Step4: Initialize Sensors:
Set up the energy monitoring sensors (voltage and current sensors).
Calibrate sensors for accurate energy measurements.

Step5: Initialize Display:
Initialize a display module (e.g., LCD or OLED) for local information display (optional).

Step6: Initialize Data Storage:
Set up data storage mechanisms (e.g., EEPROM or other non-volatile memory) for storing critical data like total energy consumption.

Step7: Main Loop:
Enter the main loop to continuously monitor and manage the device.

Step8: Read Energy Data:
Read real-time energy consumption data from the energy monitoring sensors.
Update variables with current energy values.

Step9: Calculate and Display:
Calculate instantaneous power, total energy consumption, and other relevant metrics.
Display real-time data on a local display if available.

Step10: Send Data to Cloud:
Send energy consumption data to the cloud platform (Blynk or other IoT platform).
Update cloud-based dashboards for remote monitoring.

Step11: Smart Features:
Implement smart features such as:
Real-time notifications for high energy consumption.
Time-of-use analysis for peak and off-peak energy consumption.
Historical data analysis and reporting.
Integration with smart home systems for automation.

Step12: Data Storage and Logging:
Store critical data (e.g., total energy consumption) in non-volatile memory for persistency across power cycles.
Log historical data for analysis and reporting.

Step13: Sleep Mode (Optional):
Implement a sleep mode to conserve power during periods of inactivity.

Step14: Error Handling:
Implement error handling mechanisms to address sensor failures or communication issues.

Step15: End of Main Loop:
Repeat the main loop to continuously monitor and manage the device.

Step16: Shutdown (Optional):
Implement a shutdown procedure for graceful power-off if required.

Step 17: Stop

**Block Diagram**

![123](https://github.com/SachithaCD2003/IoT-based-energy-meter/assets/149662267/83c25b85-36dd-47de-a705-2fce1a7859a7)

**Circuit code**

#define BLYNK_TEMPLATE_ID "TMPL3BfWKkOKT"
#define BLYNK_TEMPLATE_NAME "IOT ENERGY METER"
#define BLYNK_PRINT Serial

#include "EmonLib.h"
#include <EEPROM.h>
#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>
#include <Wire.h>
#include <Adafruit_SSD1306.h>

// Adafruit_SSD1306 setup
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 32
#define OLED_RESET    -1
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// Constants for calibration
const float vCalibration = 41.5;
const float currCalibration = 0.15;

// Blynk and WiFi credentials
const char ssid[] = "Suhan276";
const char pass[] = "qwertyuiop";

// EnergyMonitor instance
EnergyMonitor emon;

// Timer for regular updates
BlynkTimer timer;

// Variables for energy calculation
float kWh = 0.0;
unsigned long lastMillis = millis();

// EEPROM addresses for each variable
const int addrVrms = 0;
const int addrIrms = 4;
const int addrPower = 8;
const int addrKWh = 12;

// Function prototypes
void sendEnergyDataToBlynk();
void readEnergyDataFromEEPROM();
void saveEnergyDataToEEPROM();

void setup() {
  Serial.begin(115200);
  Blynk.begin(auth, ssid, pass);

  // Initialize the OLED display
  if(!display.begin(SSD1306_I2C_ADDRESS, OLED_RESET)) {
    Serial.println(F("SSD1306 allocation failed"));
    for(;;);
  }
  display.display();
  delay(2000);

  // Initialize EEPROM with the size of the data to be stored
  EEPROM.begin(32); // Allocate 32 bytes for float values (4 bytes each) and some extra space

  // Read the stored energy data from EEPROM
  readEnergyDataFromEEPROM();

  // Setup voltage and current inputs
  emon.voltage(35, vCalibration, 1.7); // Voltage: input pin, calibration, phase_shift
  emon.current(34, currCalibration);    // Current: input pin, calibration

  // Setup a timer for sending data every 5 seconds
  timer.setInterval(5000L, sendEnergyDataToBlynk);

  // A small delay for system to stabilize
  delay(1000);
}

void loop() {
  Blynk.run();
  timer.run();
}

void sendEnergyDataToBlynk() {
  emon.calcVI(20, 2000); // Calculate all. No.of half wavelengths (crossings), time-out

  // Calculate energy consumed in kWh
  unsigned long currentMillis = millis();
  kWh += emon.apparentPower * (currentMillis - lastMillis) / 3600000000.0;
  lastMillis = currentMillis;

  // Print data to Serial for debugging
  Serial.printf("Vrms: %.2fV\tIrms: %.4fA\tPower: %.4fW\tkWh: %.5fkWh\n",
                emon.Vrms, emon.Irms, emon.apparentPower, kWh);

  // Save the latest values to EEPROM
  saveEnergyDataToEEPROM();

  // Send data to Blynk
  Blynk.virtualWrite(V0, emon.Vrms);
  Blynk.virtualWrite(V1, emon.Irms);
  Blynk.virtualWrite(V2, emon.apparentPower);
  Blynk.virtualWrite(V3, kWh);

  // Update the OLED display with the new values
  display.clearDisplay();
  display.setTextSize(1);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,0);
  display.print("Vrms: ");
  display.print(emon.Vrms, 2);
  display.print(" V");

  display.setCursor(0, 10);
  display.print("Irms: ");
  display.print(emon.Irms, 4);
  display.print(" A");

  display.setCursor(0, 20);
  display.print("Power: ");
  display.print(emon.apparentPower, 4);
  display.print(" W");

  display.setCursor(0, 30);
  display.print("kWh: ");
  display.print(kWh, 5);
  display.print(" kWh");

  display.display();
}

void readEnergyDataFromEEPROM() {
  // Read the stored kWh value from EEPROM
  EEPROM.get(addrKWh, kWh);

  // Check if the read value is a valid float. If not, initialize it to zero
  if (isnan(kWh)) {
    kWh = 0.0;
    saveEnergyDataToEEPROM(); // Save initialized value to EEPROM
  }
}

void saveEnergyDataToEEPROM() {
  // Write the current kWh value to EEPROM
  EEPROM.put(addrKWh, kWh);

  // Commit changes to EEPROM
  EEPROM.commit();
}
