# Industrial Test Bench System

## Addendum Tecnico AS-IS

### Descrizione Dettagliata dell'Architettura Tecnica

### 1. Scopo di questo Addendum

Quesra documento fornisce una descrizione tecnica più approfondita dell'architettura attuale (AS-IS) del test bench.

Completa la descrizione principale del sistema AS-IS fornendo dettagli su:


- Componenti hardware
- Interfacce di controllo
- Flussi di dati
- Capacità del Device Under Test (DUT)
- Limitazioni di integrazione attuali

### 2. Inventario degli Asset

#### 2.1 Strato di Controllo

**PLC** - Model class: Siemens S7-1200 (e.g., CPU 1214C) - I/O: -
Digital Inputs (DI) - Digital Outputs (DO) - Analog Inputs (AI 4--20
mA) - Analog Outputs (AO 4--20 mA) - Role: - Basic sequence control
(start, hold, stop, depressurization) - Actuator command - Basic alarm
handling

**HMI** - Model class: Siemens KTP700 Basic - Connected locally to PLC -
Supports: - Manual setpoint entry - Basic recipe parameters - Status
visualization - No centralized data storage

#### 2.2 Sottosistema Pressione

-   High-pressure pump (electrically driven)
-   Solenoid discharge valve (DO controlled)
-   Optional proportional valve (AO 4--20 mA)
-   Pressure transducer:
    -   Range: 0--400 bar
    -   Output: 4--20 mA
    -   Read by PLC AI channel
-   Mechanical pressure switch:
    -   Hardwired to safety relay chain

#### 2.3 Sottosistema Temperatura

-   Climatic chamber or heating system
-   Stand-alone temperature controller (e.g., Eurotherm / Omron)
-   Temperature sensors (PT100 / thermocouples)
-   Controller operates independently
-   PLC interaction limited to:
    -   RUN / READY / FAULT digital signals
    -   No coordinated profile management

#### 2.4 Apparecchiature di Acquisizione Dati

-   Stand-alone industrial data logger
-   Records pressure and temperature signals
-   Storage medium:

    -   SD card
    -   USB memory
-   Data format:

    -   CSV export
-   No real-time integration with PLC or HMI

### 3. Architettura di Sicurezza (Implementazione Attuale)

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

### 4. Caratteristiche del Device Under Test (DUT)

The DUT frequently includes embedded electronics with internal
intelligence.

#### 4.1 Capacità Funzionali del DUT

-   Internal sensor measurements (e.g. pressure, temperature, position,
    current)
-   Onboard logging capability
-   Event recording
-   Internal memory storage

#### 4.2 Metodi di Esportazione Dati del DUT

At the end of test cycle:

-   SD card removal and file extraction
-   Ethernet-based file download (manual procedure)
-   Data provided as structured logs (e.g., CSV, proprietary format)

#### 4.3 API del DUT (Non Utilizzata Attualmente)

The DUT provides a programmable interface (not integrated in current
workflow):

-   REST API or TCP-based protocol
-   Real-time or near real-time measurement access
-   Status query endpoints
-   Log streaming capability during test execution

Current state: - API exists but is not integrated into the test bench
process - No software developed to consume live DUT data - DUT treated
operationally as a black box until log extraction

### 5. Flussi di Dati Attuali

#### 5.1 Durante il Test

-   PLC controls pressure subsystem
-   Temperature controller executes its own profile
-   Data logger records signals
-   DUT logs internal data independently

There is no shared test identifier automatically propagated across
systems.

Synchronization depends on operator actions.

#### 5.2 Fine del Test

Operator performs:

-   Logger data extraction (USB / SD)
-   DUT log extraction (SD or Ethernet download)
-   Manual association of:

    -   DUT serial number
    -   Test parameters
    -   Logger files
    -   Temperature profile data

Data aggregation is manual and typically performed using spreadsheets.

### 6. Gap di Integrazione Identificati

-   No centralized orchestration logic
-   No unified test ID across subsystems
-   No automatic correlation of multi-source data
-   DUT API capability unused
-   No structured data repository
-   No networked architecture between assets

### 7. Caratteristiche della Linea di Base Architettonica

-   Strong physical safety isolation
-   Minimal digital connectivity
-   High operator dependency
-   Multiple independent data sources
-   No OT network segmentation required (no network present)

This AS-IS configuration provides low cyber exposure but high
operational manual burden and limited repeatability.
