# 🧺 Washing Machine Controller — PIC16F877A

<p align="left">
<img src="https://img.shields.io/badge/Embedded_C-00599C?style=for-the-badge" alt="Embedded C"/>
<img src="https://img.shields.io/badge/PIC16F877A-2C3E50?style=for-the-badge" alt="PIC16F877A"/>
<img src="https://img.shields.io/badge/MPLAB_X_IDE-EE1C25?style=for-the-badge" alt="MPLAB X IDE"/>
<img src="https://img.shields.io/badge/PICSimLab-37474F?style=for-the-badge" alt="PICSimLab"/>
<img src="https://img.shields.io/badge/GPIO-1565C0?style=for-the-badge" alt="GPIO"/>
<img src="https://img.shields.io/badge/Timers-546E7A?style=for-the-badge" alt="Timers"/>
<img src="https://img.shields.io/badge/Interrupts-6A1B9A?style=for-the-badge" alt="Interrupts"/>
<img src="https://img.shields.io/badge/Keypad-00897B?style=for-the-badge" alt="Keypad"/>
<img src="https://img.shields.io/badge/CLCD-455A64?style=for-the-badge" alt="CLCD"/>
</p>

A **PIC16F877A-based washing machine controller** developed in Embedded C and simulated using **PICSimLab**. The project demonstrates microcontroller programming, GPIO control, timer-based operation, interrupts, keypad interfacing, CLCD interfacing, and peripheral control.

Developed as part of a **30-day Embedded Systems Internship at Emertxe Information Technologies**.

---

## 🚀 Project Overview

This project simulates the operation of a basic washing machine using the **PIC16F877A microcontroller**.

The user selects a washing mode through a keypad, while the system displays the current operation on a character LCD. The controller manages the selected operation using timers and controls peripherals such as a fan and buzzer through GPIO.

---

## ✨ Key Features

* 🔢 Keypad-based mode selection
* 🖥️ CLCD status display
* 🌀 Fan/motor simulation using GPIO
* 🔔 Buzzer notification at the end of a cycle
* ⏱️ Timer-based washing cycles
* 🔄 Software debounce and edge detection
* ⚙️ Multiple operating modes
* 💻 Embedded C firmware
* 🧪 Complete simulation using PICSimLab

---

## 🔄 Washing Modes

| Mode      | Duration | System Operation              |
| --------- | -------: | ----------------------------- |
| **Idle**  |        — | System remains in standby     |
| **Wash**  |    5 sec | Fan ON — `Washing` displayed  |
| **Rinse** |    3 sec | Fan ON — `Rinsing` displayed  |
| **Spin**  |    2 sec | Fan ON — `Spinning` displayed |

> Cycle durations are configured for simulation purposes.

---

## 🔌 Hardware / Pin Mapping

| Component | PIC16F877A Pins                        |
| --------- | -------------------------------------- |
| Keypad    | PORTB — RB0 to RB7                     |
| CLCD      | PORTD / PORTC — RD0 to RD7, RC0 to RC2 |
| Fan       | RC3                                    |
| Buzzer    | RC4                                    |

---

## 🧠 Embedded Concepts

### GPIO Programming

* `TRISx` and `PORTx` register configuration
* Digital input/output control

### Keypad Interfacing

* User input detection
* Software debounce
* Edge detection

### CLCD Interfacing

* Displaying system status
* Mode and operation messages

### Timers

* Timer-based cycle control
* Timing and delays

### Interrupts

* Event handling
* Timer-based control

### Peripheral Control

* Fan/motor control
* Buzzer control

---

## 📂 Project Structure

```text
Washing_machine_PIC16F877A/
│
├── Source files/
│   ├── Header files/
│   │   ├── clcd.h
│   │   ├── digital_keypad.h
│   │   ├── main.h
│   │   ├── timers.h
│   │   └── washing_machine_function_def.h
│   │
│   └── Source files/
│       ├── clcd.c
│       ├── digital_keypad.c
│       ├── isr.c
│       ├── main.c
│       ├── timers.c
│       ├── washing_machine_function_def.c
│       └── washing_machine_header_function.c
│
├── nbproject/
├── Makefile
└── README.md
```

---

## ▶️ How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/sohan2277/Washing_machine_PIC16F877A.git
```

### 2. Open the Project

Open the project in **MPLAB X IDE**.

### 3. Build the Project

Build the project using the configured **PIC16F877A** toolchain.

### 4. Run the Simulation

Load the generated firmware into **PICSimLab** and run the washing machine simulation.

> The repository contains the source code and MPLAB X project files required for the project.

---

## 🎥 Project Demonstration

▶️ **[Watch the Project Demo on YouTube](https://youtu.be/0LFGEaDlszk)**

---

## 📚 What I Learned

* Embedded C programming for PIC microcontrollers
* Working with `TRISx` and `PORTx` registers
* GPIO and peripheral interfacing
* Keypad and CLCD interfacing
* Timer configuration and interrupt handling
* Software debounce and edge detection
* Designing mode-based embedded applications
* Debugging and testing embedded firmware through simulation
* Working with PICSimLab for hardware simulation

---

## 👨‍💻 Author

**Sohan K**

Embedded Systems & IoT Developer

🔗 **LinkedIn:**
https://www.linkedin.com/in/sohan2277/
