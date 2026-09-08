# Product Specifications Document (PSD)
TODO: Possibly new product name as of 2025-04-15, Ctrl+F and replace VUE with ???
* Issued PDF timestamp: 2025-XX-XX-XXXX PT USA
* Spoke Safety Inc Confidential


# 1.0 Change Log
| Version | Time Stamp      | Author(s)     | Notes                                      |
| :------ | :-------------- | :------------ | :----------------------------------------- |
| A       | 2025-05-08-0537 | Blaze Sanders | Initial Document                           |

Table 1 – Document version history used in exported .PDF files (e.g. 999-0004-A_VUE_ProductSpecificationsDocument.pdf)

| Version | Approved By     | Notes                                      |
| :------ | :-------------- | :----------------------------------------- |
| A       | TODO            | Spoke Safety Head of Engineering           |
| A       | TODO            | MiTAC                                      |

Table 2 – List of stakeholders (e.g. EMS, Spoke Safety, 3rd perty module provider) that have approved the .PDF verion of this document

# 2.0 Abbreviations & Terminology
* [GitHub MASTER ACRONYM LIST](TODO)
* ALS = Ambient Light Sensor: Photodetector that is used to sense the amount of ambient light present
* BFT = Board Function Test: Fixture used for board level functional and automated test during Mass Production (MP)
* CM = Contract Manufacture: Term for company that manufacture products
* C-V2X = Cellular Vehicle to Everything: Enables vehicles to communicate with each other, infrastructure, & pedestrians using cellular * networks and direct communication protocols
* EMS = Electronic Manufacturing Services:  A service a CM can offer to build electronics using a Joint Development Model (JDM)
* JDM = Joint Development Model: Product development method where Spoke and CM work together in the Concept and EVT phase to design a product
* MP = Mass Production: The phase after Production Validation Testing (PVT) where units for end-user purchase are manufactured at quantities greater then 20K units
* PRD = Product Requirements Document: Medium-level detail on product features, functionality, and user experience
* PVT = Production Validation Testing: Usually around 7.5% of MP run that proves product can be made at scale at desired cost
* PSD = Product Specifications Document: Very detailed technical specifications for design and manufacturing, including diagrams, schematics, and material lists
* TRL = Technology Readiness Level: Method for estimating the maturity of technologies during the acquisition phase of a program.


# 3.0 Introduction
This document defines the "Product Specifications" for Spoke Safety’s Go-To-Market portfolio offering for the VUE hardware and software. It contains detailed technical specifications for the design and manufacturing of the VUE product line, including diagrams, schematics, key subsystem performance specs, and material lists to describe "HOW TO DELIVERY" the all requirements defined in the **999-00001 Spoke Safety VUE Product Requirements Document**.

This document is targeted at engineering, manufacturering, and quality assurance teams who are building and testing the VUE to ensure is meets design, quality and safety standards. Examples of what may be be found in this document include GitHub link to images, PCB schematics, material specifications, bill of material (BOM) .csv file, PDF assembly instructions, testing procedures, and quality control measures.

The process for both the [Validation & Verification](https://en.wikipedia.org/wiki/Verification_and_validation) of all the requirements in the **999-00001 Spoke Safety VUE Product Requirements Document** will be outlined in sections 4.1.2 and 5.1.2 of this PSD with strict passing criteria.

The full Spoke Safety platform consists of the following three (3) interconnected subsystems:
1. The VUE, an embedded hardware device which mounts to bicycle seat-posts.
2. The Spoke Companion App (SCA), an iOS & Android smart phone app that connects to VUE via Bluetooth Low Energy (BLE).
3. The Spoke HUB, Spoke’s server solution for supporting VRU2X which communicates with VUE and SCA via LTE or TCP/IP.


# 4.0 Product Specifications
Building and testing the VUE will require combining many hardware and sofware subsystems. The specifications below are for the VUE only, with only basic interface details included for elements of the SCA or Spoke HUB that interact with the VUE. Please see "6.0 Interface Control Documentation" section below for interface details documenting all the subsystem connections.

![Miro Diagram](/999_00001_A_Figure_0.jpg "Figure 0") <br>
[Figure 0 - Suggested VUE Hardware System Architecture for EMS RFP March 4, 2025](https://github.com/Spokesafety-Inc/Compal-Spoke-Safety-MNDA-Data/blob/main/ProductDocumentation/Product_Specifications_Document/999_00001_A_Figure_0.jpg)

## 4.1 Hardware Product Specifications
| Parameter                  | Specification                       |
| :------------------------- | :---------------------------------- |
| Enclosure                  | IP67 rated, fiber-filled nylon      |
| Dimensions                 | Smaller then 9.00 x 6.0 x 11.0 cm   |
| Weight                     | Less than 0.200 kg (~0.440 lbs)     |
| Input Power                | 60W USB-C Power Delivery (PD) 3.1   |
| Input Voltage & Current    | 5V @ 3A, 12V @ 5A, or 20V @ 3A      |
| Input Data                 | 5 Gbps via USB-C 3.2 Gen 1x1 port   |
| Shock Resistance           | 100 G's @ 2 meter drop (3.92 kJ)    |
| Operating Temperature      | -10°C to 60°C                       |
| Key Sensors                | IMU, Barometer, ALS, RADAR          |
| Key Indicators             | 60 dB Buzzer, 0.3 to 300 lumen LEDs |
| Core Technology            | C-V2X, LTE Cat-1 Bis, GNSS, BLE 5.3 |
| Recommended Reflow Profile | Follow APP_CPU or C-V2X_MODULE spec |
| Hardware Reliability       | 4 sigma over 2 years                |
| RF in to BLE out latency   | Less than 50 milliSeconds (ms)      |
| Internal Bus Throughput    | At least 1 MegaBits/Second (Mbps)   |
| Safety Critical Compliance | TODO: DO-178C or ISO 26262          |

Table 2 - Basic hardware specifications defined in 999-00001-B_SpokeSafetyVUE_ProductRequirementsDocument TODO: switch Core Technology from Cat-1 Bis to 4G Cat-4 1T/2R

### 4.1.1 Hardware Design (TODO CONVERT MIRO LINKS TO GITHUB LINKS WITH IMAGE FILEPATHS)
To delivery the specs in Table 2 Spoke suggests the following part numbers, materials, high level (Non-OrCAD or Non-Altium) schematics, and requires the following subsystem performance specs.

#### 4.1.1.1 RGB_LED
Display information to the end-user with single (1) SMD LED, with low current draw and adjustable brightness using the [LP5562TME/NOPB](https://mou.sr/3ZwfX5C) 4 channel LED driver.

| Parameter                 | Specification                              |
| ------------------------- | ------------------------------------------ |
| Viewing angle             | 120°                                       |
| Mininium Luminous Flux    | 0.100 lumen at 0.004 Watts (2V at ~2 mA)   |
| Maximium Current Draw     | 10 mA                                      |
| Interface                 | I2C                                        |


#### 4.1.1.2 REAR_LED
Fifthteen (15) 2835 metric SMD LEDs [JE2835APO-N-0001A0000-N0000001](https://mou.sr/3F1IEjW) into each of the three (3) rear lights (total of 45 SMD LEDs) with focusing optics, we need to balance brightness, viewing angle, regulatory visibility zones, and thermal management to pass ELEC-029 (50 to 300 lumens). Driven at ~70% max rated current (0.70 * 15* 30 lumen = 315 lumen) to maintain long life and avoid lumen depreciation using the [TPS92201ADRLR](https://mou.sr/45sHt7O) 1 channel LED driver.

| Parameter                  | Specification (per LED)                    |
| -------------------------- | ------------------------------------------ |
| Viewing angle              | ~120°                                      |
| Maximium Luminous flux     | 30 lumen at 0.4 Watts (3V at ~140 mA)      |
| Thermal Resistance         | Low (18 °C/W) on aluminum-core PCB (MCPCB) |
| SMT Footprint              | 2.80 mm × 3.50 mm                          |
| Unified Glare Rating (UGR) | Low (< 16) to reduce distraction           |
| Interface                  | Pulse Width Modulation (PMW)               |

Design Goals for Left & Right Turn Signals:
  • Layout: Curved (65 mm radius) linear array (concave toward the viewer)
	•	Brightness: Even illumination when viewed head-on or at an angle (~45°–75° off-axis) to conform to ECE R6 and SAE J913
	•	Focusing Optics: Small (20 mm diameter x 10 mm height) collimating Total Internal Reflection (TIR) lens for each LED with 10–30° beam angle

Design Goals for a Center Brake Light:
  • Layout: Angled flat array each angled ~5–10° off-axis from each other (using small reflector cups or lens holders)
	•	Brightness: Even illumination when viewed head-on or at an angle (~45°–75° off-axis) to conform to ECE R6 and SAE J913
	•	Focusing Optics: Small (20 mm diameter x 10 mm height) collimating Total Internal Reflection (TIR) lens for each LED with 10–30° beam angle

Single RetroReflector Overarching Lens:
	•	Design a custom compound reflector or Fresnel lens in front of all 10 LEDs
	•	Diffuses and shapes light into regulatory viewing angles


APP_CPU + C-V2X_MODULE + LTE_MODULE + POSITIONING_SUBSYSTEM:
Option 1A: 4 Core SA522M in 4G LTE Cat-4 mode with Internal RTK mode turned on
Option 1B: 2 Core SA522M Dual Core with Internal GNSS + External LTE Cat-1 Bis (Telit LE910Q1) that ouput RTK corrention int the  Precise Positioning Engine (PPE) of SA522.

BLE_MCU: nRF5340


![Miro Diagram](/XXXX.png "Figure 1") <br>
[Figure 1 - 998-00004-A VUE Hardware Diagram for PCB Schematic Capture](https://miro.com/app/board/uXjVITP6qL8=/?share_link_id=297586684594)

![Power Mode Image](/998-00001-B_VUE_CPU_Power_Mode_Matrix.png "Figure 2") <br>
[Figure 2 - 998-00001-B VUE CPU Power Mode Matrix](https://github.com/Spokesafety-Inc/Compal-Spoke-Safety-MNDA-Data/blob/main/ProductDocumentation/Product_Specifications_Document/998-00001-B_VUE_CPU_Power_Mode_Matrix.png)

![Concept of Operation Excel](/IMAGE_PREVIEW_OF_998-00002-B_VUE_ConceptOfOperation.png "Figure 3") <br>
Figure 3 - Image preview of 998-00002-B VUE Concept Of Operation, click [HERE](https://github.com/Spokesafety-Inc/Compal-Spoke-Safety-MNDA-Data/blob/main/ProductDocumentation/Product_Specifications_Document/998-00002-B_VUE_ConceptOfOperation.xlsx) for full Excel based off [Private 998-00002 Spoke Master File](https://spokesafety9-my.sharepoint.com/:x:/g/personal/blaze_sanders_spokesafety_com/EaGBRltgbzpBva7lRLwIu8MB05M0oOTsvnZy2P3-47i9Pg?e=H0uwv4)

![Power Mode State Machine Diagram](/998-00003-C_VUE_PowerModeStateMachineDiagram.jpg "Figure 4") <br>
[Figure 4 998-00003-C VUE Power Mode State Machine Diagram](https://github.com/Spokesafety-Inc/Compal-Spoke-Safety-MNDA-Data/blob/main/ProductDocumentation/Product_Specifications_Document/998-00003-C_VUE_PowerModeStateMachineDiagram.jpg)

![Mechanical 3D models](/XXXX.png "Figure 3") <br>
(https://TODO)


### 4.1.2 Hardware Validation, Verification, and Testing
During the 5 phases of production (Concept, Engineering Validation Testing (EVT), Design Validation Testing (DVT), Production Validation Testing (PVT), and Mass Production (MP)) of the VUE product, the hardware will be tested (Spoke Test Scenario Number (STSN)) in the following manner with all 197 PRD requirements Validated (aka "Are you building the right thing for user?") and Verified (aka "Are you building it right, have you checked specifications are implemented?"). Spoke will handling Validation internally, and the EMS supplier will be providing detailed reports for Verification.

TODO: Each of the following STSN's will be fully documented using this [TEMPLATE_TEST_SETUP](https://github.com/Spokesafety-Inc/Compal-Spoke-Safety-MNDA-Data/blob/main/ProductDocumentation/Product_Specifications_Document/TEMPLATE_TestSetup.md)

To view and/or edit on any of the ??? Requirement Verification Tests, please download all the files at the following link and open the folder of the "Test Phase" you are interested in (e.g. EVT or MP). Then either commit the files back to the GitHub repo in a new branch and submit a Pull Request (PR) or email the updated files to Blaze Sanders at blaze.sanders@spokesafety.com
    * TODO LINK TO .CSV files

#### 4.1.2.1 Concept Phase
Hardware and tests during the Concept Phase shall have a [TRL](https://en.wikipedia.org/wiki/Technology_readiness_level) of 4 or lower, proving out the highest level assumations. STSN-001, STSN-???, and ??? shall pass before moving onto the EVT phase.

* STSN-XXX: EMS will provide Spoke with "998-00004 VUE Power Tree.xlxs" and battery pack at project kick-off to discharge at least 2200 times at 21 Watts and recharge at 60 Watts for 1 year during product delevopment and also provide data sheet references to VERIFY ELEC-015 (cycle lifetime) and ELEC-009 (nominal operating lifetime of battery is up to 1 year).

* STSN-XXX: Validate that all digital interfaces have a drive strength of at least 10 mA.

#### 4.1.2.2 EVT Phase
Hardware and tests during the EVT Phase shall have a [TRL](https://en.wikipedia.org/wiki/Technology_readiness_level) of 5, proving TODO. STSN-???, STSN-???, and ??? shall pass before moving onto the DVT phase.

* STSN-XXX, STSN-20,
* STSN-XXX: TODO VERIFY SYSA-011 to SYSA-026
* STSN-XXX: TODO ELEC-020 and ELEC-021
* STSN-XXX: TODO Calibration of all sensors: Verify IMU and Barometer provide accurate data
* STSN-XXX: TODO Solder just the APP_CPU / C-V2X_MODULE, LTE_MODULE (no passive parts or connector) to QTY 5 of their correpsoning PCBA's to VERIFY SYSA-027 (Recommended Reflow Profile). Send these now useless PCBA's to Spoke as mechanical mockups.

#### 4.1.2.3 DVT Phase
Hardware and tests during the DVT Phase shall have a [TRL](https://en.wikipedia.org/wiki/Technology_readiness_level) of 6 or 7, proving TODO. STSN-???, STSN-???, and ??? shall pass before moving onto the PVT phase.

* STSN-XXX: Record VUE RGB_LED with 1080p camera while VUE charges at 60 Watts from 10% to 99% (estimated time needed is 1.16 hours) using USB-C able and 100W Power Delivery (PD) brick to VERIFY ELEC-017 (USB-C PD 3.1), ELEC-011 (red, yellow, green LED color changes). Spoke will VALIDATE that ELEC-011 (charging LED colors) and ELEC-014 (CPU shutdown) is easily understood by User Group #1 (Road bike users age 35 to 55) and User Group #2 (E-Bike users age 13 to 23). See [Figure 4 998-00003-C VUE Power Mode State Machine Diagram](TODO GITHUB LINK)
* STSN-XXX: Use Spoke Companion App (SCA) to view VUE battery percentage as VUE runs at max power (100% duty cycle) from 100% to 15% (estimated time needed is 3.3 hours) to VERIFY ELEC-012 (even integer battery percentage on IPC bus), ELEC-013 (red, yellow, green LED color changes), ELEC-016 (monitor and report battery health via IPC), and ELEC-019 (Coulomb counting). Spoke will VALIDATE that ELEC-012 & ELEC-016 needs to be implemented via IPC, instead of a direct COMPANION_MCU or BLE_MCU API call. (https://miro.com/app/board/uXjVIUogtBk=/?share_link_id=948604146903)
* STSN-XXX: TODO Hall sensor test and GPIO connection to COMPANION_MCU

#### 4.1.2.4 PVT Phase
Hardware and tests during the DVT Phase shall have a [TRL](https://en.wikipedia.org/wiki/Technology_readiness_level) of 8, proving TODO. STSN-???, STSN-???, and ??? shall pass before moving onto the MP phase.

* STSN-XXX: VERIFY via report that all PVT PCBA gerber files pass ELEC-010 (6 or less PCB layers) and ELEC-032 (only a few SMT test points).
* STSN-XXX: VERIFY via report that all MP PCBA gerber files pass ELEC-010 (6 or less PCB layers) and ELEC-033 (~0 SMT test points).
* STSN-XXX: TODO ELEC-018
* STSN-XXX: TODO X-ray of Enclosure Test: Verify injection molded enclosure and PCBA are aligned
* STSN-XXX: Airtight Leakage Test: Verify IP67 on random 1% of the fully assembled VUE’s


#### 4.1.2.5 MP Phase
Hardware and tests during the DVT Phase shall have a [TRL](https://en.wikipedia.org/wiki/Technology_readiness_level) of 9 at before first MP units is manufactured, STSN-???, STSN-???, and ??? shall pass before the MP phas starts.

All PCBA's shall pass at least the following automated tests at a rate of at least 2000/week and produce the corresponding reports:
* Optical Quality Check: Verify components are not rotated or floating, that joint quality is normal (shiny solder), and TODO KPIs as suggested by the EMS supplier.
* Power Draw Test: VERIFY VUE is not drawing a nominal amount of current (no shorts)



11. GNSS RX Antenna Sensitivity & Carrier to Noise (C/N) Value Test: Verify near window or sky light that VUE knows its latitude and longitude to within 1.5 meters
12. C-V2X TX Antenna Power Modulation & RX Antenna Sensitivity Test: Verify that a 2nd golden VUE with C-V2X is 1 m away
13. RADAR Distance Test: Verify that a partial car shell / frame is 10 meters away
14. Bluetooth TX Antenna Power Modulation & RX Antenna Sensitivity Test: Verify that both an Android and iPhone can see and connect to a VUE using QR code on it.
15. LTE TX Talk to LTE Modem to get RSSI: TODO ???
16. Full Functional Test: Application Software and Board Support Package Firmware check, Write Design Source Name (DSN), LED Brightness, Charging Speed, Battery Level Check, and Full Sensor Calibration

# 5.1 Software Product Specifications
| Parameter                  | Specification                       |
| :------------------------- | :---------------------------------- |
| Embedded platforms         | ARM Cortex M4, TODO                 |
| Communication protocols    | BLE 5.3, ZeroMQ, I2C, I2S, NMEA 2000|
| Firmware update mechanism  | USB-C 3.0, OTA via BLE 5.3 & 4G LTE |
| API Documentation          | TODO: Link to GitHub / HTTPie docs  |

Table 3 - Basic software specifications defined in 999-00001-B Spoke Safety VUE Product Requirements Document


# 5.1.1 Software Design
This section outlines the requirements for functional alloction of the hardware: Yocto, Zephyr, controlling all the drivers with the following API calls.




[Figure ? - 998-00003-C VUE Power Mode State Machine Diagram](https://miro.com/app/board/uXjVIUogtBk=/?share_link_id=948604146903)

# 5.1.2 Software Validation, Verification, and Testing
During the 5 phases of production (Concept, Engineering Validation Testing (EVT), Design Validation Testing (DVT), Production Validation Testing (PVT), & Mass Production (MP)) of the VUE product, the software will be tested in the following manner with all 197 PRD requirements Validated (aka "Are you building the right thing for user?") and Verified (aka "Are you building it right, have you checked specifications are implemented?"). Spoke will handling Validation internally, and the EMS supplier will be providing detailed reports for Verification.

BLE_MCU 2 core with IPC betweeen them,

#### 5.1.2.1 Concept Phase
Setup C and Python Linters
Setup Intergration Testing Via Docker containers runinng Yocto Images

#### 5.1.2.2 EVT Phase
Unit testing of 80% of C functions

#### 5.1.2.3 DVT Phase
Regression testing of EVT units

#### 5.1.2.4 PVT Phase
Unit testing of 100% C functions

#### 5.1.2.5 MP Phase
2. Boot Up Check: Verify all CPU boot up and present green LED on POST
3. Software Version Check: Verify software on PCB matches newest release
4. USB and I2C Test: Verify all USB & I2C devices are visible to a test master controller
5. UART bus Check: Verify ACK (acknowledgement) from all UART serial port devices


# 6.0 Interface Control Documentation


## 6.1 Interface Diagrams
	•	Timing diagrams
	•	Sequence diagrams
	•	Flowcharts



## 6.2 Interface Details
INTE-008 & INTE-010 with variable data formats (e.g. Signed Int vs Float vs Binary) in 999-0005 Spoke Safety VUE Interface Control Document

	•	General description of the interface
	•	Interface role (e.g., data exchange, command/control)
	•	Operational environment (hardware/software context)
	•	Physical Interface
	•	Connectors
	•	Pin assignments
	•	Voltage levels & power requirements
	•	Logical Interface
	•	Protocols (e.g., I2C, SPI, TCP/IP)
	•	Timing requirements
	•	Data rates
	•	Data Interface
	•	Data format/structure (e.g., JSON, binary)
	•	Field definitions (name, type, length, valid ranges)
	•	Message types (requests, responses, errors)

## 6.3 Error Handling
	•	Timeout conditions
	•	Error codes
	•	Recovery mechanisms

## 6.4 Security
	•	Authentication/encryption
	•	Access control: Passkeys, AWS certs, SSH keys,
