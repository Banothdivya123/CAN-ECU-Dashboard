# CAN-ECU-Dashboard
Developed a CAN-based dashboard to display real-time vehicle data such as speed, RPM, temperature, and gear position. Implemented communication between sensors and ECU for efficient data transfer. Enabled clear visualization of vehicle status for improved monitoring.

# 🧠 Simple Idea 

Think of a car like a team of small computers (ECUs).

One checks speed and indicators
One checks engine and time
One shows everything on a dashboard

All these computers talk to each other using CAN, which is like a shared communication wire.

👉 This project builds that system using STM32 microcontrollers.

# 🔧 What This Project Does

We created a mini car system simulation where:

Different ECUs send data (like speed, RPM, temperature)
A central ECU receives everything
It displays the data in real-time on a terminal

# 🧱 System Structure

There are 3 ECUs (nodes) connected using CAN:

# 🚦 ECU 1 – Vehicle Status

Sends:

Indicator status (ON/OFF)

Vehicle speed

Engine temperature

👉 Think of this as the driver input + basic sensors

# ⚙️ ECU 2 – Engine & Time

Sends:

Gear position

Engine RPM (from potentiometer using ADC)

Current time (RTC)

👉 This is like the engine control system

# 📊 ECU 3 – Dashboard (Receiver)

Receives all CAN messages

Filters only required messages

Displays formatted data using UART (Tera Term)

👉 This is the dashboard you see in a car

# 🔌 Hardware Used

3 × STM32F429ZIT6 boards

CAN Transceiver 

UART Terminal (Tera Term)

Potentiometer (for RPM input)

LEDs and Push Buttons

DHT11 (for temperature simulation)

# 🔄 How Communication Works

All ECUs are connected to a CAN bus

Each message has a unique ID

The receiver decides what to read using filters

# 📌 CAN Settings:

Mode: Normal

ID Type: Standard (11-bit)

Communication: Interrupt-based


# 🆔 CAN Message IDs

Parameter	CAN ID

Indicator	0x101

Speed	0x201

Temperature	0x301

Gear	0x401

RPM	0x501

Time	0x601

👉 IDs help the receiver understand what data is coming

# 🖥️ Sample Output (Tera Term)
Time     Speed   RPM   Gear   Temp   Indicator
12:45:33 45      67    G2     30     NoI

👉 This is your digital dashboard output

# ⭐ Key Features

Interrupt-based CAN communication (fast & efficient)

Hardware CAN filtering (only needed data is processed)

ADC used for RPM input

RTC used for real-time clock

UART used for displaying data

Safe ISR design using flags and volatile variables

# 🧩 Software Design

Built using STM32 HAL (CubeMX)

CAN messages handled using interrupt callbacks

Main loop processes data using flags

Modular embedded C structure

# 📚 What You Learn

How CAN communication works in vehicles

How multiple ECUs interact

Interrupt handling in embedded systems

Real-time data processing

Automotive embedded system basics

# 🚀 Future Improvements

Add FreeRTOS (multi-tasking system)

Implement error handling in CAN

Add Watchdog timer

Use LCD/OLED display instead of terminal

