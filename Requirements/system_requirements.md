# Intelligent DC-DC Converter
## Revision A — System Requirements
Version 0.2

---

## 1. Project Objective

Design, simulate, fabricate, assemble, bring up, test, and characterize a
custom high-power direct-current to direct-current (DC-DC) converter.

Revision A will focus on developing a reliable and efficient power conversion
stage. Digital monitoring, communications, and multiple output rails will be
reserved for later revisions.

The project will demonstrate experience with:

- Switching power converter design
- Power semiconductor selection
- Inductor and capacitor selection
- Feedback and control
- Hardware protection
- Printed circuit board (PCB) design
- High-current PCB layout
- Thermal management
- Hardware bring-up and debugging
- Converter characterization and efficiency testing

---

## 2. System Use Case

The converter will represent the primary power-conversion stage of a future
intelligent avionics-style power distribution module.

Revision A shall accept an unregulated low-voltage DC input and produce a
regulated 12 VDC output capable of supplying high-current loads.

The converter shall operate independently without requiring a
microcontroller or software.

---

## 3. Input Requirements

Nominal input voltage:

28 VDC

Operating input voltage range:

24–36 VDC

The converter shall maintain normal operation throughout the specified input
voltage range.

The Revision A board shall contain no direct connection to wall/mains
alternating-current (AC) voltage.

A future isolated AC-to-DC front end may provide approximately 28 VDC to the
converter but will be developed as a separate system.

---

## 4. Output Requirements

Nominal output voltage:

12 VDC

Maximum output power:

200 W

Maximum nominal output current:

I_OUT = P_OUT / V_OUT

I_OUT = 200 W / 12 V

I_OUT ≈ 16.7 A

The converter shall regulate the 12 V output across the specified input
voltage range and supported load range.

Detailed output-voltage tolerance and transient-response requirements will be
defined after the control architecture is analyzed.

---

## 5. Converter Architecture

Revision A shall use a:

Single-phase synchronous buck converter

A synchronous buck converter uses actively controlled power
metal-oxide-semiconductor field-effect transistors (MOSFETs) for both the
high-side and low-side switching devices rather than using a diode as the
primary low-side device.

The converter shall use a dedicated hardware power-converter controller.

The initial control architecture shall be based on current-mode control,
subject to verification during the controller trade study.

The converter shall not depend on a microcontroller for normal voltage
regulation.

---

## 6. Efficiency Requirements

Minimum acceptable full-load efficiency:

≥ 93%

Design target:

≥ 95%

Stretch target:

≥ 97%

Efficiency shall be measured using input and output electrical power:

Efficiency = P_OUT / P_IN

At 200 W output power, achieving 95% efficiency corresponds to approximately
10.5 W of total converter loss.

Converter losses shall be estimated during the design process and compared
with measured losses during hardware testing.

---

## 7. Hardware Protection Requirements

Primary converter protection shall be implemented in hardware and shall not
depend on firmware.

The design shall include, where appropriate:

- Input fuse protection
- Reverse-polarity protection
- Undervoltage lockout (UVLO)
- Cycle-by-cycle current limiting
- Output overcurrent protection (OCP)
- Output overvoltage protection (OVP)
- Short-circuit protection
- Controlled startup / soft-start
- Thermal protection
- Prevention of simultaneous high-side and low-side MOSFET conduction,
  commonly called shoot-through

Any single firmware failure shall not disable primary converter protection.

The exact protection thresholds will be determined after component ratings
and normal operating conditions are established.

---

## 8. Thermal Requirements

The converter shall be designed for passive cooling during normal operation
where practical.

Major power components should remain below:

85 degrees Celsius design target

Major power components shall remain below:

100 degrees Celsius maximum during full-load steady-state testing

The design shall consider heat generation in:

- MOSFETs
- Inductor
- Current-sensing components
- Capacitors
- PCB copper
- Connectors

Thermal performance shall be verified experimentally.

---

## 9. PCB Requirements

Revision A shall use a custom four-layer printed circuit board (PCB).

The layout shall prioritize:

- Short high-current paths
- Small high-frequency switching-current loops
- Low-resistance power and ground paths
- Appropriate copper area for high-current conduction
- Thermal spreading
- Thermal vias where appropriate
- Separation of sensitive feedback signals from switching nodes
- Controlled grounding and return-current paths
- Reduction of electromagnetic interference (EMI)

Input and output connectors shall be rated above the expected continuous
operating current.

High-current power shall not be routed through small signal-style headers.

---

## 10. Testability Requirements

Revision A shall provide accessible test points for important converter
signals.

Test points should include:

- Input voltage
- Output voltage
- Switching node voltage
- High-side MOSFET gate signal
- Low-side MOSFET gate signal
- Feedback voltage
- Current-sense signal
- Controller supply voltage
- Ground reference
- Hardware fault signals

The board shall be designed so that important switching and control signals
can be safely measured during bring-up.

---

## 11. Revision A Testing

The completed converter shall be characterized over multiple operating
conditions.

Testing shall include:

- Startup behavior
- Output-voltage regulation
- Input-voltage variation
- Load variation
- Full-load operation
- Efficiency versus load
- Efficiency versus input voltage
- Output-voltage ripple
- Inductor-current behavior
- Switching-node behavior
- Component temperatures
- Current-limit operation
- Short-circuit response
- Protection-system behavior

Measured results shall be compared against analytical calculations and
simulation results.

---

## 12. Revision A Deliverables

Revision A shall produce:

- System requirements
- Converter architecture documentation
- Architecture trade studies
- Hand calculations
- Loss estimates
- LTspice simulations
- Component-selection trade studies
- Complete schematic
- Four-layer PCB layout
- Design review
- Fabricated PCB
- Assembly documentation
- Hardware bring-up procedure
- Test procedures
- Characterization results
- Revision A design review and lessons learned

---

## 13. Future Revision Goals

Later revisions may expand the converter into an intelligent multi-rail power
distribution module.

Potential future capabilities include:

- 12 V, 5 V, and 3.3 V output rails
- STM32 microcontroller
- Voltage and current telemetry
- Temperature monitoring
- Individual electronically switched output channels
- Per-channel current sensing
- Fault detection and isolation
- Fault logging
- Load sequencing
- Power budgeting
- Controller Area Network (CAN) communication
- Universal Serial Bus (USB) communication
- Universal Asynchronous Receiver-Transmitter (UART) communication
- Python-based monitoring and automated testing

The microcontroller shall supervise the power system but shall not replace
primary hardware protection.

---

## 14. Future AC Input Development

A future project may develop an isolated alternating-current to direct-current
(AC-DC) front end capable of converting approximately:

120 VAC → 28 VDC

This front end shall remain electrically and physically separate from the
Revision A DC-DC converter.

Direct mains voltage shall not be introduced onto the Revision A converter
PCB.