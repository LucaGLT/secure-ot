# Industrial Test Bench System

## Emerging Cyber Security Challenges

### Interpretation in Relation to Functional Safety

------------------------------------------------------------------------

## 1. Introduction

The transition from an isolated, manually coordinated system to an
automated and partially connected platform introduces a fundamental
change in risk exposure.

While automation increases repeatability and reduces human operational
variability, connectivity introduces systemic cyber risks that can
directly or indirectly affect functional safety.

This document analyzes emerging cyber security issues and their
interaction with safety requirements.

------------------------------------------------------------------------

## 2. Change in Risk Nature

### AS-IS Risk Model

-   Risk dominated by human error.
-   Minimal cyber exposure due to isolation.
-   Safety primarily procedural and locally enforced.

### TO-BE Risk Model

-   Reduced manual variability.
-   Increased dependence on control logic integrity.
-   Introduction of network connectivity and remote access.
-   Emergence of malicious or accidental digital threats.

Risk shifts from individual human error to systemic vulnerability.

------------------------------------------------------------------------

## 3. New Cyber Exposure Surfaces

The introduction of supervision and remote capabilities creates new
attack vectors:

### 3.1 Supervisory Systems (HMI / SCADA)

Potential risks: - Unauthorized modification of test recipes. -
Manipulation of process parameters. - Suppression or alteration of
alarms. - False visualization of process variables.

Safety relevance: Incorrect supervisory information may delay human
intervention or lead to inappropriate decisions.

------------------------------------------------------------------------

### 3.2 Remote Access Channels

Potential risks: - Unauthorized access to control systems. - Lateral
movement from IT to OT network. - Uncontrolled configuration changes.

Safety relevance: Remote access could enable unsafe commands if not
technically constrained.

------------------------------------------------------------------------

### 3.3 Centralized Data Infrastructure

Potential risks: - Data integrity compromise. - Loss of traceability. -
Tampering with test records.

Safety relevance: Corrupted test results may validate unsafe components
or invalidate compliant ones.

------------------------------------------------------------------------

## 4. Safety and Cyber Security Interaction Model

Functional Safety ensures: - Safe state enforcement. - Deterministic
trip behavior. - Protection against foreseeable faults.

Cyber Security ensures: - Integrity of commands. - Authenticity of
users. - Confidentiality of sensitive data. - Availability of systems.

The intersection occurs where digital compromise could influence
safety-relevant behavior.

------------------------------------------------------------------------

## 5. Critical Design Principle

Safety must not depend on cyber integrity.

This means:

-   Safety logic must be independent from supervisory layers.
-   Remote systems cannot override safety interlocks.
-   Safety reset requires physical local interaction.
-   Critical thresholds are enforced in dedicated safety logic.

Cyber controls protect the process, but safety logic protects people and
equipment.

------------------------------------------------------------------------

## 6. Emerging Combined Risk Scenarios

### Scenario A: Recipe Manipulation

If an attacker modifies a pressure ramp profile, the process may exceed
safe mechanical limits.

Mitigation: - Parameter validation inside control logic. - Hard safety
thresholds independent of recipe.

------------------------------------------------------------------------

### Scenario B: Alarm Suppression

If alarms are hidden or disabled in HMI, operator reaction may be
delayed.

Mitigation: - Safety trip independent of HMI visibility. - Alarm
redundancy or hardware signaling.

------------------------------------------------------------------------

### Scenario C: Unauthorized Remote Control

If remote access is exploited, unsafe commands could be issued.

Mitigation: - Role-based access control. - Multi-factor
authentication. - Command logging and session traceability. - Network
segmentation.

------------------------------------------------------------------------

## 7. Governance Implications

The TO-BE system requires:

-   Clear separation between IT and OT domains.
-   Defined ownership of cyber security responsibilities.
-   Documented configuration management.
-   Change control procedures.
-   Validation of software updates.
-   Periodic security assessments.

Functional safety validation must consider cyber-induced hazards as part
of system-level risk analysis.

------------------------------------------------------------------------

## 8. Validation and Testing Considerations

Cyber Security Testing should include:

-   Authentication robustness testing.
-   Network segmentation verification.
-   Role-based access validation.
-   Logging and traceability checks.

Functional Safety Testing should confirm:

-   Safety trip independence from supervisory layer.
-   Safe state enforcement under abnormal digital behavior.
-   Proper response under corrupted command attempts.

Combined testing scenarios must verify that cyber compromise cannot
disable safety functions.

------------------------------------------------------------------------

## 9. Strategic Conclusion

The evolution toward automation and connectivity transforms the system
from: Human-centered safety control to System-centered deterministic
control.

This transition requires:

-   Explicit architectural separation.
-   Defense-in-depth cyber strategy.
-   Verified safety independence.
-   Integrated risk assessment covering both domains.

Cyber Security protects system integrity. Functional Safety protects
human life and physical assets.

Both must coexist without compromising each other.
