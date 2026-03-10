---
title: "Principi della Norma IEC 62443"
author: "Gianluca TATA"
last_updated: "2026-03-05"
---

## Panoramica della Norma IEC 62443

### Introduzione

Questo capitolo fornisce un'introduzione generale alla norma IEC 62443, lo standard internazionale per la sicurezza informatica nei sistemi di automazione e controllo industriale (OT - Operational Technology).

### Contenuti Principali

- Origine ed evoluzione dello standard IEC 62443 [→](#origine-ed-evoluzione-dello-standard-iec-62443)
- Importanza della sicurezza informatica in ambienti industriali [→](#importanza-della-sicurezza-informatica-in-ambienti-industriali)
- Relazione con altri standard (IEC 61508, ISO 13849) [→](#relazione-con-altri-standard-iec-61508-iso-13849)
- Obiettivi e ambito di applicazione [→](#obiettivi-e-ambito-di-applicazione)
- Stakeholder e ruoli principali [→](#stakeholder-e-ruoli-principali)

### Origine ed evoluzione dello standard IEC 62443

La IEC 62443 nasce dall'esigenza di affrontare in modo strutturato i rischi di cybersecurity nei sistemi industriali, in un contesto in cui l'integrazione tra reti OT e IT ha progressivamente ampliato la superficie di attacco.

Le sue radici risalgono ai lavori iniziali della serie ISA-99, sviluppata per fornire linee guida pratiche agli operatori del settore dell'automazione; successivamente, attraverso la collaborazione internazionale con IEC, questo patrimonio tecnico si e evoluto in una famiglia di standard riconosciuta a livello globale.

Nel tempo, la norma e passata da un approccio prevalentemente prescrittivo a un'impostazione piu completa e modulare, capace di coprire governance, processi organizzativi, requisiti di sistema e requisiti per i componenti. Questa evoluzione riflette la maturazione del panorama delle minacce e la necessita, sempre piu sentita dalle organizzazioni industriali, di adottare un percorso continuo di gestione del rischio, miglioramento della resilienza operativa e responsabilita condivisa tra proprietari degli impianti, integratori e fornitori.

### Importanza della sicurezza informatica in ambienti industriali

Negli ambienti industriali, la sicurezza informatica non e un tema esclusivamente tecnologico, ma un fattore che incide direttamente su continuita operativa, qualita della produzione, tutela delle persone e affidabilita dei processi.

A differenza dei contesti IT tradizionali, un incidente di sicurezza informatica in OT puo tradursi in:

- fermo impianto,
- danni fisici agli asset,
- degrado delle prestazioni
- impatti sulla sicurezza funzionale.
- danni alle persone (safety)
- danni all'ambiente

La crescente digitalizzazione delle fabbriche, l'adozione di sistemi connessi e la convergenza IT/OT hanno portato benefici significativi in termini di efficienza e monitoraggio, ma hanno anche introdotto nuove vulnerabilita che richiedono misure di protezione specifiche. Per questo motivo, la security industriale deve essere affrontata con un approccio sistemico, basato su:

- valutazione del rischio,
- segmentazione delle reti,
- controllo degli accessi,
- gestione delle patch e
- monitoraggio continuo,

in modo da garantire resilienza e capacita di risposta lungo tutto il ciclo di vita dell'impianto.

### Relazione con altri standard (IEC 61508, ISO 13849)

La IEC 62443 non sostituisce gli standard di sicurezza funzionale (Functional Safety), ma li integra in una prospettiva complementare.

In particolare, la **IEC 61508** definisce i **principi generali per la safety dei sistemi elettrici, elettronici e programmabili**, mentre la **ISO 13849** è focalizzata sulla **sicurezza delle parti dei sistemi di comando legate alle macchine**.

La **IEC 62443**, invece, affronta in modo specifico la sicurezza informatica dei sistemi industriali, con l'obiettivo di ridurre il rischio di accessi non autorizzati, alterazioni dei dati e compromissione delle funzioni operative.

Nella pratica industriale, queste norme devono essere applicate in modo coordinato: le misure di sicurezza informatica contribuiscono a proteggere le funzioni safety da eventi malevoli o accidentali, mentre i requisiti di sicurezza funzionale garantiscono che il sistema rimanga in uno stato sicuro anche in condizioni di guasto. Un approccio integrato tra questi riferimenti normativi consente quindi di migliorare la robustezza complessiva dell'impianto, riducendo i rischi sia operativi sia per persone e ambiente.

### Obiettivi e ambito di applicazione

L'obiettivo principale della IEC 62443 è fornire un quadro organico per proteggere i sistemi di automazione e controllo industriale lungo tutto il loro ciclo di vita, dalla progettazione all'esercizio e alla manutenzione.

La norma promuove una gestione del rischio strutturata, orientata a prevenire accessi non autorizzati, limitare la propagazione degli incidenti, preservare l'integrita dei processi e garantire la disponibilita delle funzioni critiche per la produzione.

Il suo ambito di applicazione è ampio e coinvolge sia gli aspetti tecnici sia quelli organizzativi per:

- proprietari e gestori degli impianti,
- integratori di sistema,
- produttori di componenti e
- fornitori di servizi.

In questo senso, la IEC 62443 non si limita a definire misure tecnologiche puntuali, ma stabilisce anche requisiti di governance, ruoli e responsabilità, consentendo alle organizzazioni di costruire un percorso progressivo di miglioramento della sicurezza informatica industriale, coerente con la complessita e la criticita del contesto operativo.

### Stakeholder e ruoli principali

La IEC 62443 attribuisce un ruolo centrale alla collaborazione tra tutti gli attori della filiera industriale, riconoscendo che la sicurezza informatica non puo essere garantita da un solo soggetto. Nelle varie parti della serie, i ruoli sono indicati con termini in inglese che identificano responsabilita precise lungo il ciclo di vita del sistema.

- **Asset Owner (AO)**: soggetto responsabile dell'impianto o del processo industriale; definisce obiettivi, livello di rischio accettabile e requisiti di sicurezza.

- **Service Provider (SP)**: fornitore di servizi tecnici (ad esempio integrazione, manutenzione, gestione e supporto) che implementa e mantiene le misure richieste dall'Asset Owner.

- **Product Supplier**: produttore o fornitore di componenti, dispositivi e software per IACS; deve sviluppare prodotti con requisiti di sicurezza e gestire vulnerabilita e aggiornamenti.

- **System Integrator**: figura spesso inclusa nel perimetro dei Service Provider; realizza l'integrazione tra componenti e sistemi, traducendo i requisiti in una architettura coerente e sicura.

La chiara definizione di ruoli e responsabilita lungo tutto il ciclo di vita dell'impianto consente di ridurre le aree di ambiguita, migliorare il coordinamento operativo e aumentare la resilienza complessiva del sistema.


