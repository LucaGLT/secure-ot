# Industrial Test Bench System

## AS-IS Technical Addendum

### Detailed Technical Architecture Description

------------------------------------------------------------------------

## 1. Purpose of This Addendum

This document provides a deeper technical description of the current
(AS-IS) test bench architecture.

It complements the main AS-IS system description by detailing: -
Hardware components - Control interfaces - Data flows - Device Under
Test (DUT) capabilities - Current integration limitations

------------------------------------------------------------------------

## 2. Asset Inventory

### 2.1 Control Layer

**PLC** - Model class: Siemens S7-1200 (e.g., CPU 1214C) - I/O: -
Digital Inputs (DI) - Digital Outputs (DO) - Analog Inputs (AI 4--20
mA) - Analog Outputs (AO 4--20 mA) - Role: - Basic sequence control
(start, hold, stop, depressurization) - Actuator command - Basic alarm
handling

**HMI** - Model class: Siemens KTP700 Basic - Connected locally to PLC -
Supports: - Manual setpoint entry - Basic recipe parameters - Status
visualization - No centralized data storage

------------------------------------------------------------------------

### 2.2 Pressure Subsystem

-   High-pressure pump (electrically driven)
-   Solenoid discharge valve (DO controlled)
-   Optional proportional valve (AO 4--20 mA)
-   Pressure transducer:
    -   Range: 0--400 bar
    -   Output: 4--20 mA
    -   Read by PLC AI channel
-   Mechanical pressure switch:
    -   Hardwired to safety relay chain

------------------------------------------------------------------------

### 2.3 Temperature Subsystem

-   Climatic chamber or heating system
-   Stand-alone temperature controller (e.g., Eurotherm / Omron)
-   Temperature sensors (PT100 / thermocouples)
-   Controller operates independently
-   PLC interaction limited to:
    -   RUN / READY / FAULT digital signals
    -   No coordinated profile management

------------------------------------------------------------------------

### 2.4 Data Acquisition Equipment

-   Stand-alone industrial data logger
-   Records pressure and temperature signals
-   Storage medium:
    -   SD card
    -   USB memory
-   Data format:
    -   CSV export
-   No real-time integration with PLC or HMI

------------------------------------------------------------------------

## 3. Safety Architecture (Current Implementation)

-   Safety relay chain (hardwired logic)
-   Inputs include:
    -   Emergency Stop
    -   Door interlock
    -   Mechanical pressure switch
-   Outputs:
    -   Power removal from pump
    -   Power removal from heating system
-   No safety PLC
-   No software-based safety logic
-   Safety reset requires local manual interaction

Safety operates independently of PLC logic.

------------------------------------------------------------------------

## 4. Device Under Test (DUT) Characteristics

The DUT frequently includes embedded electronics with internal
intelligence.

### 4.1 DUT Functional Capabilities

-   Internal sensor measurements (e.g. pressure, temperature, position,
    current)
-   Onboard logging capability
-   Event recording
-   Internal memory storage

### 4.2 DUT Data Export Methods

At the end of test cycle:

-   SD card removal and file extraction
-   Ethernet-based file download (manual procedure)
-   Data provided as structured logs (e.g., CSV, proprietary format)

### 4.3 DUT API (Currently Unused)

The DUT provides a programmable interface (not integrated in current
workflow):

-   REST API or TCP-based protocol
-   Real-time or near real-time measurement access
-   Status query endpoints
-   Log streaming capability during test execution

Current state: - API exists but is not integrated into the test bench
process - No software developed to consume live DUT data - DUT treated
operationally as a black box until log extraction

------------------------------------------------------------------------

## 5. Current Data Flow

### 5.1 During Test

-   PLC controls pressure subsystem
-   Temperature controller executes its own profile
-   Data logger records signals
-   DUT logs internal data independently

There is no shared test identifier automatically propagated across
systems.

Synchronization depends on operator actions.

------------------------------------------------------------------------

### 5.2 End of Test

Operator performs:

-   Logger data extraction (USB / SD)
-   DUT log extraction (SD or Ethernet download)
-   Manual association of:
    -   DUT serial number
    -   Test parameters
    -   Logger files
    -   Temperature profile data

Data aggregation is manual and typically performed using spreadsheets.

------------------------------------------------------------------------

## 6. Identified Integration Gaps

-   No centralized orchestration logic
-   No unified test ID across subsystems
-   No automatic correlation of multi-source data
-   DUT API capability unused
-   No structured data repository
-   No networked architecture between assets

------------------------------------------------------------------------

## 7. Architectural Baseline Characteristics

-   Strong physical safety isolation
-   Minimal digital connectivity
-   High operator dependency
-   Multiple independent data sources
-   No OT network segmentation required (no network present)

This AS-IS configuration provides low cyber exposure but high
operational manual burden and limited repeatability.
