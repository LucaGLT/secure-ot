---
tags: []
created: '2026-03-01'
title: 'perché una norma in più'
---

# Perché avevamo bisogno della IEC 62443 in ambito Industrial Control Systems e Operational Technology?

Negli ultimi anni la **Cybersecurity** è diventata un tema centrale anche nei **sistemi embedded** e nei **contesti industriali**. Tuttavia, una domanda emerge spesso tra i professionisti tecnici:

> Se esiste già una vasta letteratura sulla cybersecurity in ambito IT, perché è stata necessaria una norma specifica come la IEC 62443 per l'Operational Technology (OT) e gli Industrial Automation and Control Systems (IACS)?

La **IEC 62443**, nata come standard ISA-99 nel 2002 e successivamente adottata come norma internazionale, rappresenta oggi il **riferimento principale per la sicurezza dei sistemi di controllo industriale**.

La risposta non è tecnica in senso stretto. È architetturale e sistemica.

## IT e OT condividono i principi, non il contesto

Nel mondo IT abbiamo maturato decenni di esperienza su:

* autenticazione
* crittografia
* PKI
* segmentazione di rete
* zero trust
* vulnerability management
* monitoring continuo

Questi principi sono validi anche in ambito OT. Ma il contesto operativo è radicalmente diverso.

È vero: anche in IT esistono sistemi critici (banche, e-commerce, infrastrutture cloud). Ma tali sistemi sono progettati nativamente con:

* ridondanza massiva
* segmentazione avanzata
* monitoraggio continuo con team dedicati (SOC)
* orchestrazione distribuita

Un sistema IT è generalmente:

* dinamico
* aggiornabile frequentemente
* replicabile
* virtualizzato
* monitorato 24/7

Molti sistemi industriali embedded non nascono con queste caratteristiche:

* non possono essere patchati frequentemente
* non sono cloud-native
* non sono replicabili né virtualizzbili
* hanno cicli di vita molto lunghi

Un sistema OT embedded è spesso:

* **real-time deterministico**: deve garantire tempi di risposta certi e predicibili, rendendo difficile introdurre controlli di sicurezza che aggiungano latenza (es. deep packet inspection, analisi comportamentale)
* **con ciclo di vita ultra-lungo (10–20 anni)**: deve essere progettato "secure by design" fin dall'inizio, perché le vulnerabilità scoperte dopo anni potrebbero non essere mai patchate
* **difficilmente aggiornabile**: un update richiede fermo impianto pianificato, test di regressione completi, validazione safety, e competenze specialistiche
* **fisicamente esposto**: accessibile da personale di campo, manutentori, fornitori terzi, spesso in ambienti non presidiati
* **privo di Security Operations Center (SOC) dedicato**: non dispone di monitoraggio continuo delle minacce 24/7 come nei datacenter enterprise

Applicare la cybersecurity IT "as is" significa ignorare queste differenze strutturali.

## In OT la sicurezza non protegge solo dati

Nel mondo IT la cybersecurity protegge principalmente:

* informazioni
* servizi digitali
* infrastrutture logiche

Nel mondo OT il software controlla direttamente **processi fisici critici**:

* **valvole di pressione** in pipeline di gas naturale
* **sistemi di distribuzione elettrica** in reti di trasmissione
* **motori e robot** su linee di produzione automotive
* **pompe dosometriche** in impianti chimici e farmaceutici
* **sistemi HVAC** in ospedali e data center
* **azionamenti di gru e macchinari pesanti** in stabilimenti industriali

In altre parole: il software non elabora solo informazioni, ma **comanda attuatori che muovono, riscaldano, pressurizzano, dosano sostanze, aprono circuiti elettrici**

Un attacco informatico può quindi trasformarsi in:

* danno fisico
* fermo impianto
* alterazione di misure
* rischio per operatori

Qui entra in gioco un elemento che in IT enterprise è marginale:
> l’interazione tra **Security** e **Safety**.

In OT, un attacco malevolo può generare lo stesso effetto di un guasto accidentale. Per questo **Security** e **Safety** devono essere progettate in modo coordinato.

## Esempio pratico IT vs OT

Per comprendere meglio questa distinzione, confrontiamo due scenari reali: 

* la compromissione di un server web in una banca
* e quella di un PLC in un impianto chimico.

Entrambi sono incidenti **gravi**, con impatti economici potenzialmente devastanti. Ma la natura del danno è radicalmente diversa.

Nel primo caso, l'attacco compromette la confidenzialità e l'integrità delle informazioni: credenziali rubate, dati finanziari esposti, violazioni GDPR con sanzioni milionarie, perdita di reputazione. L'organizzazione può rispondere con procedure consolidate di incident response, ripristinando da backup e implementando remediation. Il danno è principalmente **economico e reputazionale**.

Nel secondo caso, l'attacco può alterare il comportamento di un sistema che controlla processi fisici pericolosi: una valvola che non si chiude, una temperatura che supera soglie critiche, una reazione chimica fuori controllo. Il risultato può essere un'esplosione, una contaminazione ambientale, feriti o morti. Il danno è **fisico, immediato e irreversibile**.

La differenza non è sulla **gravità**, ma sulla **natura** dell'impatto:

| Scenario | Tipo di danno | Timeline recovery |
|----------|---------------|-------------------|
| **Server web bancario compromesso** | Furto dati finanziari, violazione GDPR, perdita reputazionale, sanzioni milionarie | Restore da backup, remediation: giorni/settimane; anni per la perdita di reputazione |
| **PLC in impianto chimico compromesso** | Rischio esplosione, contaminazione ambientale, feriti/morti, danno irreversibile | Fermo impianto obbligatorio, ispezione safety, sostituzione hardware: settimane/mesi; anni per impatti ambientali |

Entrambi sono incidenti **gravi**. Ma in OT:
* l'impatto può essere **fisico e irreversibile**
* le **vite umane** sono direttamente a rischio
* non esiste un "backup" della sicurezza delle persone
* la risposta richiede **coordinamento con autorità di safety** (non solo cyber)

La IEC 62443 deve quindi integrarsi con standard di safety come IEC 61508 (safety funzionale) e IEC 61511 (safety nei processi industriali), garantendo che le misure di security non compromettano le funzioni di safety e che la gestione degli incidenti consideri entrambi i domini.

## Il vero salto logico della IEC 62443

La IEC 62443 non reinventa la crittografia, non introduce nuovi algoritmi,  non sostituisce le best practice IT.

Introduce qualcosa di diverso:

> La IEC 62443 crea un modello architetturale per progettare la sicurezza in sistemi industriali.

## Struttura della norma

La IEC 62443 è organizzata in quattro gruppi principali, **ciascuno destinato a un Attore specifico**:

* **Parte 1 - Generale**: definisce linguaggio comune, modelli concettuali e principi trasversali (terminologia, metriche, asset, threat model), così che tutti gli attori valutino il rischio con gli stessi criteri.
* **Parte 2 - Politiche e procedure**: guida l'**Asset Owner** nella governance della sicurezza (ruoli, processi, gestione del ciclo di vita, gestione fornitori, gestione incidenti, miglioramento continuo).
* **Parte 3 - Sistema**: traduce il rischio in requisiti architetturali per il **System Integrator** (zone e conduits, assegnazione SL-T, requisiti di sistema, validazione tecnica e gap analysis).
* **Parte 4 - Componenti**: specifica i requisiti che il **Product Supplier** deve implementare nei prodotti (secure development lifecycle, hardening, autenticazione, logging, patchability, evidenze di conformità).

Questa distinzione di responsabilità è fondamentale: **ogni attore ha obblighi specifici e misurabili**.

## I concetti chiave

### Zone e Conduits

> Una **Zone** è un raggruppamento logico o fisico di asset con requisiti di sicurezza comuni.

In pratica, le **Zone** servono a separare domini con criticità diverse (ad esempio: rete IT aziendale, supervisione operativa, livello di controllo PLC), evitando che tutti i dispositivi stiano nello stesso “spazio di fiducia”.

> Un **Conduit** è il canale di comunicazione controllato tra due zone.

I **Conduits** definiscono invece *come* questi domini possono comunicare: quali protocolli sono ammessi, in che direzione, con quali controlli di autenticazione, filtraggio e monitoraggio.

Questo approccio limita la propagazione laterale: se un asset viene compromesso in una zona, l’attaccante non può muoversi liberamente verso tutte le altre.

### Security Level (SL)

La norma definisce **4 lSecurity Level** (da SL-1 a SL-4), basati sulla capacità dell'attaccante:

* **SL-1**: protezione contro violazioni casuali o accidentali
* **SL-2**: protezione contro attaccanti con risorse limitate e competenze generiche
* **SL-3**: protezione contro attaccanti con risorse moderate e competenze specifiche sul sistema
* **SL-4**: protezione contro attaccanti con risorse estese e competenze avanzate (nation-state)

Ogni zona ha:

* un **SL-T** (Security Level Target): livello richiesto
* un **SL-A** (Security Level Achieved): livello effettivamente implementato

### Foundational Requirements (FR)

I **7 Foundational Requirements** sono le aree di controllo con cui la IEC 62443 traduce la sicurezza in requisiti verificabili:

1. **FR1 - Identification and Authentication Control**: garantisce che utenti, dispositivi e applicazioni siano identificati e autenticati prima di accedere al sistema.
2. **FR2 - Use Control**: definisce quali azioni sono consentite a ciascun soggetto autenticato (principio del minimo privilegio).
3. **FR3 - System Integrity**: protegge logiche, software, configurazioni e firmware da modifiche non autorizzate o malevole.
4. **FR4 - Data Confidentiality**: tutela la riservatezza delle informazioni sensibili in transito, a riposo e durante l’accesso.
5. **FR5 - Restricted Data Flow**: limita e governa le comunicazioni tra zone e conduits, riducendo propagazione laterale e superfici di attacco.
6. **FR6 - Timely Response to Events**: abilita rilevamento, registrazione, allarme e risposta tempestiva agli eventi di sicurezza.
7. **FR7 - Resource Availability**: assicura continuità operativa e resilienza del sistema anche in presenza di guasti o attacchi.

Ogni FR si declina in **System Requirements (SR)** e **Component Requirements (CR)** specifici.

### Defense in Depth

La norma adotta il principio di **Defense in Depth**: la sicurezza non si basa su un singolo controllo, ma su strati multipli e indipendenti. Se un layer viene compromesso, altri layer continuano a proteggere il sistema.

La sicurezza non è più un insieme di meccanismi (password, TLS, firewall), ma una proprietà strutturale dell’architettura.

## Da protezione del componente a protezione del dominio

La Cybersecurity IT tradizionale tende a proteggere endpoint e servizi.

La IEC 62443 sposta l’attenzione su:

* domini di fiducia
* confini architetturali
* controllo dei flussi tra zone
* contenimento della propagazione laterale

Non si tratta di proteggere il singolo device "il PLC" o "l’HMI" né il singolo dato.
Si tratta di definire **quale livello di sicurezza deve avere una Zona** e **quali controlli devono governare ogni attraversamento di confine (Conduits)**.

Questo rende possibile:

* assegnare un Security Level Target (SL-T)
* misurare un Security Level Achieved (SL-A)
* effettuare gap analysis formali
* dimostrare coerenza tra rischio e architettura

A questo punto emerge un limite chiave: **Password** e **TLS** sono necessari, ma non sufficienti, coprono solo una parte del problema:

* autenticazione
* confidenzialità

La sicurezza OT, però, richiede risposte architetturali a domande come:

* Come limito la propagazione da un dispositivo compromesso?
* Come separo il dominio Informativo (IT) da quello Operativo (OT)?
* Come gestisco l’accesso manutentivo temporaneo?
* Come assegno formalmente un livello di protezione a una parte del sistema?

**Senza un modello architetturale, la sicurezza resta frammentata**.

## Conclusione

La IEC 62443 non sostituisce la Cybersecurity IT. La integra e la adatta a un contesto diverso.

Non è una norma “in più”. È un modello di progettazione necessario per sistemi IACS e industriali che governano processi fisici.

> La IEC 62443 offre un modello architetturale e aiuta a progettare sistemi OT che restino sicuri (Security e Safety) anche quando un attacco diventa evento fisico.

* La norma IEC 62443 copre l'intero **ciclo di vita**: progettazione, implementazione, manutenzione, dismissione
* Definisce ruoli e responsabilità per **Asset Owner**, **System Integrator** e **Product Supplier**
* È complementare agli standard di Safety Funzionale (IEC 61508, IEC 61511)

Ed è questo il salto logico e strategico che rende la norma necessaria in ambito **Industrial Control Systems** e **Operational Technology**.
