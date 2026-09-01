# EC-Project
Smart Solar-Powered Irrigation
System Using Soil Moisture
Sensing
Chhotu
Roll No: 49
Reg. No:
12529195
ECE, Section
225 RH
LPU,
Phagwara,
India
Shivam Raj
Amitabh
Yadav
Roll No: 52
Reg. No:
12525198
ECE, Section
225 RH
LPU,
Phagwara,
India
Anuj Kumar
Roll No: 51
Reg. No:
12524229
ECE, Section
225 RH
LPU,
Phagwara,
India
Abstract
Roll No: 50
Reg. No:
12526470
ECE, Section
225 RH
LPU,
Phagwara,
India
Water scarcity is one of the most pressing global challenges, and
agriculture accounts for nearly 70% of freshwater consumption
worldwide. Conventional irrigation methods result in significant
water wastage due to manual operation and the absence of
real-time soil monitoring. This project presents a Smart
Solar-Powered Irrigation System that automates watering
decisions based on live soil moisture data using an Arduino Uno
microcontroller, a soil moisture sensor, a relay-controlled DC
water pump, and a 16x2 LCD display. When moisture falls below
a predefined threshold, the relay activates the pump
automatically; once sufficient moisture is achieved, the pump
stops. A mini solar panel provides renewable energy to the
control circuit. The circuit design was first validated in Proteus
simulation before hardware implementation. Test results confirm
reliable sensor response, consistent relay actuation within 2-3
seconds, and accurate LCD feedback under varied soil
conditions. The proposed system is low-cost, offline-capable, and
scalable for small to medium-scale agricultural applications.
Keywords - Smart Irrigation, Soil Moisture Sensor, Arduino
Uno, Relay Module, Solar Power, Proteus Simulation, Water
Conservation, Embedded Systems.
I. INTRODUCTION
Water is the most vital natural resource for sustaining
agricultural productivity and human life. Agriculture accounts
for approximately 70% of global freshwater withdrawals, yet
a substantial portion is wasted through inefficient manual and
timer-based irrigation that operates without real-time soil
feedback. Over-irrigation leads to nutrient leaching, soil
degradation, and energy waste, while under-irrigation results
in poor crop yield. These challenges are especially severe in
developing regions where small-scale farmers have limited
access to advanced agricultural technology.
The Smart Irrigation System addresses these challenges by
integrating soil moisture sensing with microcontroller-based
automation. The system continuously monitors soil moisture
and automatically activates or deactivates a water pump based
on a configurable threshold, ensuring water is delivered only
when and where it is truly needed. The addition of a mini
solar panel makes the system energy-independent and
suitable for off-grid rural deployment.
The project is developed using an Arduino Uno
microcontroller, a resistive soil moisture sensor (YL-69), a
5V single-channel relay module, a mini DC submersible
water pump, and a 16x2 I2C LCD display. Before physical
assembly, the circuit was fully simulated in Proteus Design
Suite 8 to validate all connections, pin assignments, and
firmware behavior. The working prototype was subsequently
assembled and tested under real soil conditions to confirm
reliable operation.
The primary objectives of this project are:- Design an automated irrigation system that responds to
real-time soil moisture readings.- Validate the complete circuit using Proteus simulation
prior to hardware implementation.- Assemble and test a physical prototype demonstrating
sensor-to-actuator control.- Reduce water wastage through intelligent threshold-based
pump control logic.- Display real-time moisture percentage and pump status on
an LCD for user awareness.- Power the control circuit using a solar panel to
demonstrate renewable energy integration.
II. LITERATURE SURVEY
A. Review of Related Work
A growing body of research has explored automated and
smart irrigation systems. Goap et al. [1] proposed an IoT and
machine learning-based system that predicts irrigation
requirements using weather data and soil sensors, achieving
high accuracy but at significant cost and infrastructure
complexity. Dursun and Ozden [2] implemented a wireless
sensor network for multi-zone irrigation monitoring,
demonstrating the value of distributed sensing but facing
scalability limitations.
Nawandar and Satpute [3] developed an IoT-based
Android-controlled irrigation system providing remote
smartphone access, but requiring stable internet connectivity
unsuitable for rural areas. Kumar et al. [4] implemented
Arduino with GSM for SMS-based pump control, offering
remote operation without a local display. Rawal [5] utilized
Raspberry Pi with a web dashboard for monitoring, providing
1
Smart Solar-Powered Irrigation System Using Soil Moisture Sensing
ECE Project | LPU
rich data visualization at the cost of higher power
consumption. Patil and Kale [6] combined Arduino with
GSM for farmer SMS alerts, while Singh et al. [7] used
NodeMCU with ThingSpeak for cloud-based data logging.
Table I summarizes key related works:
TABLE I - Literature Summary
Ref.
[1]
Authors Technology Contribution Limitation
Goap et al.
2018
IoT + ML Prediction-based
irrigation
[2]
Dursun &
Ozden 2011
[3] Nawandar &
WSN
Multi-zone
monitoring
Satpute 2019 IoT + Android Smartphone
High cost
Limited
scalability
control
[4] Kumar et al.
2020
Arduino
+ GSM
[5] Rawal 2017 Raspberry
SMS pump
control
Needs
internet
No LCD
feedback
Pi
[6] Patil & Kale
2016
[7]
Singh et al.
2021
Arduino
+ GSM
NodeMCU +
ThingSpeak
Web dashboard
monitoring
SMS farmer
alerts
High
power use
No
simulation
Cloud data
logging
B. Research Gaps
Complex
config
The literature review reveals the following critical gaps that
this project addresses:- Most systems require internet connectivity, making them
unsuitable for rural areas with poor network infrastructure.- High-cost components (Raspberry Pi, cloud servers,
GSM) place solutions beyond the reach of small-scale
farmers.- Very few studies validate designs using simulation tools
like Proteus before hardware assembly, increasing risk.- Real-time local LCD feedback is rarely included, forcing
users to rely on external devices for status monitoring.- Standard recalibrable threshold control for different crop
types and soil compositions is largely absent.- Renewable energy (solar) integration for off-grid
operation is overlooked in most existing designs.
III. METHODOLOGY
A. Requirement Analysis
The project began with a thorough requirement analysis
identifying both functional and non-functional system needs.
Functional requirements include: continuous soil moisture
monitoring via an analog sensor, automatic pump activation
below a configurable moisture threshold, real-time LCD
display of moisture percentage and pump status, and reliable
deactivation of the pump once soil moisture is restored.
Non-functional requirements include low power
consumption, ease of threshold calibration for different soil
and crop types, low overall cost, robustness under
environmental conditions, and modularity for future IoT or
GSM extensions without redesigning the core system.
B. Component Selection
TABLE II - Components and Specifications
Component
Model / Spec
Arduino Uno ATmega328P, 5V, 16MHz
Role in System
Central microcontroller
Soil Moisture Sensor YL-69 Resistive Probe
Detects soil water content
Relay Module
Water Pump
16x2 LCD + I2C
Solar Panel
5V Single-ChannelSwitches pump ON / OFF
5V Mini DC Submersible
Delivers water to soil
HD44780 + PCF8574Real-time status display
5V, 60mA Mini Panel
Renewable power source
Breadboard & Wires
C. System Architecture
830 tie-point / std. Circuit connections
The system architecture follows a simple
sense-decide-actuate loop. The soil moisture sensor (AO pin)
outputs an analog voltage to Arduino pin A0. The 10-bit ADC
converts this to a value of 0-1023. The Arduino maps this to a
moisture percentage using the map() function and compares it
against a threshold (default 40%). If moisture is below the
threshold, a LOW signal is sent to the relay IN pin (D8),
energizing the relay coil and closing the Normally Open (NO)
contact to complete the pump circuit. The LCD (connected
via I2C on A4/SDA and A5/SCL) displays real-time moisture
percentage on line 1 and pump status on line 2. When
moisture recovers above the threshold, the relay is
de-energized and the pump stops. The solar panel connects to
Arduino VIN/GND.
D. Circuit Development and Proteus Simulation
The complete circuit was designed in Proteus Design Suite 8
before any hardware was assembled. A potentiometer
replaced the soil sensor to simulate variable analog outputs.
The compiled Arduino .hex firmware was loaded into the
virtual Arduino Uno model. Both dry-soil (pump ON) and
wet-soil (pump OFF) states were simulated and confirmed:
the relay switched correctly at the threshold, the LCD
displayed proper messages, and no pin conflicts or wiring
errors were detected. This pre-validation step significantly
reduced the risk of errors during physical assembly.
E. Arduino Firmware Logic
The firmware implements the following control algorithm:
2
Smart Solar-Powered Irrigation System Using Soil Moisture Sensing
ECE Project | LPU- Initialize: lcd.init(), lcd.backlight(), pinMode(relayPin,
OUTPUT), relay HIGH (pump OFF).- Loop: Read analog value from A0 using analogRead();
range 0-1023.- Convert: moisture% = map(raw, 1023, 0, 0, 100);
constrain to valid 0-100 range.- Display: Print moisture% on LCD line 1; update every 1
second.- Decide: If moisture% < 40 then digitalWrite(relay, LOW)- pump ON; else relay HIGH - pump OFF.- Display: Print 'Pump: ON' or 'Pump: OFF' on LCD line 2.- Debug: Print all values to Serial Monitor at 9600 baud for
calibration.- Delay: Wait 1000ms before next reading cycle to prevent
LCD flicker.
F. Hardware Assembly
After Proteus validation, all components were assembled on a
full-size 830-point breadboard. Assembly sequence: (1)
Mount Arduino Uno and establish 5V/GND power rails. (2)
Connect moisture sensor AO to A0, VCC to 5V, GND to
GND. (3) Connect relay IN to D8, VCC to 5V, GND to GND;
wire pump through relay NO-COM. (4) Connect I2C LCD:
SDA to A4, SCL to A5, VCC to 5V, GND to GND. (5)
Connect solar panel to VIN and GND. (6) Upload verified
firmware via USB. Color-coded jumper wires were used for
easy identification and debugging.
IV. VIRTUAL SIMULATION
The project was fully simulated in Proteus Design Suite 8, a
professional EDA tool supporting component-level
simulation with virtual microcontroller firmware execution.
The simulation schematic included: an Arduino Uno virtual
model loaded with compiled .hex firmware, a potentiometer
on A0 simulating the soil moisture sensor's variable analog
output, a 5V relay module with NPN transistor driver on pin
D8, a virtual 16x2 LCD configured for I2C communication
(SDA on A4, SCL on A5), and a DC motor connected to relay
output representing the water pump load.
Two operating states were verified in simulation. In the Pump
OFF state, the potentiometer was set high (simulating moist
soil, ADC above 500), and the relay remained inactive with
the LCD showing 'Moisture OK - Pump OFF'. In the Pump
ON state, the potentiometer was reduced (simulating dry soil,
ADC below 500), the relay energized, the motor activated,
and the LCD showed 'Moisture Low - Pump ON'. The
simulation confirmed:- Correct LCD display in both wet and dry simulated soil
conditions.- Precise relay switching at the defined ADC threshold of
500.- No pin assignment conflicts or wiring errors in the
complete schematic.- Firmware execution without runtime errors in the virtual
environment.- Correct I2C LCD communication at default address 0x27.
V. WORKING PROTOTYPE
Following successful Proteus simulation, the hardware
prototype was assembled using the validated schematic as
reference. All components were mounted on a full-size
breadboard with color-coded jumper wires. The Arduino Uno
was powered via USB during development and via the mini
solar panel during outdoor testing. The soil moisture sensor
probes were inserted into a soil-filled tray representing a plant
container, and the mini water pump was submerged in a small
water reservoir connected via tubing to the tray.
On power-up, the LCD displays the startup message 'Smart
Water / Irrigation Sys' for 2 seconds before entering the main
monitoring loop. During testing with dry soil (ADC 250-420,
moisture 25-40%), the relay activated within 2-3 seconds and
the pump began watering. The LCD showed 'Moisture: 32% /
Pump: ON'. As water was added incrementally, the moisture
reading climbed. Once it exceeded 40%, the relay
de-energized, the pump stopped, and the LCD updated to
'Pump: OFF'. The system demonstrated consistent, reliable
response across all test cycles. Prototype images are
presented in Section VII (Figures 1 and 2).
VI. RESULTS AND DISCUSSION
A. Quantitative Test Results
The prototype was evaluated under four controlled soil
moisture conditions. Sensor readings, relay state, and LCD
output were recorded for each condition:
TABLE III - Test Results Summary
Soil Condition ADC
Reading
Moisture
%
Bone Dry 850-1000 0-15%
Dry
Relay
State
Pump
Status LCD Line 2
ON ACTIVE Pump: ON
500-849 16-40%
ON ACTIVE Pump: ON
Adequate 250-499 41-75% OFF INACTIVEPump: OFF
Waterlogged 0-249 76-100% OFF INACTIVEPump: OFF
B. Discussion
The results confirm that the Smart Irrigation System
accurately detects soil moisture levels and responds reliably
within 2-3 seconds. The relay demonstrated consistent
3
Smart Solar-Powered Irrigation System Using Soil Moisture Sensing
ECE Project | LPU
switching with no false triggers during any test cycle. The
LCD provided clear, real-time feedback without requiring any
external monitoring device. The I2C interface reduced GPIO
usage from 8 pins to 2, preserving ports for future sensor
additions.
A key limitation observed is that the resistive YL-69 moisture
sensor is prone to electrolytic corrosion over extended use in
moist soil. Replacing it with a capacitive sensor in future
iterations would significantly improve longevity. The current
binary threshold control could also be enhanced with
proportional control for finer moisture regulation. The mini
solar panel provided adequate power for the control circuit in
direct sunlight but would require a rechargeable battery for
24/7 autonomous operation.
VII. PROTOTYPE IMAGES
The following figures present the assembled working
prototype of the Smart Solar-Powered Irrigation System.
Figure 1 shows the complete setup with the solar panel
connected and the LCD backlight illuminated, demonstrating
the system powered by solar energy. Figure 2 shows a closer
view of the circuit assembly highlighting the soil moisture
sensor probes in the soil tray, the relay module with its
indicator LED, the Arduino Uno, the I2C module, and the
16x2 LCD display mounted on the breadboard.
16x2 LCD display showing real-time moisture percentage
and pump status; mini solar panel (visible in Fig. 1)
connected for renewable power supply; full-size breadboard
used for prototyping all connections.
VIII. CONCLUSION
This project successfully designed, simulated, and
implemented a Smart Solar-Powered Irrigation System using
an Arduino Uno microcontroller, soil moisture sensor, relay
module, DC water pump, and 16x2 I2C LCD display. The
system automates irrigation decisions based on real-time soil
moisture data, eliminating manual intervention and
significantly reducing water wastage compared to
conventional irrigation methods.
Proteus simulation validated the complete circuit design prior
to hardware assembly, ensuring error-free physical
implementation. The working prototype demonstrated
reliable sensor-to-actuator response under varied soil
moisture conditions, with consistent relay switching within
2-3 seconds and accurate LCD feedback. Solar panel
integration demonstrated the feasibility of
renewable-powered operation for off-grid deployment.
Future enhancements may include: replacement of the
resistive moisture sensor with a capacitive sensor for
improved longevity; integration of an ESP8266 or ESP32
Wi-Fi module for IoT-based remote monitoring via
smartphone app; addition of a DHT11 sensor for temperature
and humidity-based decision making; incorporation of a
rechargeable Li-ion battery with solar charge controller for
24/7 autonomous operation; and expansion to multi-zone
irrigation with independent threshold control per zone.
Fig. 1: Full prototype with solar panel, LCD active, sensor
probes in soil tray, relay module, and Arduino Uno.
ACKNOWLEDGMENT
Fig. 2: Closer view showing soil moisture sensor, relay
indicator LED, I2C module, LCD display, and circuit wiring.
A. Component Identification in Prototype
In both figures, the following components are clearly visible
and correctly interconnected: Arduino Uno (blue PCB,
labeled UNO) serving as the central microcontroller; soil
moisture sensor with two metal probe electrodes inserted into
the soil tray; mini DC water pump (white cylindrical
component) connected via relay; 5V relay module with red
LED indicator showing activation state; I2C module (small
blue PCB with green LED) reducing LCD wiring to 2 pins;
The authors express sincere gratitude to the Department of
Electronics and Communication Engineering at Lovely
Professional University for providing laboratory facilities and
component resources. Special thanks to the course instructor
for continuous guidance, constructive feedback, and
encouragement throughout the project development process.
The authors also acknowledge their classmates and lab
technicians for their cooperative support during testing and
prototype assembly.
REFERENCES
[1] A. Goap, D. Sharma, A. K. Shukla, and C. R. Kumar, "An IoT
based smart irrigation management system using machine learning,"
Computers and Electronics in Agriculture, vol. 155, pp. 41-49, Dec.
2018.
[2] M. Dursun and S. Ozden, "A wireless application of drip
irrigation automation supported by soil moisture sensors," Scientific
4
Smart Solar-Powered Irrigation System Using Soil Moisture Sensing
ECE Project | LPU
Research and Essays, vol. 6, no. 7, pp. 1573-1582, 2011.
[3] N. K. Nawandar and V. R. Satpute, "IoT based low cost and
intelligent module for smart irrigation system," Computers and
Electronics in Agriculture, vol. 162, pp. 979-990, Jul. 2019.
[4] R. Kumar, M. K. Mishra, and A. Dubey, "Arduino-based smart
irrigation system using GSM module," Int. Journal of Engineering
Research and Technology, vol. 9, no. 6, 2020.
[5] S. Rawal, "IoT based smart irrigation system," Int. Journal of
Computer Applications, vol. 159, no. 8, pp. 5-8, 2017.
[6] S. R. Patil and B. S. Kale, "A model for smart agriculture using
IoT," in Proc. Int. Conf. Global Trends in Signal Processing, 2016,
pp. 543-545.
[7] R. Singh, V. Sinha, and A. Sharma, "Smart irrigation system
using NodeMCU and ThingSpeak IoT platform," Int. Journal of
Advanced Research in Computer Science, vol. 12, no. 3, pp. 45-50,
2021
