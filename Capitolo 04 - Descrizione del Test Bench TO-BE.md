# Industrial Test Bench System

## Descrizione del Test Bench TO-BE

------------------------------------------------------------------------

### 1. Panoramica

The target system evolves from a manually coordinated test environment
to an integrated, automated, and partially remote-supervised industrial
test platform.

The objective is to increase repeatability, reduce manual intervention,
centralize data management, and introduce controlled remote supervision
while maintaining or improving functional safety.

------------------------------------------------------------------------

### 2. Architettura di Controllo Target

#### 2.1 Orchestrazione Centralizzata del Processo

-   A central control logic coordinates all subsystems (pressure,
    temperature, acquisition).
-   Automated sequencing manages:
    -   Ramp profiles
    -   Synchronization between subsystems
    -   Hold phases
    -   Controlled shutdown procedures
-   Pre-test validation of parameters and system state is performed
    automatically.

#### 2.2 Infrastruttura di Dati Integrata

-   All subsystems stream data to a centralized repository.
-   Each test is uniquely identified and associated with:
    -   Component ID
    -   Test recipe
    -   Timestamp
    -   Operator ID
-   Data correlation is automatic and structured.

#### 2.3 Capacità di Supervisione Remota

-   PC-based HMI for supervisory control.
-   Tablet-based monitoring (restricted functionality).
-   Controlled remote access for maintenance (via secure gateway).

Remote control privileges are limited and role-based.

------------------------------------------------------------------------

### 3. Flusso Operativo

#### 3.1 Preparazione del Test

Operator responsibilities:

-   Select test recipe.
-   Confirm correct component setup.
-   Authorize test start.

System responsibilities:

-   Validate configuration.
-   Check interlocks and safety conditions.
-   Verify sensor availability and plausibility.

Test start is conditional on validation success.

------------------------------------------------------------------------

#### 3.2 Esecuzione Automatizzata del Test

System responsibilities:

-   Coordinate all subsystems.
-   Enforce timing and synchronization.
-   Monitor process variables.
-   Log all relevant data in real time.
-   Trigger alarms or abort sequences when necessary.

Operator responsibilities:

-   Supervise process evolution.
-   Respond to alarms.
-   Intervene if required.

The operator shifts from executor to supervisor.

------------------------------------------------------------------------

#### 3.3 Fine Test e Reportistica

System responsibilities:

-   Automatically finalize test sequence.
-   Store all correlated data.
-   Generate standardized test report.
-   Log operator interventions and anomalies.

Operator responsibilities:

-   Review generated report.
-   Validate or reject test outcome.
-   Provide final approval.

------------------------------------------------------------------------

### 4. Architettura di Sicurezza (Stato Target)

-   Safety functions implemented in dedicated safety logic.
-   Critical functions include:
    -   Overpressure protection
    -   Overtemperature trip
    -   Safe depressurization
    -   Guard interlock management
-   Safety reset requires local physical confirmation.
-   Remote systems cannot override safety interlocks.

Functional safety remains independent from supervisory systems.

------------------------------------------------------------------------

### 5. Fondamenti di Sicurezza Informatica

The introduction of connectivity creates a new exposure surface.

Security principles include:

-   Network segmentation between OT and IT domains.
-   Role-based access control.
-   Authentication for critical actions.
-   Logging and traceability of configuration changes.
-   Secure remote maintenance via controlled gateway.

Cyber controls protect process integrity but do not replace safety
functions.

------------------------------------------------------------------------

### 6. Modello di Responsabilità (TO-BE)

#### Responsabilità dell'Operatore

-   Authorize test execution.
-   Supervise automated process.
-   Manage abnormal events.
-   Validate final results.
-   Maintain accountability for test acceptance.

#### Responsabilità del Sistema

-   Coordinate full test lifecycle.
-   Validate preconditions.
-   Execute deterministic sequences.
-   Aggregate and store data.
-   Generate formal reports.
-   Maintain event traceability.

#### Responsabilità della Logica di Sicurezza

-   Enforce safe operational limits.
-   Override unsafe commands.
-   Force safe state in hazardous conditions.
-   Require local reset after safety trip.

------------------------------------------------------------------------

### 7. Caratteristiche Chiave dello Stato Target

-   Reduced manual synchronization.
-   Increased repeatability.
-   Structured data lifecycle.
-   Controlled remote supervision.
-   Clear separation between process control and safety logic.
-   Emergence of cyber security as a system-level requirement.
