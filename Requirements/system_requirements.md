# Intelligent Avionics Power Module

## Project Goal

Design, simulate, fabricate, bring up, and characterize a custom
DC-DC power conversion and distribution module with onboard monitoring,
fault protection, and telemetry.

## Rev A Scope

Rev A will focus primarily on the power converter.

Input voltage:
TBD

Nominal input voltage:
TBD

Output voltage:
12 VDC

Maximum output power:
TBD

Converter topology:
Synchronous buck

Target efficiency:
> 93%

Output voltage ripple:
< 100 mV peak-to-peak

## Protection Requirements

- Input fuse
- Undervoltage lockout
- Overcurrent protection
- Output overvoltage protection
- Overtemperature monitoring

## Monitoring Requirements

- Input voltage
- Output voltage
- Input current
- Output current
- MOSFET temperature
- Inductor temperature

## Future Rev B Features

- MCU-based telemetry
- Multiple switched load channels
- Individual channel current sensing
- Fault isolation
- CAN or UART communication
- Python monitoring and test software

## Major Deliverables

1. System requirements
2. Design calculations
3. LTspice model
4. Component selection/BOM
5. Schematic
6. PCB layout
7. Bring-up procedure
8. Rev A hardware
9. Characterization results
10. Rev B improvements
11. Final engineering report