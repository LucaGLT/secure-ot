## Analisi Formale dei GAP secondo IEC 62443

### 1. Scopo del Documento

Questo documento fornisce un'analisi formale dei GAP dell'architettura attuale AS-IS
del test bench industriale rispetto ai requisiti dello standard IEC
62443.

L'obiettivo è:

- Definire lo scope del sistema valutato
- Identificare zone e condotti
- Determinare il Security Level Target (SL-T)
- Valutare l'Actual Security Level (SL-A)
- Identificare i gap rispetto ai Foundational Requirements IEC 62443-3-3
- Evidenziare i controlli programmatici mancanti (IEC 62443-2-1)
- Identificare i gap a livello di componente (IEC 62443-4-2)

Questo report è strutturato in allineamento con la metodologia di assessment
IEC 62443.

### 2. Spiegazione dei Termini Chiave di IEC 62443

Per chiarezza, le seguenti abbreviazioni sono utilizzate in questo report:

**SL (Security Level)**
Un livello definito di resistenza contro un profilo di minaccia definito.

**SL-T (Target Security Level)**
Il Security Level richiesto determinato attraverso un risk assessment (IEC
62443-3-2).

**SL-A (Achieved or Actual Security Level)**
Il Security Level attualmente raggiunto dal sistema nella sua configurazione
AS-IS.

**SL-C (Capability Security Level)**
Il Security Level che i componenti del sistema sono in grado di raggiungere quando
adeguatamente configurati.

**FR (Foundational Requirement)**
Una delle sette categorie di requisiti di sicurezza di alto livello definite in
IEC 62443-3-3.

Le sette categorie FR sono:

- FR1 -- Identification and Authentication Control (IAC)
- FR2 -- Use Control (UC)
- FR3 -- System Integrity (SI)
- FR4 -- Data Confidentiality (DC)
- FR5 -- Restricted Data Flow (RDF)
- FR6 -- Timely Response to Events (TRE)
- FR7 -- Resource Availability (RA)

### 3. Definizione del Sistema (IEC 62443-3-2)

#### 3.1 Asset Identificati (AS-IS)

- PLC (Siemens S7-1200)
- HMI locale
- Controllore di temperatura (stand-alone)
- Datalogger stand-alone
- DUT (Device Under Test) con capacità API Ethernet
- Catena relè di sicurezza (non rilevante dal punto di vista cyber ma critica per la sicurezza)
- Postazione operatore (creazione report offline)

Non esiste un'architettura di rete OT formalmente definita nella configurazione
AS-IS.

#### 3.2 Modello Preliminare di Zone (Concettuale)

Zona Z1 -- Zona di Controllo Base

- PLC
- HMI
- Controllore di temperatura
- Datalogger

Zona Z2 -- Zona DUT

- Dispositivo DUT
- Interfaccia Ethernet

Zona Z3 -- Zona Supervisiva Futura (TO-BE)

- IPC / SCADA
- Repository dati centrale

Zona Z4 -- Zona IT Enterprise

- PC per reportistica
- Rete aziendale

I condotti in AS-IS sono principalmente fisici/manuali (USB, SD, cavo Ethernet
diretto).
Nessun condotto logico o segmentazione sono formalmente definiti.

### 4. Determinazione del Security Level Target

Basato su:

- Esposizione dell'ambiente industriale
- Probabilità moderata di abuso o manomissione
- Presenza di implicazioni di sicurezza
- Nessun modello di minaccia avanzato nation-state

Il Security Level Target raccomandato è:

#### SL-T = 2

SL2 fornisce protezione contro:

- Violazioni intenzionali utilizzando mezzi semplici
- Attaccanti con risorse limitate
- Malware generico
- Scenari di abuso da parte di insider

### 5. IEC 62443-3-3 Foundational Requirement Assessment

#### FR1 -- Identification & Authentication Control (IAC)

AS-IS: - Nessuna autenticazione strutturata su PLC/HMI - Nessuna identità utente
unica - Autenticazione API DUT non definita

Requisito SL2: - ID utente univoci - Meccanismi di autenticazione - Controllo
sessione

Valutazione: SL-A ≈ 0
Gap: Alto

#### FR2 - Controllo d'Uso (UC)

AS-IS: - Nessun controllo accessi basato sui ruoli - Nessuna separazione dei
privilegi

Requisito SL2: - Controllo accessi basato sui ruoli (RBAC) - Principio del minimo
privilegio

Valutazione: SL-A ≈ 0
Gap: Alto

#### FR3 - Integrità del Sistema (SI)

AS-IS: - Nessuna verifica di integrità - Nessuna gestione formale della
configurazione - Nessun processo di aggiornamento controllato

Requisito SL2: - Protezione contro modifiche non autorizzate -
Meccanismi di garanzia dell'integrità - Procedure di aggiornamento controllate

Valutazione: SL-A ≈ 0
Gap: Alto

#### FR4 - Riservatezza dei Dati (DC)

AS-IS: - Dati memorizzati in CSV in chiaro - Nessuna crittografia - Media
rimovibili non controllati

Requisito SL2: - Protezione dei dati sensibili - Crittografia dove
richiesto

Valutazione: SL-A ≈ 0
Gap: Medio

#### FR5 - Flussi di Dati Limitati (RDF)

AS-IS: - Nessuna segmentazione di rete - Nessun firewall o controllo condotti -
Accesso Ethernet diretto al DUT

Requisito SL2: - Zone definite - Condotti controllati - Segmentazione
logica

Valutazione: SL-A ≈ 0
Gap: Alto

#### FR6 - Risposta Tempestiva agli Eventi (TRE)

AS-IS: - Nessun logging degli eventi di sicurezza - Nessun monitoraggio - Nessun
processo di risposta agli incidenti

Requisito SL2: - Event logging - Capacità di allerta - Procedura di
risposta definita

Valutazione: SL-A ≈ 0
Gap: Alto

#### FR7 - Disponibilità delle Risorse (RA)

AS-IS: - Nessuna valutazione di resilienza - Nessuna protezione dall'esaurimento
delle risorse - Nessun meccanismo watchdog definito

Requisito SL2: - Resilienza di base a scenari denial-of-service -
Meccanismi di protezione della disponibilità

Valutazione: SL-A ≈ 0--1
Gap: Medio

### 6. Sicurezza a Livello di Componente (IEC 62443-4-2)

PLC: - Nessuna baseline di hardening documentata - Esposizione dei servizi di
default non valutata

HMI: - Nessuna policy di hardening OS - Nessuna governance delle patch

DUT: - Autenticazione API non valutata - Baseline di configurazione sicura
non definita

SL-C dei componenti non formalmente determinato.

Gap: Ciclo di vita della sicurezza dei componenti assente.

### 7. Valutazione del Programma di Sicurezza (IEC 62443-2-1)

AS-IS: - Nessuna policy di cybersecurity documentata - Nessun inventario degli
asset - Nessuna gestione delle vulnerabilità - Nessuna gestione delle patch - Nessun
piano di risposta agli incidenti - Nessun ruolo di cybersecurity definito

SL2 richiede: - Sistema formale di gestione della sicurezza - Responsabilità
definite - Revisione periodica - Formazione - Integrazione della gestione
delle modifiche

Gap: Programma di sicurezza organizzativo non implementato.

### 8. Valutazione Complessiva del Security Level

| Foundational Requirement | SL-A (Actual) | SL-T (Target) | Gap Severity |
|--------------------------|---------------|---------------|--------------|
| FR1 -- IAC               | 0             | 2             | High         |
| FR2 -- UC                | 0             | 2             | High         |
| FR3 -- SI                | 0             | 2             | High         |
| FR4 -- DC                | 0             | 2             | Medium       |
| FR5 -- RDF               | 0             | 2             | High         |
| FR6 -- TRE               | 0             | 2             | High         |
| FR7 -- RA                | 0--1          | 2             | Medium       |

Il livello di maturità complessivo AS-IS approssima SL0--SL1.

Livello di maturità target: SL2.

### 9. Conclusione Esecutiva

La configurazione attuale del test bench industriale:

- È fisicamente sicura ma cyber-immatura
- Manca di zone e condotti definiti
- Non ha un modello di autenticazione o controllo accessi
- Manca di meccanismi di protezione dell'integrità
- Non ha monitoraggio degli eventi di sicurezza
- Non ha un programma formale di governance della cybersecurity

Per raggiungere la conformità SL2 secondo IEC 62443, l'architettura TO-BE deve
introdurre:

- Segmentazione formale di zone e condotti
- Meccanismi di identificazione e controllo accessi
- Controlli di integrità del sistema
- Event logging e monitoraggio
- Integrazione sicura dell'API del DUT
- Governance del ciclo di vita della sicurezza allineata a IEC 62443-2-1

Questa analisi GAP costituisce la baseline formale per la migrazione strutturata
verso la conformità IEC 62443 SL2.
