# Washing_machine_PIC16F877A

- **YOUTUBE VIDEO** - https://youtu.be/0LFGEaDlszk?si=nmy-M4vjqUtHNyZ1
- This project is a simulation of a basic washing machine using the PIC16F877A microcontroller.
It was developed as part of a 30-day Embedded Systems internship at Emertxe Information Technologies.
The project demonstrates real-time embedded programming concepts like GPIO, timers, interrupts, and peripheral interfacing — simulated using PICSimLab.

**Project Features**

- Mode selection via Keypad (Wash, Rinse, Spin, Idle)
- CLCD Display for showing system status
- Fan (motor) simulation using GPIO control
- Buzzer alert at end of cycle
- Timer-based delays for realistic wash cycles
- Software debounce and edge detection for accurate input
- Code written in Embedded C and compiled using MPLAB X IDE

**What I Learned**

- Embedded C programming for microcontroller-based systems
- Working with GPIOs using TRISx and PORTx registers
- Peripheral interfacing: CLCD, switches, fan, buzzer
- Using PICSimLab for real-time embedded simulation
- Handling real-world problems like switch bounce and mode transitions
- Planning and building a complete embedded system from scratch

**Tools & Technologies**

- PIC16F877A : Microcontroller (8-bit)
- MPLAB X IDE: Code writing & compilation
- PICSimLab  : Simulation of circuit & behavior
- Embedded C : Programming language

**Pin Mapping (Sample):**
- Keypad    : PORTB (RB0–RB7)
- CLCD      : PORTD/PORTC (RD0–RD7, RC0–RC2)
- Fan       : PORTC (RC3)
- Buzzer    : PORTC (RC4)

**Wash Cycle Modes**

- Idle   : System standby
- Wash   : 5 sec (Fan ON, LCD shows "Washing")
- Rinse  : 3 sec (Fan ON, LCD shows "Rinsing")
- Spin   : 2 sec (Fan ON, LCD shows "Spinning")

**To Run this Project Source files are available in repo :)**

- **Author :**
  **SOHAN K KUMBHAR**
- Intern at Emertxe Information Technologies
- **LinkedIn:** https://linkedin.com/in/sohan2277
