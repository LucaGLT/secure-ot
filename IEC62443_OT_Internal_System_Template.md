# IEC 62443 Documentation Template

## Internal OT Systems (Test Benches, Pilot Lines, Industrial Labs)

Version: 0.1\
Date: 2026-03-07

------------------------------------------------------------------------

# 1. Scope of this Documentation Set

This template supports the documentation of **internal OT systems** such
as:

- Industrial test benches
- Pilot production lines
- Industrial laboratories
- Engineering test environments
- R&D automation setups

It aligns with the following standards:

- IEC 62443‑2‑1 --- Security Program Requirements for IACS Asset
    Owners
- IEC 62443‑3‑2 --- Security Risk Assessment for System Design
- IEC 62443‑3‑3 --- System Security Requirements and Security Levels

The goal is to demonstrate **Security by Design** and **Security
Governance** for internal OT environments.

------------------------------------------------------------------------

# 2. Security Level Context

The depth of documentation depends on the **Target Security Level
(SL‑T)**.

 
  --------------------------
  SL1  :  Protection against casual or accidental    
 misuse   :  Basic documentation

  SL2 :   Protection against   intentional violation   with moderate resources :
Structured documentation

  SL3   :   Protection against   sophisticated attackers : Full documentation set

  SL4  :   Protection against highly capable adversaries : Extended validation and penetration testing
  

------------------------------------------------------------------------

# 3. Required Documentation Set

## 3.1 System Description

**Normative reference**\
IEC 62443‑3‑2 §4

**Purpose**\
Provide a clear description of the OT system and its boundaries.

**Recommended when** - Always required (all SL)

**Minimum content**

- System purpose
- Operational environment
- System boundaries
- Interfaces with IT networks
- Safety‑relevant functions
- Network technologies (LAN, WiFi)

**Typical structure**

    - System Overview
    - Operational Context
    - Physical Architecture
    - Logical Architecture
    - Interfaces with Corporate IT
    - Safety Functions

------------------------------------------------------------------------

## 3.2 Asset Inventory

**Normative reference**\
IEC 62443‑2‑1 §4.3.3

**Purpose**\
Identify all assets relevant to cybersecurity.

**Recommended when** - SL1--SL4

**Minimum content**

- PLC / controllers
- Industrial PCs
- Test software
- Safety controllers
- Sensors and actuators
- Network equipment
- Wireless infrastructure

**Example table**

  Asset   Type   Firmware   Network Zone   Safety Critical
  ------- ------ ---------- -------------- -----------------

------------------------------------------------------------------------

## 3.3 Security Risk Assessment

**Normative reference**\
IEC 62443‑3‑2

**Purpose**\
Identify threats and determine **Target Security Levels (SL‑T)**.

**Recommended when** - Mandatory from SL2

**Minimum content**

- Threat identification
- Vulnerability analysis
- Impact analysis
- Safety interaction analysis
- Determination of SL‑T

**Example risk structure**

  Threat   Impact   Likelihood   Risk   Mitigation
  -------- -------- ------------ ------ ------------

------------------------------------------------------------------------

## 3.4 Zones and Conduits Architecture

**Normative reference**\
IEC 62443‑3‑2 §5

**Purpose**\
Define network segmentation and security boundaries.

**Recommended when** - Mandatory SL2+

**Minimum content**

- Zone definition
- Trust levels
- Communication paths
- Security controls per conduit

Example architecture:

    Corporate IT
         |
    Firewall
         |
    Industrial DMZ
         |
    Test Lab Network
         |
    Control & Safety Devices

------------------------------------------------------------------------

## 3.5 System Security Requirements Specification

**Normative reference**\
IEC 62443‑3‑3

**Purpose**\
Translate risk assessment results into **security requirements**.

**Recommended when** - Mandatory SL2+

Requirements must be derived from the **7 Foundational Requirements**:

- FR1 Identification and Authentication
- FR2 Use Control
- FR3 System Integrity
- FR4 Data Confidentiality
- FR5 Restricted Data Flow
- FR6 Timely Response to Events
- FR7 Resource Availability

Example requirement entry:

  ID   FR   Requirement   SL
  ---- ---- ------------- ----

------------------------------------------------------------------------

## 3.6 Security Architecture Description

**Normative reference**\
IEC 62443‑3‑3

**Purpose**\
Describe how the security requirements are implemented.

**Recommended when** - SL2--SL4

**Minimum content**

- Network segmentation
- Authentication architecture
- WiFi security model
- Firewall configuration principles
- Remote access model

------------------------------------------------------------------------

## 3.7 Secure Configuration / Hardening Guide

**Normative reference**\
IEC 62443‑3‑3 / IEC 62443‑2‑1

**Purpose**\
Define secure configuration rules for system components.

**Recommended when** - SL2--SL4

Examples:

- PLC password policies
- Network switch configuration
- Wireless encryption requirements
- Service hardening

------------------------------------------------------------------------

## 3.8 Security Verification and Validation

**Normative reference**\
IEC 62443‑3‑3

**Purpose**\
Demonstrate that security requirements are satisfied.

**Recommended when** - SL2--SL4

Validation activities may include:

  Activity                      SL1   SL2   SL3   SL4
  ----------------------------- ----- ----- ----- -----
  Configuration verification    ✔     ✔     ✔     ✔
  Security functional testing   ✔     ✔     ✔     ✔
  Vulnerability scanning              ✔     ✔     ✔
  Penetration testing                       ✔     ✔
  Red‑team exercise                               ✔

------------------------------------------------------------------------

## 3.9 Vulnerability Management Procedure

**Normative reference**\
IEC 62443‑2‑1

**Purpose**\
Define how vulnerabilities are monitored and mitigated.

**Recommended when** - SL2--SL4

Content:

- Vulnerability monitoring sources
- Patch management policy
- Firmware update process
- Risk acceptance process

------------------------------------------------------------------------

## 3.10 Incident Response Procedure

**Normative reference**\
IEC 62443‑2‑1

**Purpose**\
Define response to cybersecurity incidents.

**Recommended when** - SL2--SL4

Content:

- Incident classification
- Isolation procedures
- Recovery strategy
- Communication plan

------------------------------------------------------------------------

# 4. Minimal Documentation Set for Internal Test Systems

Typical recommended baseline for **industrial test benches**:

SL1:

- System Description
- Asset Inventory

SL2:

- Risk Assessment
- Zones & Conduits Diagram
- Security Requirements

SL3:

- Security Architecture
- Hardening Guide
- Security Validation Report

SL4:

- Advanced penetration testing
- Continuous monitoring plan

------------------------------------------------------------------------

# 5. Relationship with Safety

When safety functions are present, cybersecurity documentation should
consider:

- impact of cyber attacks on safety functions
- manipulation of sensors
- bypass of safety interlocks
- loss of availability of safety controllers

Relevant safety standards may include:

- IEC 61508
- ISO 13849
- IEC 62061

Cybersecurity must ensure that **safety integrity is not compromised by
cyber attacks**.

------------------------------------------------------------------------

# 6. Document Control

Document Owner:\
Security Architect / OT System Owner

Approval:\
Engineering Manager\
Cybersecurity Lead

Review cycle:

- annually
- after major system change
- after security incident
