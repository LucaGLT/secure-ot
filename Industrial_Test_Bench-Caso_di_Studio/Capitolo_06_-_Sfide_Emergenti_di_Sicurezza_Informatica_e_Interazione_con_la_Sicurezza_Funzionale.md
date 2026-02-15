## Sfide Emergenti di Sicurezza Informatica e Interazione con la Sicurezza Funzionale

### Interpretazione in Relazione alla Sicurezza Funzionale

### 1. Introduzione

La transizione da un sistema isolato e coordinato manualmente a una piattaforma automatizzata e parzialmente connessa introduce un cambiamento fondamentale nell'esposizione al rischio.

Mentre l'automazione aumenta la ripetibilità e riduce la variabilità operativa umana, la connettività introduce rischi cyber sistemici che possono influenzare direttamente o indirettamente la sicurezza funzionale.

Questo documento analizza le problematiche emergenti di sicurezza informatica e la loro interazione con i requisiti di sicurezza.

### 2. Cambio nella Natura del Rischio

#### Modello di Rischio AS-IS

- Rischio dominato dall'errore umano
- Esposizione cyber minima dovuta all'isolamento
- Sicurezza principalmente procedurale e applicata localmente

#### Modello di Rischio TO-BE

- Variabilità manuale ridotta
- Maggiore dipendenza dall'integrità della logica di controllo
- Introduzione di connettività di rete e accesso remoto
- Emergere di minacce digitali malevole o accidentali

Il rischio si sposta dall'errore umano individuale alla vulnerabilità sistemica.

## 3. Nuove Superfici di Esposizione Cyber

L'introduzione di supervisione e capacità remote crea nuovi vettori di attacco:

### 3.1 Sistemi Supervisori (HMI / SCADA)

Rischi potenziali:

- Modifica non autorizzata delle ricette di test
- Manipolazione dei parametri di processo
- Soppressione o alterazione degli allarmi
- Visualizzazione falsa delle variabili di processo

Rilevanza per la sicurezza: Informazioni supervisorie errate possono ritardare l'intervento umano o portare a decisioni inappropriate.

#### 3.2 Canali di Accesso Remoto

Rischi potenziali:

- Accesso non autorizzato ai sistemi di controllo
- Movimento laterale dalla rete IT alla rete OT
- Modifiche di configurazione non controllate

Rilevanza per la sicurezza: L'accesso remoto potrebbe abilitare comandi non sicuri se non tecnicamente vincolato.

#### 3.3 Infrastruttura di Dati Centralizzata

Rischi potenziali:

- Compromissione dell'integrità dei dati
- Perdita di tracciabilità
- Manomissione dei record di test

Rilevanza per la sicurezza: Risultati di test corrotti possono validare componenti non sicuri o invalidare componenti conformi.

### 4. Modello di Interazione tra Sicurezza Funzionale e Sicurezza Informatica

La Sicurezza Funzionale garantisce:

- Applicazione dello stato sicuro
- Comportamento di trip deterministico
- Protezione contro guasti prevedibili

La Sicurezza Informatica garantisce:

- Integrità dei comandi
- Autenticità degli utenti
- Riservatezza dei dati sensibili
- Disponibilità dei sistemi

L'intersezione si verifica dove una compromissione digitale potrebbe influenzare comportamenti rilevanti per la sicurezza.

### 5. Principio Critico di Progettazione

La sicurezza non deve dipendere dall'integrità cyber.

Questo significa:

- La logica di sicurezza deve essere indipendente dai livelli supervisivi
- I sistemi remoti non possono sovrascrivere gli interlock di sicurezza
- Il reset di sicurezza richiede interazione fisica locale
- Le soglie critiche sono applicate nella logica di sicurezza dedicata

I controlli cyber proteggono il processo, ma la logica di sicurezza protegge le persone e le attrezzature.

### 6. Scenari di Rischio Combinato Emergenti

#### Scenario A: Manipolazione della Ricetta

Se un attaccante modifica un profilo di rampa di pressione, il processo può superare i limiti meccanici sicuri.

Mitigazione:

- Validazione dei parametri all'interno della logica di controllo
- Soglie di sicurezza rigide indipendenti dalla ricetta

#### Scenario B: Soppressione degli Allarmi

Se gli allarmi sono nascosti o disabilitati nell'HMI, la reazione dell'operatore può essere ritardata.

Mitigazione:

- Trip di sicurezza indipendente dalla visibilità HMI
- Ridondanza degli allarmi o segnalazione hardware

#### Scenario C: Controllo Remoto Non Autorizzato

Se l'accesso remoto viene sfruttato, potrebbero essere emessi comandi non sicuri.

Mitigazione:

- Controllo degli accessi basato sui ruoli
- Autenticazione multi-fattore
- Logging dei comandi e tracciabilità delle sessioni
- Segmentazione della rete

### 7. Implicazioni di Governance

Il sistema TO-BE richiede:

- Chiara separazione tra domini IT e OT
- Proprietà definita delle responsabilità di sicurezza informatica
- Gestione della configurazione documentata
- Procedure di controllo delle modifiche
- Validazione degli aggiornamenti software
- Valutazioni di sicurezza periodiche

La validazione della sicurezza funzionale deve considerare i pericoli indotti dal cyber come parte dell'analisi dei rischi a livello di sistema.

### 8. Considerazioni di Validazione e Test

I test di Sicurezza Informatica dovrebbero includere:

- Test di robustezza dell'autenticazione
- Verifica della segmentazione di rete
- Validazione del controllo accessi basato sui ruoli
- Controlli di logging e tracciabilità

I test di Sicurezza Funzionale dovrebbero confermare:

- Indipendenza del trip di sicurezza dal livello supervisivo
- Applicazione dello stato sicuro in caso di comportamento digitale anomalo
- Risposta appropriata in caso di tentativi di comandi corrotti

Gli scenari di test combinati devono verificare che una compromissione cyber non possa disabilitare le funzioni di sicurezza.

### 9. Conclusione Strategica

L'evoluzione verso l'automazione e la connettività trasforma il sistema da: Controllo di sicurezza centrato sull'umano a Controllo deterministico centrato sul sistema.

Questa transizione richiede:

- Separazione architettonica esplicita
- Strategia cyber defense-in-depth
- Indipendenza di sicurezza verificata
- Valutazione del rischio integrata che copra entrambi i domini

La Sicurezza Informatica protegge l'integrità del sistema. La Sicurezza Funzionale protegge la vita umana e le risorse fisiche.

Entrambe devono coesistere senza compromettere l'una l'altra.
