## Descrizione del Test Bench TO-BE

### 1. Panoramica

Il sistema target evolve da un ambiente di test coordinato manualmente
a una piattaforma di test industriale integrata, automatizzata e parzialmente supervisionata da remoto.

L'obiettivo è aumentare la ripetibilità, ridurre l'intervento manuale,
centralizzare la gestione dei dati e introdurre una supervisione remota controllata
mantenendo o migliorando la sicurezza funzionale.

### 2. Architettura di Controllo Target

#### 2.1 Orchestrazione Centralizzata del Processo

- Una logica di controllo centrale coordina tutti i sottosistemi (pressione,
    temperatura, acquisizione).
- Il sequenziamento automatizzato gestisce:

  - Profili di rampa
  - Sincronizzazione tra sottosistemi
  - Fasi di mantenimento
  - Procedure di spegnimento controllato
- La validazione pre-test dei parametri e dello stato del sistema viene eseguita
    automaticamente.

#### 2.2 Infrastruttura di Dati Integrata

- Tutti i sottosistemi trasmettono i dati a un repository centralizzato.
- Ogni test è identificato univocamente e associato a:
  - ID Componente
  - Ricetta di test
  - Timestamp
  - ID Operatore
- La correlazione dei dati è automatica e strutturata.

#### 2.3 Capacità di Supervisione Remota

- HMI basato su PC per il controllo supervisivo.
- Monitoraggio basato su tablet (funzionalità ristretta).
- Accesso remoto controllato per la manutenzione (tramite gateway sicuro).

I privilegi di controllo remoto sono limitati e basati sui ruoli.

### 3. Flusso Operativo

#### 3.1 Preparazione del Test

Responsabilità dell'operatore:

- Selezionare la ricetta di test.
- Confermare la corretta configurazione del componente.
- Autorizzare l'avvio del test.

Responsabilità del sistema:

- Validare la configurazione.
- Verificare interlock e condizioni di sicurezza.
- Verificare disponibilità e plausibilità dei sensori.

L'avvio del test è condizionato al successo della validazione.

#### 3.2 Esecuzione Automatizzata del Test

Responsabilità del sistema:

- Coordinare tutti i sottosistemi.
- Garantire temporizzazione e sincronizzazione.
- Monitorare le variabili di processo.
- Registrare tutti i dati rilevanti in tempo reale.
- Attivare allarmi o sequenze di arresto quando necessario.

Responsabilità dell'operatore:

- Supervisionare l'evoluzione del processo.
- Rispondere agli allarmi.
- Intervenire se necessario.

L'operatore passa da esecutore a supervisore.

#### 3.3 Fine Test e Reportistica

Responsabilità del sistema:

- Finalizzare automaticamente la sequenza di test.
- Memorizzare tutti i dati correlati.
- Generare report di test standardizzato.
- Registrare interventi dell'operatore e anomalie.

Responsabilità dell'operatore:

- Rivedere il report generato.
- Validare o rifiutare l'esito del test.
- Fornire l'approvazione finale.

### 4. Architettura di Sicurezza (Stato Target)

- Funzioni di sicurezza implementate in logica di sicurezza dedicata.
- Le funzioni critiche includono:
  - Protezione da sovrappressione
  - Trip da sovratemperatura
  - Depressurizzazione sicura
  - Gestione interlock protezioni
- Il reset di sicurezza richiede conferma fisica locale.
- I sistemi remoti non possono sovrascrivere gli interlock di sicurezza.

La sicurezza funzionale rimane indipendente dai sistemi supervisivi.

### 5. Fondamenti di Sicurezza Informatica

L'introduzione della connettività crea una nuova superficie di esposizione.

I principi di sicurezza includono:

- Segmentazione di rete tra domini OT e IT.
- Controllo accessi basato sui ruoli.
- Autenticazione per azioni critiche.
- Logging e tracciabilità delle modifiche di configurazione.
- Manutenzione remota sicura tramite gateway controllato.

I controlli cyber proteggono l'integrità del processo ma non sostituiscono le funzioni
di sicurezza.

### 6. Modello di Responsabilità (TO-BE)

#### Responsabilità dell'Operatore

- Autorizzare l'esecuzione del test.
- Supervisionare il processo automatizzato.
- Gestire eventi anomali.
- Validare i risultati finali.
- Mantenere la responsabilità per l'accettazione del test.

#### Responsabilità del Sistema

- Coordinare l'intero ciclo di vita del test.
- Validare le precondizioni.
- Eseguire sequenze deterministiche.
- Aggregare e memorizzare i dati.
- Generare report formali.
- Mantenere la tracciabilità degli eventi.

#### Responsabilità della Logica di Sicurezza

- Far rispettare i limiti operativi sicuri.
- Sovrascrivere comandi non sicuri.
- Forzare lo stato sicuro in condizioni pericolose.
- Richiedere reset locale dopo trip di sicurezza.

### 7. Caratteristiche Chiave dello Stato Target

- Ridotta sincronizzazione manuale.
- Maggiore ripetibilità.
- Ciclo di vita dei dati strutturato.
- Supervisione remota controllata.
- Chiara separazione tra controllo di processo e logica di sicurezza.
- Emergenza della sicurezza informatica come requisito a livello di sistema.
