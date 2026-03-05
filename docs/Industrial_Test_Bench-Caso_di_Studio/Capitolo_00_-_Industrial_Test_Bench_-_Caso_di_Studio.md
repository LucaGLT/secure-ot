---
title: "Industrial Test Bench - Caso di Studio"
author: "Gianluca TATA"
last_updated: "2026-03-05"
---

# Industrial Test Bench - Caso di Studio

## Panoramica

Questo documento di studio fornisce un'analisi critica della piattaforma di test industriale, coprendone lo *stato attuale* (**AS-IS**), lo *stato target desiderato* (**TO-BE**), e la trasformazione architettonica necessaria per introdurre automazione, capacità di supervisione remota e controlli di sicurezza informatica in conformità agli **standard IEC 62443**, mantenendo l'indipendenza della sicurezza funzionale.

### Capitolo 01 - Descrizione del Test Bench AS-IS [→](Capitolo_01_-_Descrizione_del_Test_Bench_AS-IS.md)

Il capitolo descrive l'architettura attuale del test bench basata su PLC locali con coordinamento manuale per i sottosistemi di pressione e temperatura. Attualmente non esiste connettività remota. Le responsabilità operative ricadono completamente sull'operatore che coordina manualmente la sincronizzazione tra i sottosistemi, estrae i dati e assembla i rapporti. I dati provengono da più fonti indipendenti senza correlazione automatica.

Contenuti principali:

- Architettura di controllo basata su PLC locale
- Flusso operativo manuale
- Gestione e reportistica dei dati
- Caratteristiche di sicurezza attuali (basate su consapevolezza dell'operatore)
- Modello di responsabilità AS-IS

### Capitolo 02 - Addendum Tecnico AS-IS [→](Capitolo_02_-_Addendum_Tecnico_AS-IS.md)

Questo capitolo fornisce una descrizione tecnica dettagliata dei componenti hardware, dell'architettura di controllo e dei flussi di dati attuali. Include un inventario completo dell'hardware (PLC, HMI, sottosistema pressione con pompa e valvole, sottosistema temperatura con controller standalone, datalogger industriale e Device Under Test dotato di API non utilizzata). Il capitolo evidenzia anche i gap di integrazione e le limitazioni della configurazione attuale.

Contenuti principali:

- Inventario e specifiche tecniche dei componenti
- Sottosistema pressione (sensori, valvole, controllo)
- Sottosistema temperatura (controller indipendente)
- Apparecchiature di acquisizione dati
- Caratteristiche del DUT (Device Under Test)
- Flussi di dati durante e dopo il test
- Gap di integrazione identificati

### Capitolo 03 - Descrizione Interfacce e Flussi di Dati AS-IS [→](Capitolo_03_-_Descrizione_Interfacce_e_Flussi_di_Dati_AS-IS.md)

Il capitolo fornisce una mappatura dettagliata di tutte le interfacce fisiche e logiche del sistema, inclusi i flussi di controllo, misurazioni e acquisizione dati. Include tabelle esaustive delle interfacce di controllo (da HMI a PLC, comandi verso pompe e valvole, feedback di pressione e temperatura), interfacce di acquisizione dati (dal sensore al datalogger) e interfacce di esportazione dati (SD/USB verso operatore). Identifica anche l'API del DUT (attualmente non utilizzata) come capabilità presente ma non integrata nel flusso operativo.

Contenuti principali:

- Mappa delle interfacce fisiche e logiche
- Interfacce di controllo e sicurezza
- Interfacce di acquisizione dati
- Interfacce di esportazione file
- Interfaccia API del DUT (non utilizzata)
- Flussi di dati end-to-end
- Punti di correlazione e gap
- Touchpoint dell'operatore

### Capitolo 04 - Descrizione del Test Bench TO-BE [→](Capitolo_04_-_Descrizione_del_Test_Bench_TO-BE.md)

Il capitolo descrive l'architettura target che trasforma il sistema da un ambiente coordinato manualmente a una piattaforma integrata, automatizzata e parzialmente supervisionata a distanza. Il TO-BE introduce orchestrazione centralizzata del processo, infrastruttura di dati unificata, capacità di supervisione remota tramite HMI su PC e tablet, e separazione rigorosa tra logica di controllo del processo e funzioni di sicurezza. Il modello di responsabilità si evolve con il sistema che diventa orchestratore del processo e l'operatore supervisore.

Contenuti principali:

- Architettura di controllo centralizzata
- Infrastruttura di dati integrata
- Capacità di supervisione remota
- Architettura di sicurezza funzionale nel TO-BE
- Fondamenti di sicurezza informatica (IEC 62443)
- Modello di responsabilità TO-BE
- Caratteristiche chiave dello stato target

### Capitolo 05 - Analisi dell'Evoluzione delle Responsabilità AS-IS vs TO-BE [→](Capitolo_05_-_Analisi_dell'Evoluzione_delle_Responsabilità_AS-IS_vs_TO-BE.md)

Questo capitolo analizza la redistribuzione delle responsabilità nella transizione da AS-IS a TO-BE. In AS-IS l'operatore è l'orchestratore del processo (coordinamento manuale, verifica dei parametri, monitoraggio continuo, estrazione e aggregazione dei dati). Nel TO-BE il sistema diventa l'orchestratore (sequenze sincronizzate, validazione della configurazione, monitoraggio continuo automatico, raccolta e aggregazione dei dati) mentre l'operatore diventa l'autorità decisionale e supervisoria (autorizzazione all'avvio, supervisione del processo, convalida dei risultati). Il capitolo fornisce una tabella sintetica della ridistribuzione responsabilità tra Umano, Sistema e Logica di Sicurezza.

Contenuti principali:

- Cambio strutturale nel modello di responsabilità
- Coordinamento del processo: operatore → sistema
- Validazione parametri: operatore → sistema + operatore
- Monitoraggio: attivo → supervisorio
- Gestione dati: manuale → automatizzato
- Generazione rapporti: artigianale → generato automaticamente
- Nuova definizione del ruolo dell'operatore
- Implicazioni della trasformazione

### Capitolo 06 - Sfide Emergenti di Sicurezza Informatica e Interazione con la Sicurezza Funzionale [→](Capitolo_06_-_Sfide_Emergenti_di_Sicurezza_Informatica_e_Interazione_con_la_Sicurezza_Funzionale.md)

Il capitolo analizza come l'introduzione di connettività e automazione crea nuove superfici di esposizione ai rischi informatici che possono influenzare direttamente o indirettamente la sicurezza funzionale. Stabilisce il principio critico che la sicurezza funzionale non deve dipendere dall'integrità informatica, il che significa che la logica di sicurezza deve essere indipendente dai livelli supervisivi e dal controllo remoto non può bypassare i blocchi di sicurezza. Il capitolo descrive scenari di rischio combinato (manipolazione della ricetta, soppressione degli allarmi, controllo remoto non autorizzato) e le strategie di mitigazione.

Contenuti principali:

- Cambio nella natura del rischio (da errore umano a vulnerabilità sistemica)
- Nuove superfici di esposizione informatica
- Modello di interazione Sicurezza e Cyber Security
- Principio critico di progettazione (la sicurezza non dipende dal cyber)
- Scenari di rischio combinato
- Implicazioni di governance
- Considerazioni di validazione e test

### Capitolo 07 - Analisi dei GAP AS-IS vs TO-BE [→](Capitolo_07_-_Analisi_dei_GAP_AS-IS_vs_TO-BE.md)

Il capitolo fornisce un'analisi strutturata dei gap tra la configurazione attuale (AS-IS) e l'architettura desiderata (TO-BE) attraverso cinque aree di intervento: A) Orchestrazione del Processo, B) Gestione dei Dati e Tracciabilità, C) Sicurezza Funzionale, D) Sicurezza Informatica (OT), E) Governance e Gestione del Ciclo di Vita. Per ogni area sono definiti gli obiettivi macro, gli standard di riferimento, i passi di implementazione macro e i dettagli tecnici micro. L'analisi fornisce una roadmap strutturata per l'evoluzione architettonica del sistema.

Contenuti principali:

- Aree di intervento (5 aree principali)
- Obiettivi macro per ogni area
- Standard di riferimento (IEC 61508, ISO 13849, IEC 62443, IEC 61511, ISA-95, ALCOA+)
- Passi di implementazione macro
- Dettagli tecnici micro
- Sommario del gap
- Principi di trasformazione

### Capitolo 08 - Analisi Formale dei GAP secondo IEC 62443 [→](Capitolo_08_-_Analisi_Formale_dei_GAP_secondo_IEC_62443.md)

Il capitolo fornisce un'analisi formale secondo **IEC 62443** della configurazione attuale rispetto ai requisiti di sicurezza informatica. Definisce lo scope del sistema, identifica zone e condotti, determina il Security Level Target (SL-T = 2, basato su esposizione industriale moderata e implicazioni di sicurezza), valuta il Security Level Attuale (SL-A ≈ 0-1). Analizza il gap per ognuno dei 7 Foundational Requirements di IEC 62443-3-3 (FR1-FR7), valuta la maturità della sicurezza a livello componente e del programma, e conclude che l'architettura AS-IS è fisicamente sicura ma cyber immaturi e richiede interventi significativi in segmentazione, autenticazione, integrità, logging e governance.

Contenuti principali:

- Scopo e metodologia dell'analisi IEC 62443
- Definizione del sistema e modello di zone
- Determinazione del Security Level Target
- Valutazione dei 7 Foundational Requirements
- Gap analysis per ogni requisito (FR1-FR7)
- Valutazione della sicurezza a livello componente
- Valutazione del programma di sicurezza
- Conclusioni esecutive e raccomandazioni
