## Descrizione Interfacce e Flussi di Dati AS-IS

### 1. Scopo

Questo documento mappa le **interfacce** e i **flussi di dati** dell'architettura attuale (AS-IS) del test bench industriale, includendo:

- Interfacce di controllo (segnali e percorsi di comando)
- Percorsi di misurazione
- Percorsi di logging/esportazione dati
- Interfacce dati del Device Under Test (DUT) (compresa l'API attualmente non utilizzata)

L'obiettivo è fornire una baseline concreta per derivare i requisiti architetturali TO-BE.

## 2. Confini del Sistema (AS-IS)

Asset inclusi:

- PLC (controllo locale)
- HMI locale
- Sottosistema pressione (pompa, valvole, trasduttore di pressione, pressostato meccanico)
- Sottosistema temperatura (controllore stand-alone + camera/riscaldatore)
- Datalogger stand-alone
- DUT con intelligenza onboard e logging
- Azioni dell'operatore (coordinamento manuale ed estrazione dati)

Escluso (AS-IS):

- Accesso remoto (supervisione PC/tablet)
- Server centrale / historian / database
- Pipeline di generazione report automatizzata
- Segmentazione rete OT (nessuna rete OT in pratica)

## 3. Mappa delle Interfacce (Fisiche / Logiche)

### 3.1 Interfacce di Controllo e Sicurezza (Segnali)

| ID Interfaccia | Da | A | Tipo | Segnale/Protocollo | Scopo | Note |
|----------------|----|----|------|-------------------|-------|------|
| IF-01 | HMI | PLC | Fieldbus | Profinet (HMI runtime) | Inserimento comandi operatore, setpoint | Solo locale |
| IF-02 | PLC | Pompa | Digitale | DO (24V) | Avvio/Arresto pompa | Via contattore/relè |
| IF-03 | PLC | Valvola di scarico | Digitale | DO (24V) | Apertura/Chiusura controllata depressurizzazione | La catena di sicurezza può sovrascrivere via rimozione potenza |
| IF-04 | PLC | Valvola proporzionale (opzionale) | Analogico | AO 4-20 mA | Comando regolazione pressione | Solo se installato |
| IF-05 | Trasduttore pressione | PLC | Analogico | AI 4-20 mA | Misurazione pressione | PLC usa per controllo di processo/allarmi |
| IF-06 | Pressostato meccanico | Catena relè sicurezza | Digitale | Contatto pulito | Rilevamento sovrappressione indipendente | Cablaggio diretto |
| IF-07 | E-Stop | Catena relè sicurezza | Digitale | Contatto pulito | Arresto emergenza | Cablaggio diretto |
| IF-08 | Interlock porta | Catena relè sicurezza | Digitale | Contatto pulito | Sicurezza protezioni | Cablaggio diretto |
| IF-09 | Catena relè sicurezza | Alimentazione pompa/riscaldatore | Potenza | Controllo contattore sicurezza | Rimozione energia ad attuatori pericolosi | Indipendente da PLC |
| IF-10 | Controllore temp | Camera/Riscaldatore | Locale | I/O vendor | Attuazione temperatura | Interno al sottosistema temp |
| IF-11 | PLC | Controllore temp | Digitale | DI/DO contatto pulito | Stato RUN/READY/FAULT e abilitazione semplice | Nessun coordinamento profili |
| IF-12 | Sensori temp | Controllore temp | Analogico | PT100/TC | Misurazione temperatura | Non acquisito da PLC in AS-IS |

### 3.2 Interfacce di Acquisizione Dati (Da Misura a Logger)

| ID Interfaccia | Da | A | Tipo | Segnale/Protocollo | Dati | Note |
|----------------|----|----|------|-------------------|------|------|
| IF-20 | Trasduttore pressione (o mirror PLC) | Datalogger | Analogico | 4-20 mA / 0-10V | Trend pressione | Cablaggio logger varia per banco |
| IF-21 | Controllore temp (uscita analogica) o sonda dedicata | Datalogger | Analogico | 4-20 mA / Modulo PT100/TC | Trend temperatura | Spesso canali separati |
| IF-22 | Sensori ausiliari (se presenti) | Datalogger | Misto | Analogico/Digitale | Segnali opzionali | Non standardizzato |                                                       

### 3.3 Interfacce di Esportazione Dati (File)

| ID Interfaccia | Da | A | Supporto | Formato | Tempistica | Note |
|----------------|----|----|----------|---------|------------|------|
| IF-30 | Datalogger | Operatore | SD / USB | CSV | Fine test | Estrazione manuale |
| IF-31 | HMI (valori) | Operatore | Manuale | Note / foto / copia manuale | Qualsiasi momento | Spesso non strutturato |
| IF-32 | Controllore temp | Operatore | USB / esportazione locale | CSV / proprietario | Fine test o per batch | Dipendente dal vendor |
| IF-33 | DUT | Operatore | Scheda SD | File log (CSV/proprietario) | Fine test (dopo finalizzazione log) | Rimozione manuale |
| IF-34 | DUT | Operatore | Ethernet (diretto) | Trasferimento file (SMB/FTP/HTTP download) | Fine test (dopo finalizzazione log) | Usato occasionalmente |
| IF-35 | Operatore | Template Report | PC (offline) | Workbook Excel | Post-test | Aggregazione manuale |                

### 3.4 Interfaccia Dati Real-Time del DUT (Presente ma NON utilizzata)

| ID Interfaccia | Da | A | Protocollo | Capacità | Stato in AS-IS | Rischio/Nota |
|----------------|----|----|------------|----------|----------------|---------------|
| IF-40 | DUT | Client esterno | REST/HTTP o TCP | Lettura misure live, stato, stream eventi | Non usata | Richiede software client + integrazione rete |
| IF-41 | Client esterno | DUT | REST/HTTP o TCP | Avvio/arresto logging, recupero log parziali | Non usata | Deve essere vincolato per evitare controllo non intenzionale |

## 4. Mappa dei Flussi di Dati (End-to-End)

### 4.1 Flussi di Dati Durante il Test

**DF-01 Controllo di processo (pressione)**

- L'operatore inserisce i parametri su HMI → il PLC esegue la sequenza base
- Il PLC comanda pompa/valvole
- Il feedback di pressione è letto dal PLC per la regolazione del processo e gli allarmi

**DF-02 Evoluzione temperatura**

- Il controllore di temperatura esegue il profilo configurato localmente
- Il PLC può ricevere stati grossolani READY/FAULT (se cablato)
- I dati di temperatura non sono nativamente centralizzati

**DF-03 Trending e registrazione**

- Il datalogger registra i canali di pressione e temperatura
- Il DUT registra i propri sensori interni in modo indipendente
- Non esiste un identificatore di test condiviso tra le sorgenti

### 4.2 Flussi di Dati a Fine Test

**DF-10 Esportazione logger**

- L'operatore estrae il CSV dal logger via SD/USB
- I file sono denominati manualmente o inseriti in cartelle (denominazione non standard)

**DF-11 Esportazione DUT**

- L'operatore finalizza il log sul DUT
- Dati estratti via rimozione SD o download file Ethernet
- Tipicamente eseguito solo dopo il completamento completo del test

**DF-12 Esportazione controllore temperatura (opzionale)**

- L'operatore esporta un file di profilo o trend, a volte in formato vendor

**DF-13 Assemblaggio report**

- L'operatore correla manualmente:
  - Seriale/batch DUT
  - Parametri di test (note HMI/ricetta)
  - CSV logger (pressione/temp)
  - File log DUT
  - Esportazione controllore (opzionale)
- Il report è costruito in Excel (copia/incolla, calcoli, grafici)

## 5. Punti di Correlazione e Gap

### 5.1 Punti di Correlazione

- Tempo di inizio test (definito dall'operatore)
- Durata test / tempo di mantenimento
- Forma della rampa di pressione
- Milestone del profilo di temperatura
- Timestamp interni del DUT (se presenti)

### 5.2 Gap Attuali

- Nessun **ID Test** automatico propagato tra i sottosistemi
- Nessuna sincronizzazione temporale garantita tra:
  - Orologio del datalogger
  - Orologio interno del DUT
  - Timestamp PLC/HMI (se presenti)
- La denominazione manuale dei file è un singolo punto di fallimento per la tracciabilità
- I dati sono multi-sorgente e post-correlati manualmente
- La capacità API del DUT è inutilizzata, impedendo l'integrazione near-real-time

## 6. Punti di Contatto dell'Operatore

- Sequenziamento avvio/arresto su più dispositivi
- Conferma manuale degli stati di prontezza
- Esportazione manuale da logger/controllore/DUT
- Associazione manuale dei file a un test
- Calcoli manuali e compilazione report

Questi punti di contatto sono le principali fonti di variabilità operativa e errori nel modello AS-IS.

## 7. Diagramma Riassuntivo (Testuale)

- **Percorso di Controllo**

  - HMI → PLC → (Pompa / Valvole)
  - Catena Relè Sicurezza → (Rimozione potenza a Pompa/Riscaldatore) [override   indipendente]
  - Controllore Temp → (Camera/Riscaldatore) [indipendente]

- **Percorso di Misurazione**

  - Trasduttore Pressione → PLC (feedback processo)
  - Segnali Pressione/Temp → Datalogger (registrazione)
  - Sensori interni DUT → Log interno DUT (registrazione)

- **Percorso di Esportazione**

  - Datalogger → SD/USB → Operatore
  - Controllore Temp → USB/export → Operatore (opzionale)
  - DUT → Download SD/Ethernet → Operatore
  - Operatore → Excel → Report

- **Capacità Non Utilizzata**

  - API DUT (dati live) esiste ma non fa parte del flusso operativo

## 8. Driver di Baseline per TO-BE

- Introdurre un **ID Test** univoco e propagarlo tra le sorgenti dati
- Ridurre i passaggi di esportazione manuale attraverso percorsi di ingestione strutturati
- Migliorare correlazione e tracciabilità (timestamp, metadati, azioni operatore)
- Decidere se e come utilizzare le API real-time del DUT preservando l'indipendenza di sicurezza
- Preservare l'indipendenza della sicurezza dai livelli supervisivi/dati
