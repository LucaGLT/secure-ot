# Confronto tra Norme Applicabili

## Motivazione della Scelta della IEC 62443

------------------------------------------------------------------------

# 1. Scopo del Documento

Il presente documento fornisce una comparazione tra le principali norme
applicabili al caso di studio del banco di test industriale, al fine di
giustificare formalmente la scelta della IEC 62443 come riferimento
principale per la Cyber Security dell'architettura TO-BE.

L'analisi considera: - Titolo completo della norma - Ambito di
applicazione - Scopo primario - Pertinenza rispetto al sistema in esame

------------------------------------------------------------------------

# 2. IEC 62443

## Industrial communication networks -- Network and system security

### Scopo primario

Fornire un framework completo per la Cyber Security dei sistemi di
automazione e controllo industriale (IACS), coprendo aspetti
organizzativi, architetturali, di sistema e di componente.

### Ambito

-   Sistemi PLC-based
-   Reti OT
-   Dispositivi industriali
-   Zone e conduits
-   Lifecycle di sicurezza

### Pertinenza nel caso di studio

La norma è specificamente progettata per ambienti industriali con
sistemi di controllo.\
Introduce concetti chiave come Security Level (SL), Foundational
Requirements, segmentazione di rete e protezione dei componenti
industriali.

È l'unica norma che fornisce un modello tecnico completo e specifico per
sistemi IACS come il banco di test oggetto del caso di studio.

------------------------------------------------------------------------

# 3. IEC 61508

## Functional safety of electrical/electronic/programmable electronic safety-related systems

### Scopo primario

Definire i requisiti per garantire la sicurezza funzionale dei sistemi
elettrici, elettronici e programmabili, introducendo il concetto di
Safety Integrity Level (SIL).

### Ambito

-   Failure sistematici
-   Failure casuali
-   Analisi di rischio safety
-   Lifecycle di sicurezza funzionale

### Pertinenza nel caso di studio

Rilevante per la parte di sicurezza legata a sovrapressione,
sovratemperatura e interlock fisici.\
Non copre attacchi intenzionali o minacce cyber.\
Non è una norma di Cyber Security.

È complementare alla IEC 62443 ma non sostitutiva.

------------------------------------------------------------------------

# 4. ISO 13849

## Safety of machinery -- Safety-related parts of control systems

### Scopo primario

Definire i requisiti di sicurezza delle parti di comando legate alla
sicurezza nelle macchine, introducendo il concetto di Performance Level
(PL).

### Ambito

-   Macchine industriali
-   Circuiti di sicurezza
-   Interlock
-   Arresti di emergenza

### Pertinenza nel caso di studio

Applicabile alla parte macchina del banco di test (interlock, E-Stop,
protezioni fisiche).\
Non affronta aspetti di Cyber Security o protezione delle reti
industriali.

------------------------------------------------------------------------

# 5. ISO/IEC 27001

## Information security management systems -- Requirements

### Scopo primario

Definire i requisiti per un sistema di gestione della sicurezza delle
informazioni (ISMS).

### Ambito

-   Governance organizzativa
-   Gestione documentale
-   Politiche di sicurezza
-   Controlli IT generici

### Pertinenza nel caso di studio

Rilevante a livello organizzativo e gestionale.\
Non fornisce requisiti tecnici specifici per PLC, dispositivi OT o
architetture IACS.\
È orientata prevalentemente al mondo IT.

Può supportare la governance ma non sostituisce la IEC 62443 per
l'architettura tecnica OT.

------------------------------------------------------------------------

# 6. NIST SP 800-82

## Guide to Industrial Control Systems (ICS) Security

### Scopo primario

Fornire linee guida per la sicurezza dei sistemi di controllo
industriale.

### Ambito

-   Best practice
-   Raccomandazioni tecniche
-   Linee guida operative

### Pertinenza nel caso di studio

Documento di riferimento tecnico molto utile, ma non è una norma
internazionale strutturata con livelli di sicurezza formalizzati come la
IEC 62443.\
Non introduce un modello certificabile basato su Security Level.

------------------------------------------------------------------------

# 7. Conclusione Comparativa

Nel contesto del banco di test industriale:

-   La sicurezza funzionale è coperta da IEC 61508 / ISO 13849.
-   La governance generale può essere supportata da ISO 27001.
-   Le linee guida tecniche possono essere integrate con NIST SP 800-82.
-   Tuttavia, la Cyber Security specifica per sistemi di automazione
    industriale è formalmente e strutturalmente coperta dalla IEC 62443.

La IEC 62443 è quindi scelta come norma primaria di riferimento poiché:

-   È specifica per sistemi IACS.
-   Integra aspetti tecnici e organizzativi.
-   Introduce il concetto di Security Level applicabile
    all'architettura.
-   È coerente con ambienti PLC-based e reti OT.
-   È riconosciuta come standard di riferimento per la Cyber Security
    industriale.

La scelta non esclude le altre norme, ma le integra in modo
complementare.
