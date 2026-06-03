# STM32 Temperature and Humidity Monitoring System using DHT11

This project implements a temperature and humidity monitoring system using an **STM32F103C8** microcontroller, a **DHT11** digital temperature-humidity sensor, and an **LCD 16x02** display.  
The system reads environmental temperature and relative humidity, processes the sensor data, and displays the measured values in real time.

The project was developed as a course project for **Embedded System Design**, focusing on sensor interfacing, timing control, embedded C programming, simulation, and basic hardware implementation.

---

## 1. Project Overview

The main objective of this project is to design a low-cost and reliable embedded monitoring module that can measure:

- Ambient temperature
- Relative humidity
- Sensor response status
- Measurement stability over time

The system is suitable for small-scale environments such as classrooms, laboratories, storage rooms, or basic monitoring applications.

---

## 2. System Architecture

The system consists of four main blocks:

1. **Sensor Block**
   - Uses the DHT11 sensor to measure temperature and humidity.
   - Communicates with the microcontroller through a single-wire data line.

2. **Controller Block**
   - Uses STM32F103C8 as the main processing unit.
   - Sends the start signal to DHT11.
   - Receives and decodes the 40-bit data frame.
   - Checks data validity using checksum.

3. **Display Block**
   - Uses an LCD 16x02 module.
   - Displays temperature in degrees Celsius and humidity in percentage RH.

4. **Power Block**
   - Provides stable DC power for STM32, DHT11, and LCD.
   - Uses common GND for all modules.

---

## 3. Hardware Components

| Component | Function |
|---|---|
| STM32F103C8T6 | Main microcontroller for sensor reading and data processing |
| DHT11 | Digital sensor for temperature and humidity measurement |
| LCD 16x02 | Displays temperature and humidity values |
| Pull-up Resistor 4.7 kΩ – 10 kΩ | Stabilizes the DHT11 single-wire DATA line |
| Crystal Oscillator | Provides stable clock for STM32 |
| Breadboard / PCB Dot Board | Used for circuit testing and assembly |
| ST-Link Programmer | Used to upload firmware to STM32 |
| Power Supply | Provides stable 3.3 V / 5 V supply |

---

## 4. DHT11 Communication Principle

The DHT11 sensor communicates with STM32 using a single-wire protocol.

The communication process includes:

1. STM32 pulls the DATA line low for at least 18 ms to start communication.
2. STM32 releases the DATA line and waits for the DHT11 response.
3. DHT11 responds with a low-level signal followed by a high-level signal.
4. DHT11 sends a 40-bit data frame.
5. STM32 measures pulse widths to determine whether each bit is `0` or `1`.
6. STM32 verifies the received data using checksum.

The DHT11 data frame consists of:

| Data Field | Size |
|---|---|
| Humidity Integer Part | 8 bits |
| Humidity Decimal Part | 8 bits |
| Temperature Integer Part | 8 bits |
| Temperature Decimal Part | 8 bits |
| Checksum | 8 bits |

---

## 5. Software Workflow

The firmware is written in **C** for STM32.  
The main workflow is:

1. Initialize system clock, GPIO, timer, and LCD.
2. Send start signal to DHT11.
3. Wait for sensor response.
4. Read the 40-bit data frame.
5. Decode temperature and humidity values.
6. Verify checksum.
7. Display valid data on LCD.
8. Repeat the measurement every 1 second.

---

## 6. Algorithm Flow

```text
Start
  |
  v
Initialize STM32 peripherals
  |
  v
Initialize LCD and DHT11 GPIO
  |
  v
Main loop
  |
  v
Wait 1 second
  |
  v
Send start signal to DHT11
  |
  v
Read 40-bit data frame
  |
  v
Check checksum
  |
  +-- Invalid --> Display error / retry
  |
  +-- Valid --> Extract temperature and humidity
  |
  v
Display values on LCD
  |
  v
Repeat
```

---

## 7. Display Format

The measured data is displayed on the LCD as:

```text
TEMP: XX °C
RH:   YY %
```

Example:

```text
TEMP: 30.0 C
RH:   58.0 %
```

---

## 8. Simulation and Hardware Testing

The system was designed and tested using both simulation and practical measurement.

### Simulation

- The circuit was simulated in **Proteus 8**.
- STM32 was connected to DHT11 and LCD 16x02.
- The LCD successfully displayed temperature and humidity values.

### Hardware Testing

The system was tested in three different environments:

1. **Closed room**
2. **Air-conditioned room**
3. **Outdoor environment**

The measured values from STM32 were compared with reference thermometer and humidity readings.

---

## 9. Experimental Results

The project recorded temperature and humidity values in different environments.

### Closed Room

- Average reference temperature: about 28.95 °C
- Average STM32 temperature: about 30.00 °C
- Temperature error: about 1.05 °C
- Average humidity error: about 0.87%

### Air-Conditioned Room

- Average reference temperature: about 26.60 °C
- Average STM32 temperature: about 26.50 °C
- Temperature error: about 0.10 °C
- Humidity error: about 5.5%RH

### Outdoor Environment

- The system continued to operate normally.
- Temperature and humidity values remained within the expected DHT11 operating range.

Overall, the system operated stably and produced acceptable results for a basic low-cost temperature and humidity monitoring module.

---

## 10. Tools and Technologies Used

- STM32F103C8T6
- DHT11 Sensor
- LCD 16x02
- C Programming Language
- STM32CubeIDE
- Proteus 8
- KiCad
- ST-Link Programmer
- Embedded GPIO Control
- Timer-based Delay
- Single-Wire Sensor Communication

---

## 11. Project Features

- Measures temperature from 0 °C to 50 °C.
- Measures relative humidity from 20%RH to 80%RH.
- Displays temperature and humidity on LCD.
- Uses STM32F103C8 for embedded processing.
- Communicates with DHT11 through a single-wire data line.
- Applies checksum verification to detect invalid data.
- Updates measured values periodically.
- Can be expanded for logging, alerting, or IoT monitoring.

---

## 12. Repository Structure

```text
.
├── firmware/
│   └── STM32 source code
├── simulation/
│   └── Proteus simulation files
├── hardware/
│   └── Schematic / PCB files
├── documents/
│   └── Project report and references
└── README.md
```

You may adjust the folder names depending on the actual structure of the repository.

---

## 13. Future Development

Possible improvements include:

- Replace DHT11 with DHT22 or SHT3x for higher accuracy.
- Add buzzer or LED warning when temperature or humidity exceeds a threshold.
- Add data logging to memory card or EEPROM.
- Add wireless communication such as WiFi, Bluetooth, or LoRa.
- Build a Web or mobile dashboard for remote monitoring.
- Design a compact PCB for real deployment.
- Add calibration to improve measurement accuracy.

---

## 14. Author

**Pham Thao Nguyen**  
Electronics and Telecommunications Engineering  
Ho Chi Minh City University of Technology – VNU-HCM
