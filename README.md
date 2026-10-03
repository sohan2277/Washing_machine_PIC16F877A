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

> A PIC16F877A-based embedded controller that simulates a basic washing machine cycle using keypad input, CLCD status display, timer-based control, interrupts, and GPIO-driven peripherals.

---

## 📑 Table of Contents

1. [Overview](#1-overview)
2. [Key Features](#2-key-features)
3. [Tech Stack](#3-tech-stack)
4. [Washing Modes](#4-washing-modes)
5. [Hardware & Pin Mapping](#5-hardware--pin-mapping)
6. [Embedded Concepts](#6-embedded-concepts)
7. [Project Structure](#7-project-structure)
8. [How to Run](#8-how-to-run)
9. [Project Demonstration](#9-project-demonstration)
10. [Learning Outcomes](#10-learning-outcomes)
11. [Author](#11-author)

---

# 1. Overview

**Washing Machine Controller** is an Embedded C project based on the **PIC16F877A microcontroller**.

The system allows the user to select different washing modes through a keypad. The selected operation is displayed on a character LCD, while the controller manages the cycle using timers and controls the simulated fan/motor and buzzer through GPIO.

The complete system is developed and tested using **PICSimLab**, without requiring physical hardware.

---

# 2. Key Features

| Feature | Description |
|---|---|
| 🔢 Keypad Input | Select washing modes through keypad controls |
| 🖥️ CLCD Display | Displays the current system state and operation |
| 🌀 Fan / Motor Control | Simulated through GPIO |
| 🔔 Buzzer Alert | Provides notification after a cycle |
| ⏱️ Timer-Based Control | Controls washing-cycle timing |
| 🔄 Debounce | Prevents false keypad inputs |
| ↔️ Edge Detection | Detects input transitions reliably |
| ⚙️ Multiple Modes | Idle, Wash, Rinse and Spin |
| ⚡ GPIO Control | Interfaces with simulated peripherals |
| 🧪 Simulation | Tested using PICSimLab |

---

# 3. Tech Stack

| Technology / Concept | Purpose |
|---|---|
| **Embedded C** | Firmware development |
| **PIC16F877A** | 8-bit microcontroller |
| **MPLAB X IDE** | Firmware development and project management |
| **PICSimLab** | Hardware and firmware simulation |
| **GPIO** | Digital input/output control |
| **Timers** | Cycle timing and delay control |
| **Interrupts** | Event and timer handling |
| **Keypad** | User input and mode selection |
| **CLCD** | System-status display |
| **TRISx / PORTx** | PIC I/O register configuration |

---

# 4. Washing Modes

The controller provides four operating states:

| Mode | Duration | Operation |
|---|---:|---|
| **Idle** | — | System remains in standby |
| **Wash** | 5 sec | Fan ON and `Washing` displayed |
| **Rinse** | 3 sec | Fan ON and `Rinsing` displayed |
| **Spin** | 2 sec | Fan ON and `Spinning` displayed |

> Cycle durations are configured for simulation purposes.

### Operating Flow

```text
              ┌──────────┐
              │   IDLE   │
              └────┬─────┘
                   │
             Keypad Selection
                   │
       ┌───────────┼───────────┐
       │           │           │
       ▼           ▼           ▼
     WASH        RINSE        SPIN
     5 sec       3 sec        2 sec
       │           │           │
       └───────────┼───────────┘
                   │
                   ▼
              Buzzer Alert
                   │
                   ▼
                  IDLE
```

---

# 5. Hardware & Pin Mapping

## Component Mapping

| Component | PIC16F877A Connection |
|---|---|
| **Keypad** | PORTB — RB0 to RB7 |
| **CLCD** | PORTD / PORTC — RD0 to RD7, RC0 to RC2 |
| **Fan / Motor** | RC3 |
| **Buzzer** | RC4 |

### Peripheral Interaction

```text
                 PIC16F877A
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
     Keypad         CLCD       Peripherals
        │            │            │
        │            │       ┌────┴────┐
        │            │       │         │
        ▼            ▼       ▼         ▼
      Input        Status    Fan      Buzzer
```

---

# 6. Embedded Concepts

## GPIO Programming

The project uses PIC16F877A GPIO registers for peripheral interfacing.

Key concepts include:

- `TRISx` register configuration
- `PORTx` register operations
- Digital input/output control
- Peripheral control through GPIO

---

## Keypad Interfacing

The keypad provides user input for selecting the washing mode.

The implementation includes:

- Key detection
- Software debounce
- Edge detection
- Mode selection

---

## CLCD Interfacing

The character LCD provides real-time system information such as:

```text
Washing
Rinsing
Spinning
```

It allows the user to observe the current operating state.

---

## Timer Control

Timers are used for controlling the duration of each washing operation.

```text
Wash  → 5 sec
Rinse → 3 sec
Spin  → 2 sec
```

---

## Interrupt Handling

Interrupt-based control is used for handling timer-related events and supporting reliable system operation.

---

## Peripheral Control

The controller manages:

- Fan / motor simulation
- Buzzer notification
- Keypad input
- CLCD output

---

# 7. Project Structure

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

### Source Organization

| Directory / File | Purpose |
|---|---|
| `Source files/Header files/` | Header files and declarations |
| `Source files/Source files/` | Embedded C source implementation |
| `nbproject/` | MPLAB X project configuration |
| `Makefile` | Project build configuration |
| `README.md` | Project documentation |

> Generated build outputs and private MPLAB X files are excluded from version control through `.gitignore`.

---

# 8. How to Run

## 8.1 Clone the Repository

```bash
git clone https://github.com/sohan2277/Washing_machine_PIC16F877A.git
```

Navigate to the project:

```bash
cd Washing_machine_PIC16F877A
```

---

## 8.2 Open in MPLAB X IDE

Open the project in **MPLAB X IDE**.

Make sure the project is configured for:

```text
PIC16F877A
```

---

## 8.3 Build the Project

Build the project using the configured PIC compiler/toolchain.

The required firmware output can then be used with the simulation environment.

---

## 8.4 Run in PICSimLab

Load the generated firmware into **PICSimLab** and start the simulation.

The simulated system allows you to:

1. Select a washing mode using the keypad.
2. View the selected operation on the CLCD.
3. Observe fan/motor operation.
4. Monitor the cycle timing.
5. Observe the buzzer notification at the end of the cycle.

---

# 9. Project Demonstration

🎥 **Project Demo:**

[▶️ Watch the Washing Machine Controller Demo](https://youtu.be/0LFGEaDlszk)

The demonstration shows the simulated washing-machine controller operating through different modes and displaying the corresponding system states.

---

# 10. Learning Outcomes

This project provided practical experience with:

- Embedded C programming
- PIC16F877A microcontroller programming
- GPIO configuration using `TRISx` and `PORTx`
- Keypad interfacing
- CLCD interfacing
- Timer configuration
- Interrupt handling
- Software debounce
- Edge detection
- Peripheral control
- Embedded system state/mode handling
- Firmware testing through simulation
- PICSimLab-based hardware simulation

---

# 11. Author

<div align="center">

### **Sohan K**

**Embedded Systems & IoT Developer**

<p>
  <a href="https://github.com/sohan2277">
    <img src="https://img.shields.io/badge/GitHub-sohan2277-181717?style=for-the-badge&logo=github" alt="GitHub"/>
  </a>
  <a href="https://www.linkedin.com/in/sohan2277/">
    <img src="https://img.shields.io/badge/LinkedIn-Sohan%20K-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
</p>

</div>

---

<p align="center">
  <b>🧺 Embedded C • PIC16F877A • GPIO • Timers • Interrupts • Peripheral Interfacing</b>
</p>
