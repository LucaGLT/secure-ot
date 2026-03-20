---
title: "Principi della Norma IEC 62443"
author: "Gianluca TATA"
last_updated: "2026-03-10"
---

## Struttura della Norma (Serie IEC 62443-1, 2, 3, 4)

### Introduzione

Questo capitolo analizza la struttura modulare della norma IEC 62443, descrivendo le quattro serie principali e come si relazionano tra loro.

### Contenuti Principali

- Come si divide la norma e perché [→](#come-si-divide-la-norma-e-perché)
- IEC 62443-1: General / Concetti generali [→](#iec-62443-1-general--concetti-generali)
- IEC 62443-2: Policies and Procedures / Sistemi di gestione [→](#iec-62443-2-policies-and-procedures--sistemi-di-gestione)
- IEC 62443-3: System Requirements / Requisiti di sistema [→](#iec-62443-3-system-requirements--requisiti-di-sistema)
- IEC 62443-4: Component Requirements / Requisiti dei componenti [→](#iec-62443-4-component-requirements--requisiti-dei-componenti)

### Come si divide la norma e perché

La IEC 62443 e realmente suddivisa in una famiglia di documenti organizzati in piu parti, raccolte nelle serie 1, 2, 3 e 4.

1. **IEC 62443-1 - General / Concetti generali**: Questa parte raccoglie i principi di base, le definizioni e i modelli concettuali usati in tutta la serie. Comprende temi come: terminologia, modelli di sicurezza, metriche, concetti fondamentali per IACS.

2. **IEC 62443-2 - Policies and Procedures / Sistemi di gestione**: Questa sezione riguarda gli aspetti gestionali, organizzativi e procedurali della sicurezza informatica OT. Tratta i requisiti dei programmi di sicurezza, CSMS, patch management, requisiti per fornitori e integratori.

3. **IEC 62443-3 - System Requirements / Requisiti di sistema**: Include gli aspetti tecnici a livello di sistema, come architetture, valutazione del rischio, zone e conduits, requisiti di sicurezza di sistema e livelli di sicurezza (SL).

4. **IEC 62443-4 - Component Requirements / Requisiti dei componenti**: Riguarda i requisiti di sicurezza per i singoli componenti e il secure development lifecycle (SDLC). Definisce i requisiti tecnici che i prodotti devono soddisfare.

Questa articolazione consente di assegnare a ciascun attore indicazioni più mirate e applicabili al proprio ruolo, evitando approcci generici o eccessivamente astratti.

La suddivisione riflette anche una logica di ciclo di vita, perché accompagna le organizzazioni dalla definizione dei concetti e delle responsabilita fino alla progettazione, integrazione, esercizio, manutenzione e sviluppo dei prodotti.

In questo modo, la serie IEC 62443 risulta piu flessibile, scalabile e adatta a essere applicata in contesti industriali differenti, mantenendo al tempo stesso coerenza metodologica e visione d'insieme.

### IEC 62443-1: General / Concetti generali

La serie IEC 62443-1 definisce le basi concettuali comuni su cui si appoggiano tutte le altre serie. Il suo valore principale e creare un linguaggio condiviso tra stakeholder diversi (asset owner, fornitori, integratori, auditor), evitando interpretazioni ambigue quando si passa ai requisiti tecnici e gestionali.

In particolare, i contenuti si articolano attorno a due riferimenti chiave:

1. **IEC 62443-1-1 - Terminology, concepts and models**: stabilisce la terminologia ufficiale e i modelli concettuali di riferimento. Qui vengono chiariti termini come zona, conduit, livello di sicurezza, requisito di sicurezza e ruolo organizzativo, fornendo la cornice teorica necessaria per applicare correttamente le parti 2, 3 e 4.

2. **IEC 62443-1-5 - Scheme for IEC 62443 security profiles**: introduce lo schema dei security profile, cioe un approccio strutturato per mappare esigenze operative, rischio e requisiti applicabili. Questo consente di costruire profili coerenti con il contesto impiantistico, riducendo il rischio di applicazioni parziali o non omogenee della norma.

Dal punto di vista pratico, la serie 1 non impone direttamente contromisure puntuali, ma definisce il quadro metodologico che permette di selezionarle e giustificarle in modo tracciabile.

Per questo motivo è spesso il punto di partenza in un percorso di adozione IEC 62443: prima si allineano lessico e modelli, poi si implementano processi, requisiti di sistema e requisiti di prodotto nelle serie successive.

### IEC 62443-2: Policies and Procedures / Sistemi di gestione

La serie IEC 62443-2 traduce i principi generali in requisiti organizzativi e procedurali, definendo come una organizzazione deve governare nel tempo la sicurezza informatica dei sistemi IACS. La serie struttura il sistema di gestione, chiarendo responsabilità, processi operativi, controlli periodici e miglioramento continuo.

I riferimenti principali della serie sono:

1. **IEC 62443-2-1 - Security program requirements for IACS asset owners**: definisce i requisiti del programma di sicurezza per proprietari e gestori degli impianti. Include governance, politiche, gestione del rischio, gestione degli accessi, formazione, gestione delle modifiche, risposta agli incidenti e verifica dell'efficacia delle misure adottate.

2. **IEC 62443-2-2 - IACS security protection scheme**: descrive uno schema di protezione per impostare, valutare e mantenere i controlli di sicurezza nel contesto IACS, con attenzione alla coerenza tra misure tecniche e processi di gestione.

3. **IEC 62443-2-3 - Patch management in the IACS environment**: tratta il processo di gestione delle patch in ambiente industriale, dove la priorita non e solo aggiornare rapidamente, ma farlo in modo controllato per non compromettere disponibilita, stabilita e sicurezza del processo produttivo.

4. **IEC 62443-2-4 - Security program requirements for IACS service providers**: stabilisce i requisiti per i fornitori di servizi (inclusi integratori e manutentori), in modo che le attivita svolte su sistemi industriali siano coerenti con obiettivi, responsabilita e livelli di protezione richiesti dall'asset owner.

Dal punto di vista applicativo, la serie 2 è il ponte tra strategia e operativita: senza processi chiari, anche requisiti tecnici ben progettati rischiano di perdere efficacia nel tempo. Per questo motivo, in un percorso maturo IEC 62443, i controlli tecnici della serie 3 e i requisiti di prodotto della serie 4 vengono sostenuti da una solida disciplina di gestione definita dalla serie 2.

### IEC 62443-3: System Requirements / Requisiti di sistema

La serie IEC 62443-3 affronta la sicurezza informatica a livello di architettura di sistema IACS. Se la serie 2 definisce come governare il programma di sicurezza, la serie 3 definisce come progettare e verificare tecnicamente il sistema in funzione del rischio e del contesto operativo.

I riferimenti principali della serie sono:

1. **IEC 62443-3-1 - Security technologies for industrial automation and control systems**: fornisce una panoramica delle tecnologie di protezione applicabili ai sistemi industriali, utile per orientare le scelte architetturali e comprendere le opzioni tecniche disponibili.

2. **IEC 62443-3-2 - Security risk assessment and system design**: definisce il processo con cui l'analisi del rischio guida la progettazione del sistema. In questa parte si formalizza il legame tra minacce, impatto operativo e misure da implementare, con particolare attenzione a segmentazione, zone e conduits.

3. **IEC 62443-3-3 - System security requirements and security levels**: stabilisce i requisiti di sicurezza di sistema e li collega ai security level (SL), fornendo una base verificabile per specificare cosa il sistema deve garantire e con quale robustezza.

Dal punto di vista pratico, la serie 3 e il riferimento tecnico centrale per la progettazione di una architettura OT difendibile: traduce obiettivi di rischio in requisiti di sistema misurabili e consente di dimostrare in modo tracciabile che la soluzione adottata e coerente con il livello di protezione richiesto.

#### IEC 62443-3-1 - Security technologies for industrial automation and control systems

La IEC 62443-3-1 e un rapporto tecnico che **descrive le principali tecnologie di sicurezza informatica applicabili ai sistemi di automazione e controllo industriale**, con l'obiettivo di supportare progettisti e gestori nella scelta delle contromisure piu adatte al contesto operativo. Non e una parte prescrittiva in senso stretto: non impone requisiti obbligatori come la 3-3, ma fornisce una base tecnica per comprendere quali soluzioni siano disponibili, come funzionino e quali limiti possano avere in ambiente OT.

Le tecnologie trattate (a livello di famiglie funzionali) includono in particolare:

- segmentazione architetturale con zone e conduits, per ridurre la propagazione degli incidenti;
- controllo dei flussi e filtraggio del traffico tra domini di rete;
- gestione delle identità e controllo degli accessi (utenti, ruoli, privilegi);
- hardening di sistemi e dispositivi, con riduzione della superficie di esposizione;
- protezione delle comunicazioni e dell'integrità dei dati scambiati;
- registrazione, monitoraggio e correlazione degli eventi di sicurezza;
- rilevazione anomalie e meccanismi di allerta per identificare comportamenti non attesi;
- misure di continuità operativa e recupero, incluse strategie di backup e ripristino.

Il collegamento tra rischio reale e misura tecnica avviene attraverso un percorso logico: si parte da scenari di minaccia concreti (ad esempio accesso remoto improprio, propagazione laterale, modifica non autorizzata di logiche di controllo), si valuta l'impatto sul processo industriale e si selezionano poi le tecnologie che riducono quel rischio specifico. In questo modo la scelta non è guidata dalla sola disponibilita della tecnologia, ma dalla sua capacità di abbassare probabilità e conseguenze dell'evento indesiderato nel contesto impiantistico reale.

La 3-1 chiarisce anche quando una singola misura e insufficiente, promuovendo una logica di difesa in profondità. Una misura è efficace quando è coerente con lo scenario di rischio, applicabile al contesto operativo e verificabile nel tempo; diventa invece parziale quando lascia scoperti altri vettori di attacco o dipende da condizioni non garantite (ad esempio configurazioni manuali, assenza di monitoraggio, eccezioni operative). Per questo la norma orienta a combinare controlli preventivi, rilevativi e correttivi: ad esempio segmentazione di rete insieme a controllo accessi, monitoraggio eventi e procedure di risposta, cosi da aumentare robustezza e resilienza complessiva del sistema.

Dal punto di vista metodologico, questa parte è particolarmente utile nelle fasi iniziali di progettazione e nelle attivita di revisione architetturale, perché consente di costruire una mappa ragionata delle opzioni di protezione prima di formalizzare i requisiti finali in IEC 62443-3-2 e IEC 62443-3-3. In altre parole, la 3-1 fornisce il catalogo tecnico e il contesto di utilizzo delle tecnologie, mentre le altre parti della serie 3 definiscono come trasformare tali scelte in requisiti verificabili e livelli di sicurezza coerenti con il rischio.

#### IEC 62443-3-2 - Security risk assessment and system design

La IEC 62443-3-2 e la parte che trasforma la valutazione del rischio in scelte progettuali concrete a livello di sistema IACS. Il suo obiettivo non è solo identificare le minacce, ma guidare la definizione di una architettura sicura coerente con il contesto operativo, con la criticità del processo e con le conseguenze potenziali su produzione, persone e ambiente.

Il nucleo metodologico della 3-2 puo essere letto come una sequenza strutturata:

1. definizione del perimetro e del contesto: si individuano sistema, confini, asset critici, interfacce e dipendenze operative;
2. identificazione di minacce e scenari di incidente: si analizzano eventi plausibili (accessi non autorizzati, alterazioni logiche, indisponibilità di funzioni essenziali, propagazione laterale);
3. stima del rischio: si valuta la combinazione tra probabilità e impatto per stabilire le priorità;
4. definizione del target security level (SL-T): si determina il livello di protezione richiesto per zone e conduits in funzione del rischio accettabile;
5. traduzione in requisiti di progetto: i risultati dell'analisi vengono trasformati in vincoli architetturali e requisiti tecnici da implementare e verificare.

Un elemento centrale della 3-2 e il collegamento tra analisi del rischio e segmentazione del sistema. La norma spinge a strutturare l'architettura in *Zone* omogenee per requisiti di sicurezza e in *Conduits* controllati per le comunicazioni tra zone, cosi da ridurre la superficie di esposizione e limitare la propagazione degli incidenti. In questo modo, la progettazione non è generica ma guidata da priorità di rischio esplicite.

Dal punto di vista applicativo, la 3-2 fornisce anche la base di tracciabilita necessaria per giustificare le decisioni tecniche: ogni misura prevista dovrebbe poter essere ricondotta a uno scenario di rischio e a un obiettivo di protezione. Questo approccio rende il progetto più difendibile sia tecnicamente sia in ottica di audit, e prepara il passaggio naturale alla IEC 62443-3-3, dove i requisiti di sistema e i livelli di sicurezza vengono formalizzati in modo verificabile.

#### IEC 62443-3-3 - System security requirements and security levels

La IEC 62443-3-3 è la parte prescrittiva della serie 3: definisce in modo esplicito quali requisiti di sicurezza deve soddisfare un sistema IACS e con quale livello di robustezza. Se la 3-2 stabilisce come analizzare il rischio e progettare l'architettura, la 3-3 specifica cosa deve essere implementato e verificato per dimostrare che il sistema raggiunge il livello di protezione atteso.

Il cuore della norma e l'insieme dei **System Security Requirements (SR)**, organizzati in famiglie coerenti con le funzioni fondamentali di sicurezza del sistema (identificazione e autenticazione, controllo d'uso, integrità del sistema, riservatezza dei dati, flussi dati limitati, risposta tempestiva agli eventi, consapevolezza situazionale). Questa struttura consente di tradurre gli obiettivi di protezione in requisiti tecnici concreti e verificabili.

Un secondo elemento centrale è la gestione dei **Security Level (SL)**. La 3-3 non tratta il livello di sicurezza come un'etichetta generica del sistema, ma come un obiettivo da assegnare e verificare per specifici requisiti e specifiche zone/conduits, in coerenza con il risultato della valutazione del rischio. In pratica:

1. dalla 3-2 si ricava il target security level (SL-T) necessario;
2. nella 3-3 si selezionano i requisiti applicabili e il livello richiesto per ciascuno;
3. si verifica che la soluzione implementata raggiunga il livello effettivo previsto.

In sintesi, la IEC 62443-3-3 e il riferimento che rende il progetto realmente verificabile: trasforma obiettivi di rischio e scelte architetturali in un set di requisiti misurabili, permette di dimostrare conformita in modo tracciabile e costituisce la base tecnica per audit, validazione e miglioramento continuo della sicurezza del sistema.

### IEC 62443-4: Component Requirements / Requisiti dei componenti

La serie IEC 62443-4 definisce i requisiti di sicurezza a livello di prodotto e componente, con l'obiettivo di garantire che la sicurezza informatica sia incorporata fin dalla fase di sviluppo e non aggiunta solo in esercizio. In questa prospettiva, la serie 4 completa le serie 2 e 3: non si limita a chiedere come gestire o progettare un sistema, ma specifica cosa devono offrire concretamente i componenti che lo compongono.

I riferimenti principali sono:

1. **IEC 62443-4-1 - Secure product development lifecycle requirements**: stabilisce i requisiti di processo per lo sviluppo sicuro del prodotto. Copre governance dello sviluppo, definizione dei requisiti di sicurezza, progettazione sicura, pratiche di implementazione, verifica e validazione, gestione delle vulnerabilita, gestione degli aggiornamenti e documentazione tecnica verso il cliente.

2. **IEC 62443-4-2 - Technical security requirements for IACS components**: definisce i requisiti tecnici che i componenti devono soddisfare (ad esempio controlli di autenticazione, autorizzazione, integrita, logging, protezione delle comunicazioni, gestione delle sessioni e funzioni di hardening), consentendo di valutare in modo oggettivo le capacita di sicurezza del prodotto.

Dal punto di vista applicativo, la serie 4 è particolarmente rilevante per fornitori, produttori e integratori, perché introduce una responsabilità diretta sulla qualità di sicurezza del componente lungo tutto il suo ciclo di vita. Per gli asset owner, invece, rappresenta un riferimento fondamentale in fase di selezione e qualifica dei prodotti, permettendo di richiedere evidenze tecniche e di processo coerenti con i requisiti del sistema.

In sintesi, la IEC 62443-4 abilita un approccio "secure by design" e "secure by default": riduce il rischio di introdurre vulnerabilità a monte, migliora la manutenibilita nel tempo e rende piu robusta l'intera architettura OT, soprattutto quando i requisiti di prodotto sono allineati con i requisiti di sistema definiti nella IEC 62443-3-3.
