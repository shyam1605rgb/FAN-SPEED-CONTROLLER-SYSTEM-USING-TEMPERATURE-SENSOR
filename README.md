

# FAN-SPEED-CONTROLLER-SYSTEM-USING-TEMPERATURE-SENSOR
# EXP 1(A) FAN SPEED CONTROLLER SYSTEM USING TEMPERATURE SENSOR


# Aim:
	To measure the Temperature using DHT11/DHT22/TMP36  sensor with Arduino UNO Board/ESP-32 using Tinker CAD.

# Hardware / Software Tools required:
	PC/ Laptop with Internet connection
    Tinker CAD tool (Online)
	Arduino UNO Board/ESP-32
	Temperature Sensor (DHT11/DHT22/TMP36)

# Circuit Diagram:

---
<img width="673" height="598" alt="image" src="https://github.com/user-attachments/assets/ab009695-4de5-4ed4-b99b-9f79f3c46a30" />
---

# Procedure // Modify the procedure based on your circuit

Step 1: Set Up the Tinkercad Environment
1.	Log in to Tinkercad: Open Tinkercad in your web browser and log in to your account.
2.	Create a New Circuit: In the Tinkercad dashboard, click on "Circuits" and then select "Create New Circuit."
Step 2: Add Components to the Circuit
1.	Arduino Uno: Drag an Arduino Uno board from the components panel onto the workspace.
2.	TMP36 Sensor: Search for the TMP36 sensor in the components panel and drag it into the workspace.
3.	Breadboard: Drag a small breadboard to the workspace to help with wiring connections.
4.	Resistor (Optional): A resistor may not be necessary for this simple setup, but you can include it for more accurate readings.
5.	Wires: Use wires to connect the components.

Step 3: Connect the TMP36 Sensor to the Arduino
1.	TMP36 Pins:
o	Vout (Middle Pin): Connect this to an analog input pin on the Arduino (e.g., A0).
o	GND (Right Pin): Connect this pin to the ground (GND) on the Arduino.
o	Vs (Left Pin): Connect this to the 5V pin on the Arduino.
2.	Breadboard Wiring:
o	TMP36 Vout (Middle Pin) to Arduino A0: Use a wire to connect the middle pin (Vout) of the TMP36 sensor to the A0 analog input pin on the Arduino.
o	TMP36 GND (Right Pin) to Breadboard GND Rail: Connect the GND pin of the TMP36 sensor to the ground rail of the breadboard.
o	TMP36 Vs (Left Pin) to Breadboard 5V Rail: Connect the Vs pin of the TMP36 sensor to the 5V rail of the breadboard.
o	Arduino GND to Breadboard GND Rail: Connect a wire from the Arduino GND pin to the ground rail on the breadboard.
o	Arduino 5V to Breadboard 5V Rail: Connect a wire from the Arduino 5V pin to the power rail on the breadboard.
Step 4: Write the Arduino Code
1.	Code Editor: Click on the "Code" button at the top of the Tinkercad workspace to open the code editor.
2.	Set the Coding Mode: Ensure the editor is in "Text" mode to write your code in C/C++.
3.	Enter the Code: Write the following code to read the temperature from the TMP36 sensor
Step 5: Simulate the Circuit
1.	Start Simulation: Click the "Start Simulation" button at the top of the workspace to run the circuit and code.
2.	Monitor Output: Open the serial monitor by clicking the "Serial Monitor" button to view the temperature readings in both Celsius and Fahrenheit.
Step 6: Troubleshoot and Refine
1.	Check Connections: Ensure that all connections are made correctly on the breadboard and the Arduino.
2.	Adjust Code: If needed, tweak the code to improve accuracy or change the format of the output.
Step 7: Save Your Work
1.	Stop Simulation: Click "Stop Simulation" to end the simulation.
2.	Save the Circuit: Click "Save" to keep your circuit design and code for future use.


# Program
		// Temperature Based Fan Speed Controller
		// Sensor: LM35
		// Fan control: PWM using MOSFET
		
		#define LM35_PIN A0
		#define FAN_PIN 9
		
		void setup()
		{
		  Serial.begin(9600);
		  pinMode(FAN_PIN, OUTPUT);
		}
		
		void loop()
		{
		  // Read LM35 sensor
		  int sensorValue = analogRead(LM35_PIN);
		
		  // Convert ADC value to voltage
		  float voltage = sensorValue * (5.0 / 1023.0);
		
		  // LM35 gives 10 mV per degree Celsius
		  float temperature = voltage * 100.0;
		
		  int fanSpeed;
		
		  // Temperature-based fan control
		  if (temperature < 25)
		  {
		    fanSpeed = 0;       // Fan OFF
		  }
		  else if (temperature < 30)
		  {
		    fanSpeed = 80;      // Low speed
		  }
		  else if (temperature < 35)
		  {
		    fanSpeed = 150;     // Medium speed
		  }
		  else if (temperature < 40)
		  {
		    fanSpeed = 220;     // High speed
		  }
		  else
		  {
		    fanSpeed = 255;     // Maximum speed
		  }
		
		  // Set fan speed using PWM
		  analogWrite(FAN_PIN, fanSpeed);
		
		  // Display values in Serial Monitor
		  Serial.print("Temperature: ");
		  Serial.print(temperature);
		  Serial.print(" °C | Fan PWM: ");
		  Serial.println(fanSpeed);
		
		  delay(1000);
		}
# Output
		Temperature: 23.45 °C | Fan PWM: 0
		Temperature: 26.38 °C | Fan PWM: 80
		Temperature: 28.91 °C | Fan PWM: 80
		Temperature: 31.25 °C | Fan PWM: 150
		Temperature: 34.18 °C | Fan PWM: 150
		Temperature: 36.52 °C | Fan PWM: 220
		Temperature: 39.10 °C | Fan PWM: 220
		Temperature: 41.35 °C | Fan PWM: 255
		Temperature: 43.20 °C | Fan PWM: 255

# Result

The experiment to measure the temperature using the DHT11/DHT22/TMP36 sensor with Arduino UNO on Tinkercad has been successfully completed and verified. The system was able to accurately sense and display temperature (in both Celsius and Fahrenheit) and humidity values through the Arduino serial monitor. All procedure steps, including hardware setup, circuit simulation, and code validation, were performed as planned. The experimental results confirm the circuit and program function as intended.
