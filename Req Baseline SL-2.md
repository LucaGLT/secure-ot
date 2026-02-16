---
tags: []
created: '2026-02-16'
title: 'Req Baseline SL-2'
---

# Requirement Baseline Matrix SL2

## Industrial Test Equipment – Derivazione Architetturale To‑Be

## 1. Premessa

Il presente documento formalizza la **Requirement Baseline Matrix per il raggiungimento del Security Level Target 2 (SL‑T = 2)** secondo IEC 62443, applicata al caso di studio relativo a un sistema di Industrial Test Equipment.

La baseline qui definita rappresenta la traduzione dei gap identificati nell’analisi AS‑IS in **requisiti architetturali To‑Be**, necessari per il conseguimento di un livello di sicurezza coerente con SL2.

Il documento non tratta aspetti organizzativi o procedurali, ma esclusivamente le implicazioni architetturali derivanti dalle Foundational Requirements (FR) rilevanti.

# 2. Foundational Requirements – SL2

## FR1 – Identification and Authentication Control (IAC)

### Stato AS‑IS

* Assenza di autenticazione strutturata su PLC e HMI.
* Assenza di identificativi utente univoci.
* Autenticazione delle API del DUT non formalizzata.

### Obiettivo SL2

* Identificazione univoca degli utenti.
* Meccanismi di autenticazione robusti.
* Gestione delle sessioni.

### Implicazioni architetturali To‑Be

* Implementazione di un sistema di autenticazione su HMI/IPC.
* Introduzione di identità per‑device per comunicazioni verso backend.
* Gestione controllata delle sessioni (timeout, rinnovo, chiusura).
* Autenticazione delle API del DUT.

## FR2 – Use Control (UC)

### Stato AS‑IS

* Nessuna separazione dei privilegi.
* Assenza di modello di ruoli.

### Obiettivo SL2

* Controllo degli accessi basato sui ruoli.
* Principio del minimo privilegio.

### Implicazioni architetturali To‑Be

* Definizione di un modello RBAC.
* Separazione tra ruoli operatore, manutentore e amministratore.
* Enforcement applicativo dei privilegi.

## FR3 – System Integrity (SI)

### Stato AS‑IS

* Nessuna verifica di integrità firmware.
* Assenza di controllo formale delle configurazioni.
* Processo di aggiornamento non strutturato.

### Obiettivo SL2

* Protezione contro modifiche non autorizzate.
* Integrità del software e delle configurazioni.
* Gestione controllata degli aggiornamenti.

### Implicazioni architetturali To‑Be

* Introduzione di Root of Trust.
* Secure Boot con verifica crittografica.
* Meccanismo di aggiornamento firmware autenticato.
* Protezione dell’integrità delle configurazioni critiche.

## FR4 – Data Confidentiality (DC)

### Stato AS‑IS

* File CSV in chiaro.
* Nessuna cifratura dati sensibili.
* Media rimovibili non controllati.

### Obiettivo SL2

* Protezione dei dati sensibili.
* Cifratura ove necessario.

### Implicazioni architetturali To‑Be

* Classificazione dei dati.
* Cifratura dei dati sensibili in transito.
* Politica di gestione e controllo dei supporti rimovibili.

## FR5 – Restricted Data Flow (RDF)

### Stato AS‑IS

* Assenza di segmentazione di rete.
* Connessione Ethernet diretta al DUT.
* Nessun controllo sui condotti di comunicazione.

### Obiettivo SL2

* Definizione formale di Zone e Conduits.
* Controllo dei flussi tra zone.

### Implicazioni architetturali To‑Be

* Formalizzazione del modello Zone & Conduits.
* Separazione tra zona di controllo, DUT, supervisione e IT.
* Introduzione di firewall o ACL.
* Controllo degli accessi remoti tramite gateway sicuro.

## FR6 – Timely Response to Events (TRE)

### Stato AS‑IS

* Assenza di logging degli eventi di sicurezza.
* Nessun sistema di monitoraggio.

### Obiettivo SL2

* Capacità di registrare eventi rilevanti.
* Possibilità di rilevazione e risposta.

### Implicazioni architetturali To‑Be

* Introduzione di logging locale degli eventi critici.
* Meccanismo di forwarding verso sistema di supervisione.
* Architettura predisposta per integrazione con processi di incident response.

## FR7 – Resource Availability (RA)

### Stato AS‑IS

* Nessuna protezione contro esaurimento risorse.
* Assenza di meccanismi di resilienza.

### Obiettivo SL2

* Resilienza base contro attacchi DoS.
* Protezione delle risorse critiche.

### Implicazioni architetturali To‑Be

* Introduzione di watchdog hardware/software.
* Meccanismi di timeout e rate limiting.
* Gestione controllata delle connessioni concorrenti.

# 3. Conclusione

La presente Requirement Baseline Matrix SL2 definisce l’insieme minimo di requisiti architetturali necessari per il passaggio dallo stato AS‑IS a un’architettura To‑Be coerente con IEC 62443 – Security Level 2.

Tutti i requisiti qui elencati devono essere tradotti in decisioni architetturali esplicite nel documento:

> “Cybersecurity Architecture Definition – Risk‑Informed Baseline for Embedded Industrial Systems”

Ogni misura architetturale dovrà essere tracciabile a una Foundational Requirement e al relativo gap identificato nell’analisi iniziale.
