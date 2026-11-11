# Servo-Tester-Design

A compact, analog PWM Servo Tester designed in KiCad using an NE555P timer IC. This 2-layer through-hole PCB generates a variable-duty-cycle PWM signal controlled via a 100kΩ rotary potentiometer, allowing manual position testing and calibration of standard 3-pin hobby servo motors without requiring a microcontroller[cite: 3, 7].
<img width="1228" height="646" alt="servo tester" src="https://github.com/user-attachments/assets/8fa7bbe8-d272-41db-bb65-2d9c7c6918c9" />
<img width="581" height="434" alt="top_image" src="https://github.com/user-attachments/assets/ff1785ce-87f8-4683-bb9c-407654ed4dbd" />

---

## About the Project

The **Servo Tester** is built around the classic **NE555P** timer configured to output a ~50 Hz PWM signal[cite: 3]. By adjusting the **100kΩ potentiometer (`RV1`)**, the pulse width is varied to sweep the connected servo motor across its full range of motion[cite: 3, 7]. A **1N4148** switching diode (`D1`) separates the charging and discharging paths of the timing capacitor (`C1`) to achieve the asymmetric duty cycle required for standard servo control[cite: 3].

### Hardware Specifications
* **Input Power:** 6V DC via 2-pin 2.54mm header (`J1`)[cite: 3, 7]
* **Output:** 3-pin 2.54mm servo header (`J2` — `GND`, `VCC`, `SIG`)[cite: 3, 7]
* **Core IC:** NE555P (DIP-8)[cite: 3, 7]
* **Indicators:** 3mm Power LED (`D2`) with 1kΩ current-limiting resistor (`R3`)[cite: 3, 7]
* **Board:** 2-Layer PCB (`F.Cu` & `B.Cu`), 1.6 mm thickness, Through-Hole Technology (THT)[cite: 7]

### Bill of Materials (BOM)
| Reference | Value / Part | Footprint / Package | Quantity |
| :--- | :--- | :--- | :---: |
| `U1` | NE555P | DIP-8 (7.62mm)[cite: 3, 7] | 1 |
| `RV1` | 100K Potentiometer | Alps RK163 Single Horizontal[cite: 3, 7] | 1 |
| `R1` | 3M3 | Axial THT (DIN0204)[cite: 3, 7] | 1 |
| `R2` | 56K | Axial THT (DIN0204)[cite: 3, 7] | 1 |
| `R3` | 1K | Axial THT (DIN0204)[cite: 3, 7] | 1 |
| `C1` | 22nF | Ceramic Disc (5.00mm pitch)[cite: 3, 7] | 1 |
| `D1` | 1N4148 | DO-35 Axial[cite: 3, 7] | 1 |
| `D2` | LED | THT 3.0mm[cite: 3, 7] | 1 |
| `J1` | 2-Pin Header (Power) | 2.54mm Horizontal[cite: 3, 7] | 1 |
| `J2` | 3-Pin Header (Servo) | 2.54mm Horizontal[cite: 3, 7] | 1 |

---

## Applications

* **Robotics & Mechatronics:** Quickly test, center, and calibrate servo motors before mechanical assembly.
* **RC & Drone Builds:** Verify servo travel limits, direction, and responsiveness on the workbench without a receiver or flight controller.
* **Hardware Debugging:** Troubleshoot faulty servos or power delivery issues using a dedicated, standalone signal source.
* **Educational Use:** Demonstrates practical 555 timer astable/PWM circuit design and analog-to-PCB hardware implementation.

---

## Skills Used

* **Schematic Capture:** Designing clean, ERC-verified circuit schematics in KiCad Eeschema[cite: 1, 3].
* **PCB Layout & Routing:** Component placement, 2-layer manual trace routing, and footprint assignment in KiCad Pcbnew[cite: 1, 7].
* **Design Rule Checking (DRC):** Configuring and validating clearance, track width (0.5 mm), and annular ring rules[cite: 1, 7].
* **DFM (Design for Manufacturing):** Generating production-ready Gerber files (`F_Cu`, `B_Cu`, `Mask`, `Silkscreen`, `Edge_Cuts`) and NC drill files (`PTH`/`NPTH`)[cite: 6].
* **Analog Circuit Design:** Timing network calculation and diode-steered PWM generation using the NE555P[cite: 3].

---

## Techniques Used in the Project

* **Diode-Steered Duty Cycle Control:** Using a `1N4148` fast-switching diode (`D1`) alongside `R1` (3.3MΩ), `R2` (56kΩ), and `RV1` (100kΩ) to decouple charge/discharge paths for precise servo pulse-width modulation[cite: 3].
* **Dual-Layer Ground Plane Pour:** Implemented `GND` copper zones on both `F.Cu` and `B.Cu` layers with thermal reliefs to improve signal integrity, reduce noise, and simplify return paths[cite: 7].
* **Mechanical Integration:** Added 4 corner mounting holes directly on the `Edge.Cuts` layer for enclosure or standoff mounting[cite: 7].
* **Clear Silkscreen Documentation:** Labeled polarity (`+`, `-`), pinouts (`SIG`, `VCC`, `GND`), and board branding (`Servo Tester` / `Ampnics`) on `F.SilkS` for error-free assembly and field use[cite: 7].

---

## Repository Structure

```text
├── Servo Tester.kicad_pro   # KiCad project configuration[cite: 1]
├── Servo Tester.kicad_sch   # Schematic file[cite: 1, 3]
├── Servo Tester.kicad_pcb   # 2-layer PCB layout[cite: 7]
├── Servo Tester.kicad_prl   # KiCad project local settings[cite: 2]
└── grbr/                    # Manufacturing Gerber & Drill files[cite: 6]
