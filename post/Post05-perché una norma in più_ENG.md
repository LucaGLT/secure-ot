---
tags: []
created: '2026-03-01'
title: 'why one more standard'
---

# Why did we need IEC 62443 in Industrial Control Systems and Operational Technology?

In recent years, **Cybersecurity** has become a central topic also in **embedded systems** and **industrial environments**. However, one question often comes up among technical professionals:

> If there is already extensive cybersecurity literature in IT, why was a specific standard like IEC 62443 needed for Operational Technology (OT) and Industrial Automation and Control Systems (IACS)?

**IEC 62443**, born as the ISA-99 standard in 2002 and later adopted as an international standard, is now the **main reference for industrial control system security**.

The answer is not purely technical. It is architectural and systemic.

## IT and OT share principles, not context

In the IT world, we have built decades of experience around:

* authentication
* cryptography
* PKI
* network segmentation
* zero trust
* vulnerability management
* continuous monitoring

These principles are also valid in OT. **But the operating context is radically different**.

It is true: critical systems also exist in IT (banks, e-commerce, cloud infrastructure). But those systems are natively designed with:

* massive redundancy
* advanced segmentation
* continuous monitoring with dedicated teams (SOC)
* distributed orchestration

An IT system is generally:

* dynamic
* frequently updatable
* replicable
* virtualized
* monitored 24/7

Many embedded industrial systems are not born with these characteristics:

* they cannot be patched frequently
* they are not cloud-native
* they are neither replicable nor virtualizable
* they have very long life cycles

An embedded OT system is often:

* **deterministic real-time**: it must guarantee fixed and predictable response times, making it difficult to introduce security controls that add latency (e.g., deep packet inspection, behavioral analysis)
* **ultra-long life cycle (10–20 years)**: it must be designed secure by design from the beginning, because vulnerabilities discovered years later may never be patched
* **hard to update**: an update requires planned plant downtime, full regression testing, safety validation, and specialist skills
* **physically exposed**: accessible to field personnel, maintainers, and third-party vendors, often in unmonitored environments
* **without a dedicated Security Operations Center (SOC)**: it does not have continuous 24/7 threat monitoring as in enterprise datacenters

Applying IT cybersecurity "as is" means ignoring these structural differences.

## In OT, security does not protect only data

In IT, cybersecurity mainly protects:

* information
* digital services
* logical infrastructure

In OT, software directly controls **critical physical processes**:

* **pressure valves** in natural gas pipelines
* **power distribution systems** in transmission grids
* **motors and robots** on automotive production lines
* **dosing pumps** in chemical and pharmaceutical plants
* **HVAC systems** in hospitals and data centers
* **crane drives and heavy machinery** in industrial facilities

In other words: software does not only process information, it **commands actuators that move, heat, pressurize, dose substances, and open electrical circuits**.

A cyber attack can therefore turn into:

* physical damage
* plant shutdown
* measurement alteration
* risk to operators

This is where an element that is marginal in enterprise IT becomes central:
> the interaction between **Security** and **Safety**.

In OT, a malicious attack can generate the same effect as an accidental failure. For this reason, **Security** and **Safety** must be designed in a coordinated way.

## Practical example: IT vs OT

To better understand this distinction, let’s compare two real scenarios:

* a compromised web server in a bank
* and a compromised PLC in a chemical plant

Both are **serious** incidents, with potentially devastating economic impacts. But the nature of the damage is radically different.

In the first case, the attack compromises confidentiality and integrity of information: stolen credentials, exposed financial data, GDPR violations with multi-million penalties, reputational loss. The organization can respond with established incident response procedures, restoring from backup and implementing remediation. The damage is mainly **economic and reputational**.

In the second case, the attack can alter the behavior of a system controlling hazardous physical processes: a valve that fails to close, a temperature that exceeds critical thresholds, a chemical reaction out of control. The result may be an explosion, environmental contamination, injuries, or fatalities. The damage is **physical, immediate, and irreversible**.

The difference is not in **severity**, but in the **nature** of the impact:

| Scenario | Type of damage | Recovery timeline |
|----------|----------------|-------------------|
| **Compromised banking web server** | Financial data theft, GDPR violation, reputational loss, multi-million penalties | Restore from backup, remediation: days/weeks; years for reputational recovery |
| **Compromised PLC in a chemical plant** | Explosion risk, environmental contamination, injuries/fatalities, irreversible damage | Mandatory plant shutdown, safety inspection, hardware replacement: weeks/months; years for environmental impacts |

Both are **serious** incidents. But in OT:
* impact can be **physical and irreversible**
* **human lives** are directly at risk
* there is no backup for people’s safety
* response requires **coordination with safety authorities** (not only cyber)

IEC 62443 must therefore integrate with safety standards such as IEC 61508 (functional safety) and IEC 61511 (process industry safety), ensuring that security measures do not compromise safety functions and that incident management considers both domains.

## The real logical leap of IEC 62443

IEC 62443 does not reinvent cryptography, does not introduce new algorithms, and does not replace IT best practices.

It introduces something different:

> IEC 62443 creates an architectural model to design security in industrial systems.

## Structure of the standard

IEC 62443 is organized into four main groups, **each intended for a specific actor**:

* **Part 1 - General**: defines common language, conceptual models, and cross-cutting principles (terminology, metrics, assets, threat model), so that all actors assess risk using the same criteria.
* **Part 2 - Policies and procedures**: guides the **Asset Owner** in security governance (roles, processes, life-cycle management, supplier management, incident management, continuous improvement).
* **Part 3 - System**: translates risk into architectural requirements for the **System Integrator** (zones and conduits, SL-T assignment, system requirements, technical validation, and gap analysis).
* **Part 4 - Components**: specifies requirements the **Product Supplier** must implement in products (secure development lifecycle, hardening, authentication, logging, patchability, compliance evidence).

This distinction of responsibilities is fundamental: **each actor has specific and measurable obligations**.

## Key concepts

### Zones and Conduits

> A **Zone** is a logical or physical grouping of assets with common security requirements.

In practice, **Zones** are used to separate domains with different criticality levels (for example: corporate IT network, operations supervision, PLC control level), preventing all devices from sharing the same "trust space".

> A **Conduit** is the controlled communication channel between two zones.

**Conduits** define *how* these domains can communicate: which protocols are allowed, in which direction, and with which authentication, filtering, and monitoring controls.

This approach limits lateral movement: if one asset is compromised in a zone, the attacker cannot move freely across all others.

### Security Level (SL)

The standard defines **4 Security Levels** (from SL-1 to SL-4), based on attacker capability:

* **SL-1**: protection against casual or accidental violations
* **SL-2**: protection against attackers with limited resources and generic skills
* **SL-3**: protection against attackers with moderate resources and system-specific skills
* **SL-4**: protection against attackers with extensive resources and advanced skills (nation-state)

Each zone has:

* an **SL-T** (Security Level Target): required level
* an **SL-A** (Security Level Achieved): actually implemented level

### Foundational Requirements (FR)

The **7 Foundational Requirements** are the control areas through which IEC 62443 translates security into verifiable requirements:

1. **FR1 - Identification and Authentication Control**: ensures that users, devices, and applications are identified and authenticated before accessing the system.
2. **FR2 - Use Control**: defines which actions are allowed for each authenticated subject (least-privilege principle).
3. **FR3 - System Integrity**: protects logic, software, configurations, and firmware from unauthorized or malicious modifications.
4. **FR4 - Data Confidentiality**: protects confidentiality of sensitive information in transit, at rest, and during access.
5. **FR5 - Restricted Data Flow**: limits and governs communications between zones and conduits, reducing lateral movement and attack surfaces.
6. **FR6 - Timely Response to Events**: enables timely detection, logging, alerting, and response to security events.
7. **FR7 - Resource Availability**: ensures operational continuity and system resilience even in the presence of failures or attacks.

Each FR is broken down into specific **System Requirements (SR)** and **Component Requirements (CR)**.

### Defense in Depth

The standard adopts the **Defense in Depth** principle: security does not rely on a single control, but on multiple independent layers. If one layer is compromised, others continue to protect the system.

Security is no longer just a set of mechanisms (passwords, TLS, firewalls), but a structural property of the architecture.

## From component protection to domain protection

Traditional IT cybersecurity tends to protect endpoints and services.

IEC 62443 shifts focus to:

* trust domains
* architectural boundaries
* flow control between zones
* containment of lateral movement

It is not about protecting a single device such as "the PLC" or "the HMI," nor a single data item.
It is about defining **what security level a Zone must have** and **which controls must govern every boundary crossing (Conduits)**.

This makes it possible to:

* assign a Security Level Target (SL-T)
* measure a Security Level Achieved (SL-A)
* perform formal gap analyses
* demonstrate consistency between risk and architecture

At this point, one key limitation becomes clear: **Passwords** and **TLS** are necessary, but not sufficient, and they cover only part of the problem:

* authentication
* confidentiality

OT security, however, requires architectural answers to questions such as:

* How do I limit propagation from a compromised device?
* How do I separate the Information domain (IT) from the Operational domain (OT)?
* How do I manage temporary maintenance access?
* How do I formally assign a protection level to a part of the system?

**Without an architectural model, security remains fragmented**.

## Conclusion

IEC 62443 does not replace IT Cybersecurity. It integrates it and adapts it to a different context.

It is not "one more standard." It is a necessary design model for IACS and industrial systems that govern physical processes.

> IEC 62443 provides an architectural model and helps design OT systems that remain secure (Security and Safety), even when a cyber attack becomes a physical event.

* The IEC 62443 standard covers the entire **lifecycle**: design, implementation, maintenance, decommissioning
* It defines roles and responsibilities for **Asset Owner**, **System Integrator**, and **Product Supplier**
* It is complementary to Functional Safety standards (IEC 61508, IEC 61511)

And this is the logical and strategic leap that makes the standard necessary in **Industrial Control Systems** and **Operational Technology**.
