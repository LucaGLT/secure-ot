# Industrial Test Bench System

## AS-IS System Description

------------------------------------------------------------------------

## 1. Overview

The current system consists of multiple industrial test benches used for
mechanical component verification under critical pressure and
temperature conditions.\
The control architecture is primarily based on local PLC systems with no
remote connectivity.

Operations are predominantly manual and coordinated directly by
operators.

------------------------------------------------------------------------

## 2. Control Architecture

### 2.1 PLC-Based Local Control

-   Each subsystem (pressure, temperature, data acquisition) is
    controlled locally.
-   PLCs execute basic sequential logic.
-   Controllers may operate as stand-alone units.
-   There is no centralized orchestration logic.

### 2.2 Lack of Remote Access

-   No remote supervision via PC or tablet.
-   No external connectivity to enterprise or external networks.
-   System is effectively isolated from IT infrastructure.

------------------------------------------------------------------------

## 3. Operational Workflow

### 3.1 Test Execution

Operators are responsible for:

-   Manually starting each subsystem.
-   Synchronizing pressure, temperature, and acquisition phases.
-   Monitoring test evolution.
-   Identifying abnormal conditions.
-   Deciding when to stop the test.

Coordination is operator-driven rather than system-driven.

### 3.2 End-of-Test Activities

At the end of each test:

-   Data is manually extracted from individual instruments.
-   Files are collected separately.
-   Data is aggregated manually.

There is no automatic correlation between test ID, component ID, and
measurement data.

------------------------------------------------------------------------

## 4. Data Management and Reporting

-   Data is processed manually.
-   Reports are created using spreadsheets (e.g., Excel).
-   Copy-paste and manual calculations are common.
-   Traceability depends on operator discipline.
-   There is no centralized repository or structured database.

------------------------------------------------------------------------

## 5. Safety Characteristics (Current State)

-   Safety relies primarily on:
    -   Operator awareness
    -   Basic hardware protections
    -   Local interlocks (if present)
-   No centralized safety orchestration.
-   No automated global validation of process states.

Safety is strongly dependent on human supervision.

------------------------------------------------------------------------

## 6. Cyber Security Exposure (Current State)

-   Minimal attack surface due to system isolation.
-   No remote access.
-   No external network connectivity.
-   No centralized digital infrastructure to compromise.

Cyber risk is currently low because connectivity is absent.

------------------------------------------------------------------------

## 7. Responsibility Model (AS-IS)

### Operator Responsibilities

-   System coordination
-   Parameter verification
-   Manual synchronization
-   Anomaly detection
-   Data extraction
-   Report creation
-   Final validation

The operator acts as the primary process orchestrator.

### System Responsibilities

-   Execute local control logic
-   Apply manually configured setpoints
-   Generate raw measurement data
-   Trigger basic local protections

The system executes but does not govern the overall process.

------------------------------------------------------------------------

## 8. Key Observations

-   High dependence on human expertise.
-   Limited repeatability.
-   Manual data handling.
-   Low cyber exposure.
-   Safety primarily procedural rather than systemic.
