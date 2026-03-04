## Addendum Tecnico AS-IS

### Descrizione Dettagliata dell'Architettura Tecnica

### 1. Scopo di questo Addendum

Questo documento fornisce una descrizione tecnica più approfondita dell'architettura attuale (AS-IS) del test bench.

Completa la descrizione principale del sistema AS-IS fornendo dettagli su:

- Componenti hardware
- Interfacce di controllo
- Flussi di dati
- Capacità del Device Under Test (DUT)
- Limitazioni di integrazione attuali

### 2. Inventario degli Asset

#### 2.1 Strato di Controllo

##### PLC

- Modello: Siemens S7-1200 (es. CPU 1214C)
- I/O:
  - Ingressi Digitali (DI)
  - Uscite Digitali (DO)
  - Ingressi Analogici (AI 4-20 mA)
  - Uscite Analogiche (AO 4-20 mA)
- Ruolo:
  - Controllo sequenze di base (avvio, mantenimento, arresto, depressurizzazione)
  - Comando attuatori
  - Gestione allarmi di base

##### HMI

- Modello: Siemens KTP700 Basic
- Connesso localmente al PLC
- Funzionalità:
  - Inserimento manuale setpoint
  - Parametri ricetta di base
  - Visualizzazione stato
  - Nessuna memorizzazione dati centralizzata

#### 2.2 Sottosistema Pressione

- Pompa alta pressione (azionamento elettrico)
- Valvola di scarico a solenoide (controllo DO)
- Valvola proporzionale opzionale (AO 4-20 mA)
- Trasduttore di pressione:
  - Range: 0-400 bar
  - Uscita: 4-20 mA
  - Lettura tramite canale AI del PLC
- Pressostato meccanico:
  - Cablaggio diretto alla catena di sicurezza

#### 2.3 Sottosistema Temperatura

- Camera climatica o sistema di riscaldamento
- Controllore di temperatura stand-alone (es. Eurotherm / Omron)
- Sensori di temperatura (PT100 / termocoppie)
- Controllore opera in modo indipendente
- Interazione con PLC limitata a:
  - Segnali digitali RUN / READY / FAULT
  - Nessuna gestione coordinata dei profili

#### 2.4 Apparecchiature di Acquisizione Dati

- Datalogger industriale stand-alone
- Registra segnali di pressione e temperatura
- Supporto di memorizzazione:
  - Scheda SD
  - Memoria USB
- Formato dati:
  - Esportazione CSV
- Nessuna integrazione real-time con PLC o HMI

### 3. Architettura di Sicurezza (Implementazione Attuale)

- Catena di relè di sicurezza (logica cablata)
  - Ingressi includono:
    - Arresto di emergenza
    - Interlock porta
    - Pressostato meccanico
  - Uscite:
    - Rimozione potenza dalla pompa
    - Rimozione potenza dal sistema di riscaldamento
- Nessun PLC di sicurezza
- Nessuna logica di sicurezza software-based
- Il reset di sicurezza richiede interazione manuale locale

La sicurezza opera indipendentemente dalla logica PLC.

### 4. Caratteristiche del Device Under Test (DUT)

Il DUT frequentemente include elettronica embedded con intelligenza interna.

#### 4.1 Capacità Funzionali del DUT

- Misurazioni da sensori interni (es. pressione, temperatura, posizione, corrente)
- Capacità di logging onboard
- Registrazione eventi
- Memoria interna di archiviazione

#### 4.2 Metodi di Esportazione Dati del DUT

Al termine del ciclo di test:

- Rimozione scheda SD ed estrazione file
- Download file via Ethernet (procedura manuale)
- Dati forniti come log strutturati (es. CSV, formato proprietario)

#### 4.3 API del DUT (Non Utilizzata Attualmente)

Il DUT fornisce un'interfaccia programmabile (non integrata nel flusso di lavoro attuale):

- API REST o protocollo TCP-based
- Accesso alle misure in tempo reale o near real-time
- Endpoint per interrogazioni di stato
- Capacità di streaming dei log durante l'esecuzione del test

Stato attuale:

- L'API esiste ma non è integrata nel processo del test bench
- Nessun software sviluppato per consumare dati live dal DUT
- Il DUT è trattato operativamente come una black box fino all'estrazione dei log

### 5. Flussi di Dati Attuali

#### 5.1 Durante il Test

- Il PLC controlla il sottosistema pressione
- Il controllore di temperatura esegue il proprio profilo
- Il datalogger registra i segnali
- Il DUT registra dati interni in modo indipendente

Non esiste un identificatore di test condiviso propagato automaticamente tra i sistemi.

La sincronizzazione dipende dalle azioni dell'operatore.

#### 5.2 Fine del Test

L'operatore esegue:

- Estrazione dati dal datalogger (USB / SD)
- Estrazione log dal DUT (SD o download Ethernet)
- Associazione manuale di:
  - Numero seriale DUT
  - Parametri di test
  - File del datalogger
  - Dati profilo temperatura

L'aggregazione dei dati è manuale e tipicamente eseguita utilizzando fogli di calcolo.

### 6. Gap di Integrazione Identificati

- Nessuna logica di orchestrazione centralizzata
- Nessun ID test unificato tra i sottosistemi
- Nessuna correlazione automatica di dati multi-sorgente
- Capacità API del DUT non utilizzata
- Nessun repository dati strutturato
- Nessuna architettura di rete tra gli asset

### 7. Caratteristiche della Linea di Base Architettonica

- Forte isolamento fisico di sicurezza
- Connettività digitale minima
- Alta dipendenza dall'operatore
- Molteplici sorgenti dati indipendenti
- Nessuna segmentazione di rete OT richiesta (rete assente)

Questa configurazione AS-IS fornisce bassa esposizione cyber ma alto carico manuale operativo e ripetibilità limitata.
