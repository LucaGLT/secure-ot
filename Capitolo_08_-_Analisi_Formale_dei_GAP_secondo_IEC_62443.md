# Industrial Test Bench System

## Analisi Formale dei GAP secondo IEC 62443

### Rapporto di Valutazione del GAP AS-IS rispetto al Security Level Target (SL2)

# 1. Scopo del Documento

This document provides a formal GAP Analysis of the current AS-IS
industrial test bench architecture against the requirements of IEC
62443.

The objective is to:

-   Define the assessed system scope
-   Identify zones and conduits
-   Determine the Target Security Level (SL-T)
-   Assess the Actual Security Level (SL-A)
-   Identify gaps against IEC 62443-3-3 Foundational Requirements
-   Highlight missing programmatic controls (IEC 62443-2-1)
-   Identify component-level gaps (IEC 62443-4-2)

This report is structured in alignment with IEC 62443 assessment
methodology.

# 2. Spiegazione dei Termini Chiave di IEC 62443

For clarity, the following abbreviations are used in this report:

**SL (Security Level)**\
A defined level of resistance against a defined threat profile.

**SL-T (Target Security Level)**\
The required Security Level determined through risk assessment (IEC
62443-3-2).

**SL-A (Achieved or Actual Security Level)**\
The Security Level currently achieved by the system in its AS-IS
configuration.

**SL-C (Capability Security Level)**\
The Security Level that system components are capable of achieving when
properly configured.

**FR (Foundational Requirement)**\
One of the seven high-level security requirement categories defined in
IEC 62443-3-3.

The seven FR categories are:

-   FR1 -- Identification and Authentication Control (IAC)
-   FR2 -- Use Control (UC)
-   FR3 -- System Integrity (SI)
-   FR4 -- Data Confidentiality (DC)
-   FR5 -- Restricted Data Flow (RDF)
-   FR6 -- Timely Response to Events (TRE)
-   FR7 -- Resource Availability (RA)

# 3. Definizione del Sistema (IEC 62443-3-2)

## 3.1 Asset Identificati (AS-IS)

-   PLC (Siemens S7-1200)
-   Local HMI
-   Temperature controller (stand-alone)
-   Stand-alone data logger
-   DUT (Device Under Test) with Ethernet API capability
-   Safety relay chain (not cyber-relevant but safety-critical)
-   Operator workstation (offline report creation)

No formally defined OT network architecture exists in AS-IS
configuration.

## 3.2 Modello Preliminare di Zone (Concettuale)

Zone Z1 -- Basic Control Zone\
- PLC\
- HMI\
- Temperature controller\
- Data logger

Zone Z2 -- DUT Zone\
- DUT device\
- Ethernet interface

Zone Z3 -- Future Supervisory Zone (TO-BE)\
- IPC / SCADA\
- Central data repository

Zone Z4 -- Enterprise IT Zone\
- Reporting PC\
- Corporate network

Conduits in AS-IS are mostly physical/manual (USB, SD, direct Ethernet
cable).\
No logical conduits or segmentation are formally defined.

# 4. Determinazione del Security Level Target

Based on:

-   Industrial environment exposure
-   Moderate likelihood of misuse or tampering
-   Presence of safety implications
-   No advanced nation-state threat model

The recommended Target Security Level is:

**SL-T = 2**

SL2 provides protection against:

-   Intentional violation using simple means
-   Attackers with limited resources
-   Generic malware
-   Insider misuse scenarios

# 5. IEC 62443-3-3 Foundational Requirement Assessment

## FR1 -- Identification & Authentication Control (IAC)

AS-IS: - No structured authentication on PLC/HMI - No unique user
identities - DUT API authentication undefined

SL2 Requirement: - Unique user IDs - Authentication mechanisms - Session
control

Assessment: SL-A ≈ 0\
Gap: High

## FR2 - Controllo d'Uso (UC)

AS-IS: - No role-based access control - No privilege separation

SL2 Requirement: - Role-based access control (RBAC) - Principle of least
privilege

Assessment: SL-A ≈ 0\
Gap: High

## FR3 - Integrità del Sistema (SI)

AS-IS: - No integrity verification - No formal configuration
management - No controlled update process

SL2 Requirement: - Protection against unauthorized modification -
Integrity assurance mechanisms - Controlled update procedures

Assessment: SL-A ≈ 0\
Gap: High

## FR4 - Riservatezza dei Dati (DC)

AS-IS: - Data stored in plain CSV - No encryption - Removable media
uncontrolled

SL2 Requirement: - Protection of sensitive data - Encryption where
required

Assessment: SL-A ≈ 0\
Gap: Medium

## FR5 - Flussi di Dati Limitati (RDF)

AS-IS: - No network segmentation - No firewall or conduit control -
Direct DUT Ethernet access

SL2 Requirement: - Defined zones - Controlled conduits - Logical
segmentation

Assessment: SL-A ≈ 0\
Gap: High

## FR6 - Risposta Tempestiva agli Eventi (TRE)

AS-IS: - No security event logging - No monitoring - No incident
response process

SL2 Requirement: - Event logging - Alerting capability - Defined
response procedure

Assessment: SL-A ≈ 0\
Gap: High

## FR7 - Disponibilità delle Risorse (RA)

AS-IS: - No resilience evaluation - No resource exhaustion protection -
No watchdog mechanisms defined

SL2 Requirement: - Basic resilience to denial-of-service scenarios -
Availability protection mechanisms

Assessment: SL-A ≈ 0--1\
Gap: Medium

# 6. Sicurezza a Livello di Componente (IEC 62443-4-2)

PLC: - No documented hardening baseline - Default service exposure not
assessed

HMI: - No OS hardening policy - No patch governance

DUT: - API authentication not assessed - Secure configuration baseline
undefined

Component SL-C not formally determined.

Gap: Component security lifecycle absent.

# 7. Valutazione del Programma di Sicurezza (IEC 62443-2-1)

AS-IS: - No documented cybersecurity policy - No asset inventory - No
vulnerability management - No patch management - No incident response
plan - No cybersecurity roles defined

SL2 requires: - Formal security management system - Defined
responsibilities - Periodic review - Training - Change management
integration

Gap: Organizational security program not implemented.

# 8. Valutazione Complessiva del Security Level

  Foundational Requirement    SL-A (Actual)  SL-T (Target)  Gap Severity
  FR1 -- IAC                  0              2              High

  FR2 -- UC                   0              2              High

  FR3 -- SI                   0              2              High

  FR4 -- DC                   0              2              Medium

  FR5 -- RDF                  0              2              High

  FR6 -- TRE                  0              2              High

  FR7 -- RA                   0--1           2              Medium

Overall AS-IS maturity level approximates SL0--SL1.

Target maturity level: SL2.

# 9. Conclusione Esecutiva

The current industrial test bench configuration:

-   Is physically safe but cyber immature
-   Lacks defined zones and conduits
-   Has no authentication or access control model
-   Lacks integrity protection mechanisms
-   Has no security event monitoring
-   Has no formal cybersecurity governance program

To achieve SL2 compliance under IEC 62443, the TO-BE architecture must
introduce:

-   Formal zone and conduit segmentation
-   Identification and access control mechanisms
-   System integrity controls
-   Event logging and monitoring
-   Secure integration of DUT API
-   Security lifecycle governance aligned with IEC 62443-2-1

This GAP Analysis forms the formal baseline for structured migration
toward IEC 62443 SL2 compliance.
