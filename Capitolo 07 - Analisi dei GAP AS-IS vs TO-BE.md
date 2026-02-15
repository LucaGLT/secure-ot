# Industrial Test Bench System

## Analisi dei GAP AS-IS vs TO-BE

### Automazione, Sicurezza Funzionale e Trasformazione della Sicurezza Informatica

------------------------------------------------------------------------

# 1. Scopo

This document defines the structured GAP analysis between the current
AS-IS configuration and the desired TO-BE architecture of the industrial
test bench system.

The objective is to:

-   Identify intervention areas
-   Define macro objectives
-   Outline macro implementation steps
-   Decompose into technical micro-steps
-   Reference applicable Safety and Cyber Security standards

This document serves as a decision and architectural planning baseline.

------------------------------------------------------------------------

# 2. Aree di Intervento e Obiettivi Macro

------------------------------------------------------------------------

## AREA A - Orchestrazione del Processo

### Obiettivi Macro

A1 -- Transition from manual coordination to deterministic centralized
orchestration\
A2 -- Introduce unified Test ID and time synchronization

### Reference Standards

-   IEC 61508 (systematic capability principles)
-   ISA-95 (enterprise-control integration)
-   ISO 9001 / ISO 17025 (traceability)

------------------------------------------------------------------------

## AREA B - Gestione dei Dati & Tracciabilità

### Obiettivi Macro

B1 -- Unify multi-source data collection\
B2 -- Ensure data integrity and correlation\
B3 -- Automate structured report generation

### Reference Standards

-   ISO 17025 (data integrity)
-   ISO 9001 (document control)
-   IEC 62443-3-3 (data integrity controls)
-   ALCOA+ principles

------------------------------------------------------------------------

## AREA C - Sicurezza Funzionale

### Obiettivi Macro

C1 -- Define architectural boundary between process logic and safety
logic\
C2 -- Guarantee safety independence from supervisory systems\
C3 -- Extend hazard analysis to include cyber-induced failures

### Reference Standards

-   IEC 61508
-   ISO 13849 / IEC 62061
-   ISO 12100
-   IEC 61511 (if process environment)

------------------------------------------------------------------------

## AREA D - Sicurezza Informatica (OT)

### Obiettivi Macro

D1 -- Introduce segmented OT network architecture\
D2 -- Protect authenticity and integrity of commands\
D3 -- Control remote access\
D4 -- Secure DUT API integration

### Reference Standards

-   IEC 62443 family
-   NIST SP 800-82
-   ISO 27001

------------------------------------------------------------------------

## AREA E - Governance & Gestione del Ciclo di Vita

### Obiettivi Macro

E1 -- Introduce configuration and version management\
E2 -- Formalize change management\
E3 -- Integrate combined Safety and Cyber validation lifecycle

### Reference Standards

-   IEC 61508 lifecycle model
-   IEC 62443-2-1
-   ISO 9001

------------------------------------------------------------------------

# 3. Macro Implementation Steps

------------------------------------------------------------------------

## AREA A -- Orchestration

1.  Define centralized control architecture.
2.  Introduce Test ID concept.
3.  Define unified time model.
4.  Redefine operator vs system responsibilities.

------------------------------------------------------------------------

## AREA B -- Data

1.  Define common data model.
2.  Introduce centralized repository.
3.  Define ingestion pipeline.
4.  Define automated reporting structure.

------------------------------------------------------------------------

## AREA C -- Safety

1.  Update hazard and risk analysis.
2.  Define safety boundary architecture.
3.  Validate safety independence.
4.  Define proof-test and validation strategy.

------------------------------------------------------------------------

## AREA D -- Cyber

1.  Define zones and conduits (IEC 62443).
2.  Implement network segmentation.
3.  Define role-based authentication model.
4.  Harden PLC/HMI/IPC.
5.  Implement security logging and monitoring.

------------------------------------------------------------------------

## AREA E -- Governance

1.  Define configuration management process.
2.  Introduce version control.
3.  Define secure update procedures.
4.  Implement change traceability register.

------------------------------------------------------------------------

# 4. Technical Micro-Steps

------------------------------------------------------------------------

## AREA A -- Technical Details

-   Implement centralized orchestration logic (PLC or IPC).
-   Implement NTP-based time synchronization.
-   Generate unique Test ID (UUID) per execution.
-   Propagate Test ID to all subsystems.
-   Introduce automated interlocks between subsystems.

------------------------------------------------------------------------

## AREA B -- Technical Details

-   Define structured database schema (SQL/Time-series).
-   Implement automatic parser for logger CSV.
-   Integrate DUT API client for real-time data (if adopted).
-   Automate report generation and digital signature.
-   Implement backup and retention policy.

------------------------------------------------------------------------

## AREA C -- Technical Details

-   Maintain physical safety independence.
-   Ensure remote systems cannot modify safety thresholds.
-   Validate fail-safe behavior on network loss or IPC crash.
-   Execute combined cyber-safety test scenarios.

------------------------------------------------------------------------

## AREA D -- Technical Details

-   Create dedicated OT network segment.
-   Introduce firewall between IT and OT.
-   Disable unused services on PLC/IPC.
-   Implement RBAC and MFA.
-   Introduce application whitelisting.
-   Centralize security event logging.

------------------------------------------------------------------------

## AREA E -- Technical Details

-   Introduce internal Git repository for control software.
-   Backup PLC programs with versioning.
-   Define formal change request process.
-   Implement regression testing before release.

------------------------------------------------------------------------

# 5. GAP Summary Concept

The transformation from AS-IS to TO-BE represents:

-   Shift from human-centered coordination to system-centered
    orchestration
-   Transition from isolated hardware safety to validated safety
    architecture
-   Introduction of cyber risk requiring structured mitigation
-   Evolution from manual data handling to structured digital lifecycle

This GAP analysis provides the structured roadmap for architectural
design and controlled system evolution.
