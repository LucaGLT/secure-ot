---
tags: []
created: '2026-02-16'
title: 'Zone and Conduits'
---

# Capitolo X – Zone & Conduits Model

## Conforme a IEC 62443 – Security Level 2 (SL2)

## 1. Scopo del Capitolo

Il presente capitolo definisce il **modello formale di Zone & Conduits** per l’Industrial Test Equipment oggetto del caso di studio.

Il modello è costruito in coerenza con:

* IEC 62443-3-2 (Risk Assessment & System Design)
* IEC 62443-3-3 (System Security Requirements – SL2)
* Le indicazioni del Capitolo 8 del caso di studio

L’obiettivo è:

* Separare logicamente e funzionalmente gli elementi del sistema
* Limitare la propagazione di una compromissione
* Controllare esplicitamente i flussi di comunicazione
* Costituire la base architetturale per il raggiungimento di SL2

Il modello Zone & Conduits rappresenta un elemento strutturale dell’architettura To-Be.

# 2. Principi di Segmentazione

Il modello è costruito secondo i seguenti principi:

* Separazione tra dominio OT e dominio IT
* Separazione tra funzioni di controllo e funzioni di supervisione
* Isolamento del DUT (Device Under Test) come entità distinta
* Controllo esplicito di ogni flusso dati tra domini
* Assunzione che ogni zona sia non trusted rispetto alle altre

La segmentazione è sia:

* Logica (VLAN, firewall, ACL)
* Fisica dove necessario

# 3. Definizione delle Zone

## 3.1 Zona Z1 – Controllo

Comprende:

* PLC
* IPC / HMI
* Componenti di controllo del banco

Caratteristiche:

* Funzione critica per l’operatività del sistema
* Elevato impatto in caso di compromissione
* Accesso limitato a personale autorizzato

Requisiti SL2 associati:

* FR1 (autenticazione utenti)
* FR2 (RBAC)
* FR3 (integrità software e configurazioni)
* FR6 (logging eventi critici)

## 3.2 Zona Z2 – DUT (Device Under Test)

Comprende:

* Dispositivo oggetto di test
* API di comunicazione verso il sistema di controllo

Caratteristiche:

* Entità potenzialmente non trusted
* Superficie di attacco diretta tramite Ethernet

Requisiti SL2 associati:

* FR1 (autenticazione API)
* FR3 (integrità comunicazioni)
* FR5 (controllo flussi verso Z1)

::: {custom-style="b-note"}
Nota architetturale:
Il DUT non deve poter influenzare direttamente la zona di controllo senza attraversare un conduit controllato.
:::

## 3.3 Zona Z3 – Supervisione / Storage

Comprende:

* Storage locale
* Eventuale server di supervisione futuro

Caratteristiche:

* Contiene dati di test
* Può interfacciarsi con IT aziendale

Requisiti SL2 associati:

* FR4 (protezione dati)
* FR6 (event logging e forwarding)
* FR5 (segmentazione verso IT)

## 3.4 Zona Z4 – IT Enterprise

Comprende:

* Rete aziendale
* Backend
* Sistemi remoti di manutenzione

Caratteristiche:

* Considerata non trusted rispetto al dominio OT
* Accesso remoto controllato

Requisiti SL2 associati:

* FR5 (restricted data flow)
* FR1 (autenticazione device-server)

# 4. Definizione dei Conduits

Ogni comunicazione tra zone avviene esclusivamente tramite conduits definiti e controllati.

## 4.1 Conduit C1 – Z1 ↔ Z2

* Protocollo controllato
* Autenticazione reciproca
* Limitazione delle funzioni esposte
* Logging delle interazioni

Obiettivo: impedire che un DUT compromesso possa compromettere la zona di controllo.

## 4.2 Conduit C2 – Z1 ↔ Z3

* Trasferimento controllato dei dati di test
* Controllo integrità
* Logging

## 4.3 Conduit C3 – Z3 ↔ Z4

* Firewall o gateway dedicato
* Accesso remoto autenticato
* Segmentazione IT/OT
* Monitoraggio traffico

## 4.4 Conduit C4 – Accesso manutenzione

* Accesso temporaneo
* Autenticazione forte
* Tracciabilità completa

# 5. Regole Generali sui Flussi

* Nessuna comunicazione diretta tra Z2 e Z4
* Nessuna comunicazione non autenticata tra zone
* Ogni flusso deve essere esplicitamente giustificato
* Le porte non utilizzate devono essere chiuse

# 6. Collegamento con le Foundational Requirements

Il modello Zone & Conduits contribuisce direttamente al soddisfacimento di:

* FR5 – Restricted Data Flow
* FR1 – Identification & Authentication
* FR2 – Use Control
* FR6 – Timely Response to Events
* FR7 – Resource Availability

La segmentazione rappresenta la misura architetturale primaria per ridurre la superficie d’attacco e limitare la propagazione laterale.

# 7. Conclusione

Il modello Zone & Conduits qui definito costituisce la struttura portante dell’architettura To-Be.

Ogni ulteriore misura (Secure Boot, Identity, Logging, Hardening) deve essere implementata nel rispetto di questa segmentazione.

Il modello è coerente con SL2 e con le indicazioni del Capitolo 8 del caso di studio.

---
