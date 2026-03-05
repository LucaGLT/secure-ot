---
title: "Industrial Test Bench - Caso di Studio"
author: "Gianluca TATA"
last_updated: "2026-03-05"
---

## Descrizione del Test Bench AS-IS

### 1. Panoramica

Il sistema attuale consiste in più test bench industriali utilizzati per la verifica di componenti meccanici in condizioni critiche di pressione e temperatura. L'architettura di controllo è principalmente basata su sistemi PLC locali senza connettività remota.

Le operazioni sono prevalentemente manuali e coordinate direttamente dagli operatori.

### 2. Architettura di Controllo

#### 2.1 Controllo Locale Basato su PLC

- Ogni sottosistema (pressione, temperatura, acquisizione dati) è controllato localmente.
- I PLC eseguono logica sequenziale di base.
- I controllori possono operare come unità autonome.
- Non esiste una logica di orchestrazione centralizzata.

#### 2.2 Mancanza di Accesso Remoto

- Nessuna supervisione remota via PC o tablet.
- Nessuna connettività esterna a reti aziendali o esterne.
  - Il sistema è effettivamente isolato dall'infrastruttura IT.

### 3. Flusso Operativo

#### 3.1 Esecuzione del Test

Gli operatori sono responsabili di:

- Avviare manualmente ogni sottosistema.
- Sincronizzare le fasi di pressione, temperatura e acquisizione.
- Monitorare l'evoluzione del test.
- Identificare condizioni anomale.
- Decidere quando interrompere il test.

Il coordinamento è guidato dall'operatore piuttosto che dal sistema.

#### 3.2 Attività Post-Test

Alla fine di ogni test:

- I dati vengono estratti manualmente dai singoli strumenti.
- I file vengono raccolti separatamente.
- I dati vengono aggregati manualmente.

Non esiste una correlazione automatica tra ID del test, ID del componente e dati di misurazione.

### 4. Gestione dei Dati e Reportistica

- I dati vengono elaborati manualmente.
- I report vengono creati utilizzando fogli di calcolo (ad es. Excel).
- La copia-incolla e i calcoli manuali sono comuni.
- La tracciabilità dipende dalla disciplina dell'operatore.
  - Non esiste un repository centralizzato o un database strutturato.

### 5. Caratteristiche di Sicurezza (Stato Attuale)

- La sicurezza si basa principalmente su:
  - Consapevolezza dell'operatore
  - Protezioni hardware di base
  - Blocchi locali (se presenti)
- Nessuna orchestrazione centralizzata della sicurezza.
- Nessuna validazione automatica globale degli stati del processo.

La sicurezza dipende fortemente dalla supervisione umana.

### 6. Esposizione alla Sicurezza Informatica (Stato Attuale)

- Superficie di attacco minima dovuta all'isolamento del sistema.
- Nessun accesso remoto.
- Nessuna connettività di rete esterna.
- Nessuna infrastruttura digitale centralizzata da compromettere.

Il rischio informatico è attualmente basso perché la connettività è assente.

### 7. Modello di Responsabilità (AS-IS)

#### Responsabilità dell'Operatore

- Coordinamento del sistema
- Verifica dei parametri
- Sincronizzazione manuale
- Rilevamento di anomalie
- Estrazione dei dati
- Creazione di report
- Convalida finale

L'operatore agisce come orchestratore primario del processo.

#### Responsabilità del Sistema

- Eseguire la logica di controllo locale
- Applicare i setpoint configurati manualmente
- Generare dati di misurazione grezzi
- Attivare protezioni locali di base

Il sistema esegue ma non governa il processo complessivo.

### 8. Osservazioni Chiave

- Elevata dipendenza dall'esperienza umana.
- Riprenibilità limitata.
- Gestione manuale dei dati.
- Bassa esposizione informatica.
- Sicurezza principalmente procedurale piuttosto che sistemica.
