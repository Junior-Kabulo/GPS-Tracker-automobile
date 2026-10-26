# GPS Tracker Automobile — Custom PCB Design

**An embedded vehicle tracking system integrating GNSS positioning, GSM/GPRS connectivity, and backup power.**

## 1. Project Overview

This project focuses on the design of a custom printed circuit board (PCB) for an embedded vehicle tracking system.

The system is designed to acquire geographic position data using a GNSS receiver and transmit tracking information through a GSM/GPRS cellular network.

The hardware integrates an ESP32-S3 microcontroller module, a GNSS receiver, a cellular modem, power management circuitry, antenna interfaces, and a backup battery interface.

The project emphasizes electronic hardware design, PCB layout, power integrity, RF design considerations, and technical documentation using Altium Designer.

## 2. System Architecture

The system is organized around four main functional blocks:

- **Microcontroller:** An ESP32-S3-WROOM-1 module responsible for system control, data processing, and communication management.
- **GNSS receiver:** A Quectel L76L-M33 module intended to provide positioning and navigation data.
- **GSM/GPRS modem:** A SIM800C module intended to transmit tracking data over a cellular network.
- **Power management:** Power conversion and distribution circuitry, with a backup battery interface.

### Data Flow

```text
GNSS Antenna
     |
     v
L76L-M33 GNSS Receiver
     |
     | UART
     v
ESP32-S3-WROOM-1
     |
     | UART
     v
SIM800C GSM/GPRS Modem
     |
     v
Cellular Network
     |
     v
Remote Server / Tracking Interface
```

The GNSS receiver provides positioning data to the microcontroller. The ESP32-S3 processes the data and manages its transmission through the cellular modem.

The end-to-end data transmission and tracking interface remain subject to firmware implementation and system validation.

## 3. Main Hardware Components

| Component | Function |
|---|---|
| ESP32-S3-WROOM-1 | Main microcontroller module |
| SIM800C | GSM/GPRS cellular communication |
| Quectel L76L-M33 | GNSS positioning |
| GNSS antenna interface | Connection to the GNSS antenna |
| GSM antenna interface | Connection to the cellular antenna |
| Power conversion circuitry | Voltage regulation and power distribution |
| Battery interface | Backup power connection |
| USB-C interface | USB connectivity and development access, according to the implemented circuit |

The final component references, quantities, and manufacturer details are documented in the hardware design files and Bill of Materials (BOM).

## 4. Design Objectives

The main objectives of this project are to:

- Design a compact custom PCB using Altium Designer.
- Integrate GNSS positioning and GSM/GPRS connectivity.
- Develop a power architecture suitable for the different supply requirements of the electronic modules.
- Provide an interface for backup battery power.
- Design appropriate antenna interfaces and RF signal paths.
- Apply suitable PCB layout and grounding practices.
- Prepare PCB design files and manufacturing documentation.
- Establish a foundation for future firmware development and hardware validation.

## 5. Hardware Design Considerations

### 5.1 RF Design and Antenna Interfaces

The GNSS and GSM interfaces require careful consideration of RF routing, grounding, antenna integration, and component placement.

The design considerations include:

- A target characteristic impedance of 50 Ω for RF transmission lines, where required by the selected interfaces.
- Continuous ground reference planes along RF signal paths.
- Appropriate placement of antenna connectors and matching-network components.
- RF keepout areas according to module and antenna manufacturer recommendations.
- Verification of the PCB stack-up and transmission-line geometry.

The final trace dimensions and matching-network values must be determined from the selected PCB manufacturer's stack-up data and the antenna and module specifications. RF performance must be verified through appropriate analysis and measurements.

### 5.2 Power Management

The power architecture must accommodate the supply requirements of the ESP32-S3, GNSS receiver, and SIM800C modem.

Particular attention is required for the SIM800C because its GSM transmission bursts can cause significant current demand and supply-voltage dips.

The design must account for:

- Input power protection.
- Voltage conversion and regulation.
- Supply decoupling and transient response.
- Battery connection and backup operation.
- Grounding and return-current paths.

The suitability of the power supply must be confirmed through design review and testing under representative operating conditions.

### 5.3 PCB Stack-up and Layout

The PCB layout must provide suitable grounding, power distribution, signal routing, and RF performance.

A four-layer stack-up may be used if confirmed by the current PCB design and manufacturing requirements.

An example of a possible four-layer arrangement is:

| Layer | Intended purpose |
|---|---|
| L1 | Components, signals, and RF routing |
| L2 | Continuous ground reference plane |
| L3 | Power distribution and additional routing where appropriate |
| L4 | Additional signal routing and components, if required |

This arrangement is a design proposal, not a claim that the manufactured stack-up has been finalized. The actual layer assignment, dielectric properties, copper thicknesses, and RF trace geometry must be confirmed before fabrication.

## 6. Design Tools

- **Altium Designer:** Schematic capture, PCB layout, and hardware design documentation.
- **Git:** Version control for project files.
- **GitHub:** Source repository and project documentation.

Firmware development and debugging tools will be documented as the software implementation progresses.

## 7. Repository Structure

```text
GPS-Tracker-automobile/
├── hardware/
│   ├── BOM/
│   │   └── GPS_Tracker_V1.xlsx
│   ├── PCB/
│   │   ├── GPS_Tracker_V1.PrjPcb
│   │   └── PCB.PcbDoc
│   └── Shematic/
│       ├── Alimentation.SchDoc
│       ├── GPS_GNSS.SchDoc
│       ├── MCU.SchDoc
│       ├── SIM.SchDoc
│       └── USB-C.SchDoc
├── docs/
├── images/
└── README.md
```

This structure reflects the current organization of the hardware files. Additional directories, such as `firmware/`, may be added when corresponding project files are available.

## 8. Project Status

**Current phase:** Hardware design and PCB development.

The repository contains PCB project files, schematic documents, and a BOM spreadsheet. Their presence does not by itself imply that the design has been fully reviewed, manufactured, or validated.

The next stages include:

- Reviewing the schematic and component selection.
- Checking PCB design rules and routing.
- Confirming the power architecture and RF layout.
- Preparing and reviewing manufacturing outputs.
- Manufacturing and assembling a prototype.
- Testing GNSS reception, cellular communication, and power stability.
- Documenting test procedures, results, and design revisions.

Project status will be updated as each stage is completed.

## 9. Planned Improvements

- Complete the schematic and PCB design review.
- Verify power-supply performance under cellular transmission load.
- Review RF routing, antenna integration, and impedance requirements.
- Complete manufacturing documentation.
- Assemble and test a prototype.
- Develop the firmware and tracking data transmission workflow.
- Integrate a remote tracking interface when the communication backend is implemented.
- Record test results and document hardware revisions.

## 10. Author

**Junior Kabulo Sungu**

Engineering Student — Mechatronics and Embedded Systems

Areas of work: PCB design, embedded systems, GNSS positioning, and GSM/GPRS communication.

---

*This project is intended for engineering education, prototyping, and portfolio demonstration. Its final performance depends on the completed hardware design, component selection, antenna integration, firmware, network availability, and validation results.*
