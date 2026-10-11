## 📌 Project Overview

The Smart Exam Hall Monitoring and Management System provides an automated and reliable solution for managing examination halls. 
The system uses an RTC to maintain accurate time, a countdown timer to manage examination duration, an LM35 sensor to monitor room 
temperature, and multiple display and alert devices to provide real-time status information.

The system also includes password-protected configuration, pause/resume functionality, automatic examination start and 
end time recording, and LED-based examination status alerts.

## 🎯 Objectives

* Display the current RTC time and room temperature on a 16x2 LCD.
* Configure examination duration using a 4x4 matrix keypad.
* Implement a countdown timer for examination management.
* Display remaining examination time using multiplexed 7-segment displays.
* Provide Green, Yellow, and Red LED alerts based on the remaining time.
* Protect RTC and examination configuration using an admin password.
* Configure RTC time, examination start time, and examination duration.
* Implement Pause/Resume functionality using External Interrupt 1.
* Continuously monitor room temperature using an LM35 sensor.
* Automatically record examination start and end times.
* Reduce manual timing errors and improve examination hall efficiency.

## 🧰 Hardware Requirements

* LPC2148 ARM7 Microcontroller
* 16x2 LCD
* 4x4 Matrix Keypad
* RTC
* LM35 Temperature Sensor
* Two Multiplexed 7-Segment Displays
* Green LED
* Yellow LED
* Red LED
* Buzzer
* Switches
* USB-UART Converter / DB-9 Cable

## 💻 Software Requirements

* Embedded C
* Keil uVision
* Flash Magic
* LPC2148 Development Board

## ⚙️ System Working

### 1. Normal Monitoring Mode

Before the examination starts, the LCD displays:

* Current RTC date
* Current RTC time
* Room temperature

The LM35 sensor continuously monitors the temperature of the examination hall.

### 2. Password-Protected Configuration

Using External Interrupt 0, the invigilator can enter the configuration mode.

The system asks for an administrator password through the 4x4 keypad.

If the password is correct, the invigilator can:

* Edit RTC date and time.
* Configure examination start time.
* Set examination duration.

If the password is incorrect, access is denied and the system returns to normal monitoring mode.

### 3. Examination Countdown

When the examination starts:

1. The exact start time is recorded using the RTC.
2. The countdown timer starts.
3. The remaining examination time is displayed.
4. The remaining time is shown on two multiplexed 7-segment displays.

The 7-segment displays show the remaining examination time in minutes from `00` to `99`.

### 4. Examination Status Indication

The system uses three LEDs to indicate the examination status:

| Remaining Time       | LED Status    |
| -------------------- | ------------- |
| More than 10 minutes | Green LED ON  |
| Last 10 minutes      | Yellow LED ON |
| Last 1 minute        | Red LED ON    |
| Time reaches 00      | Buzzer ON     |

### 5. Pause and Resume

External Interrupt 1 is used for Pause/Resume functionality.

* First press → Countdown pauses.
* Second press → Countdown resumes.
* Timer continues from the exact point where it was paused.

This is useful during unexpected disturbances, technical problems, or official announcements.

### 6. Examination Start and End Logging

The RTC automatically records:

* Examination start time
* Examination end time

These records can be used for monitoring and administrative verification.

## 🔌 Main Modules

### RTC Module

Used for:

* Current date and time
* Examination start time
* Examination end time

### LCD Module

Displays:

* RTC time
* Date
* Room temperature
* Examination status
* Remaining time
* Configuration information

### Keypad Module

Used for:

* Password entry
* RTC configuration
* Examination duration configuration
* Start-time configuration

### LM35 Module

Used for continuous room temperature monitoring.

### 7-Segment Display

Displays the remaining examination time in minutes.

### LED Alert Module

Provides visual examination status indication.

### Buzzer

Indicates the end of the examination.

### External Interrupts

* **External Interrupt 0:** Password-protected configuration.
* **External Interrupt 1:** Pause/Resume countdown timer.

## 🔄 Project Workflow

<img width="1402" height="1122" alt="image" src="https://github.com/user-attachments/assets/42462097-17a7-4c43-b9da-4c9639da2260" />


## ⏱️ Examination Flow

```text
Power ON
   ↓
Initialize LPC2148 Peripherals
   ↓
Display RTC Time and Temperature
   ↓
External Interrupt 0
   ↓
Enter Password
   ↓
Password Valid?
   ├── No  → Return to Normal Mode
   │
   └── Yes
          ↓
   Configure RTC / Exam Time / Duration
          ↓
   Examination Starts
          ↓
   Start Countdown Timer
          ↓
   Display Remaining Time
          ↓
   Green / Yellow / Red LED Alerts
          ↓
   External Interrupt 1
          ↓
   Pause / Resume Timer
          ↓
   Countdown Reaches Zero
          ↓
   Activate Buzzer
          ↓
   Record Examination End Time
```

## ✨ Key Features

* RTC-based accurate time management.
* Password-protected configuration.
* Automated examination countdown.
* Room temperature monitoring.
* Multiplexed 7-segment display.
* Three-level LED warning system.
* Examination end buzzer alert.
* Pause/Resume functionality.
* Automatic examination start and end time recording.
* Modular Embedded C design.
* Reduced manual timing errors.

## 🛠️ Embedded C Modules

The project can be organized into modular files:

```text
Smart-Exam-Hall-Monitoring/
│
├── README.md
├── main.c
├── lcd.c
├── lcd.h
├── rtc.c
├── rtc.h
├── keypad.c
├── keypad.h
├── lm35.c
├── lm35.h
├── seven_segment.c
├── seven_segment.h
├── interrupt.c
├── interrupt.h
├── timer.c
├── timer.h
├── gpio.c
├── gpio.h
└── docs/
```

## 📚 Technologies Used

* Embedded C
* ARM7TDMI
* LPC2148
* RTC
* GPIO
* External Interrupts
* Timers
* LCD Interface
* Keypad Interface
* LM35 Temperature Sensor
* 7-Segment Multiplexing

## 🚀 Future Enhancements

* Store examination records in external memory.
* Add EEPROM-based event logging.
* Add UART or IoT-based remote monitoring.
* Add multiple examination hall support.
* Add automatic student attendance monitoring.
* Add web-based monitoring dashboard.
* Add real-time alerts to administrators.

