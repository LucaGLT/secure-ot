---
title: "Principi della Norma IEC 62443"
author: "Gianluca TATA"
last_updated: "2026-03-10"
---

## Zone di Sicurezza e Conduits

### Introduzione

Questo capitolo illustra i concetti fondamentali di zone di sicurezza (Security Zones) e conduits, elementi essenziali per la segmentazione e la protezione dei sistemi industriali.

### Contenuti Principali

- Definizione di Zona di Sicurezza (Security Zone)
- Concetto di Conduit (percorso di comunicazione)
- Modelli di architettura (DMZ, zone annidate, etc.)
- Principi di segmentazione
- Identificazione delle criticità in base alla zonizzazione
- Casi d'uso e applicazioni pratiche

### Definizione di Zona di Sicurezza (Security Zone)

Nella IEC 62443, una `Security Zone` è un **insieme logico o fisico di asset che condividono requisiti di sicurezza omogenei**.

L'obiettivo della zonizzazione è raggruppare sistemi, dispositivi e applicazioni con livello di criticita simile, in modo da applicare controlli coerenti con il rischio e ridurre la complessità della protezione dell'intero impianto. Una zona può includere PLC, HMI, server di supervisione, workstation di engineering o altri componenti che svolgono funzioni correlate e con esposizione comparabile alle minacce.

La definizione delle zone non e solo una scelta di rete, ma una decisione architetturale che tiene conto di processo industriale, impatto operativo, responsabilità organizzative e requisiti normativi. In pratica, la zona rappresenta il perimetro entro cui si stabiliscono regole comuni di accesso, monitoraggio, aggiornamento e gestione delle anomalie. Questo approccio consente di applicare il principio della `Defence in Depth`, limitando la propagazione di incidenti e migliorando la resilienza complessiva del sistema.

### Concetto di Conduit (percorso di comunicazione)

Il `Conduit` è il **percorso controllato di comunicazione tra due `Security Zone`**.

Nella logica IEC 62443, non è un semplice collegamento di rete, ma un canale governato da regole precise, progettato per far transitare solo i flussi strettamente necessari tra domini con requisiti potenzialmente diversi. Il suo compito principale è proteggere il confine tra zone, applicando controlli che riducano il rischio di accessi non autorizzati, movimenti laterali e alterazioni dei dati.

Un Conduit può includere firewall, regole ACL, proxy, gateway industriali, sistemi di ispezione del traffico, meccanismi di autenticazione e registrazione eventi. La sua efficacia dipende dalla coerenza tra policy definite e comportamento reale dei flussi, per questo deve essere progettato insieme alla zonizzazione e verificato nel tempo. In termini pratici, i conduits consentono di mantenere la necessaria interoperabilità tra funzioni operative diverse, senza rinunciare al controllo dei confini e alla robustezza dell'architettura.

### Modelli di architettura (DMZ, zone annidate, etc.)

La segmentazione secondo IEC 62443 non segue un unico schema architetturale, ma si adatta al contesto industriale, alla criticità dei processi e al profilo di rischio dell'impianto. Tuttavia, alcuni **modelli ricorrenti** si sono affermati nella pratica per la loro efficacia nel contenere le minacce e facilitare la gestione della sicurezza informatica.

Il modello `DMZ (Demilitarized Zone)` è uno dei più diffusi negli ambienti OT (Operational Technology) che devono interfacciarsi con reti IT aziendali. Una DMZ è una zona intermedia, con requisiti di sicurezza intermedi, che media gli accessi tra il dominio IT (uffici, gestionali) e i sistemi DCS/SCADA/PLC critici. In pratica, la DMZ ospita applicazioni di front-end, concentratori dati, gateway o proxy che filtrano e traducono i comandi prima che raggiungano la zona operativa. Questo modello riduce significativamente il rischio di movimenti laterali da un'intrusione IT verso i sistemi di controllo, allineandosi al principio di defence in depth e ai requisiti SR di IEC 62443-3-3 su segmentazione e controllo dei flussi di comunicazione.

Un secondo approccio diffuso è il modello di `Nested Zones` (Zone Annidate), in cui zone di minore criticità si trovano all'interno di zone di maggiore criticità, creando livelli di isolamento progressivamente più ristrittivi. Ad esempio, in un impianto di produzione, potrebbe esistere una zona esterna per i sistemi diagnostici e di monitoraggio remoto (Security Level 1), una zona intermedia per i controllori di settore (Security Level 2), e una zona interna per il nucleo critico di controllo dei processi (Security Level 3-4). Ogni passaggio tra livelli richiede un conduit specifico con controlli proporzionati al differenziale di rischio. Le zone annidate permettono di applicare il principio di `Least Privilege` a livello architetturale: ogni funzione operativa riceve solo i diritti e l'accesso necessari alla sua zona, senza esposizione ai sistemi esterni meno controllati. Questo modello è particolarmente efficace in ambienti dove coesistono funzioni di automazione, pianificazione della produzione, manutenzione remota e supervisione esterna, poiché permette di bilanciare operabilità e sicurezza senza sacrificare né l'una né l'altra.

La scelta tra `DMZ`, `Nested Zones` o combinazioni ibride dipende dalla **topologia fisica e logica** dell'impianto, dal numero e dalla natura delle connessioni esterne, dal profilo di minaccia prospettico e dalla capacità organizzativa di gestire zone multiple. In tutti i casi, IEC 62443 richiede che il modello architetturale sia documentato, che i confini di zona siano chiari (con mappatura esplicita degli asset e dei Conduit associati), e che i controlli tecnici (firewall, ACL, sistemi di detection) siano configurati e verificati in modo coerente con i requisiti di Security Level assegnati. L'importante è che ogni zona disponga di un'architettura di comunicazione esplicita e che nessun asset operi "fuori zona" in modo incontrollato.

### Principi di segmentazione

La segmentazione di una rete OT non è una scelta puramente tecnica, ma un'espressione di **principi di sicurezza informatica fondamentali** che IEC 62443 eredita dalla teoria della sicurezza dell'informazione e l'adatta al contesto industriale.

Il primo principio è la `Defence in Depth` (Difesa in Profondità), già citata nei paragrafi precedenti: la sicurezza non deve dipendere da una singola linea di difesa, ma da **molteplici barriere sovrapposte**, dove ogni zona rappresenta un livello di controllo indipendente. Se un attaccante compromette un segmento, la segmentazione limita la sua capacità di muoversi lateralmente verso le funzioni critiche.

Un secondo principio cruciale è il `Least Privilege` (Minimo Privilegio): ogni asset, utente e componente di comunicazione deve disporre solo dei diritti e dell'accesso strettamente necessari per svolgere la sua funzione. In termini di zone, questo significa che le comunicazioni tra zone devono essere explicit allow (lista bianca di flussi autorizzati) piuttosto che implicit deny (lista nera di flussi proibiti), e ogni connessione deve essere documentata e giustificata dal punto di vista funzionale e di rischio.

Un terzo principio è la `Separation of Duties` (Separazione dei Compiti), che in ambito OT si traduce nella divisione delle zone secondo responsabilità organizzative e tecniche: ad esempio, la zona di engineering (dove si progettano i comandi) dovrebbe essere separata dalla zona operativa (dove i comandi vengono eseguiti), con un conduit intermedio che valida e autorizza le transizioni di stato. Questo principio riduce il rischio di errori innocenti e complica gli attacchi volti a modificare il comportamento del sistema mediante accesso "dall'interno".

Un quarto principio, sempre presente in IEC 62443, è l'`Observability` (Osservabilità): una segmentazione efficace non può basarsi solo su isolamento fisico/logico, ma deve includere **monitoraggio continuo e tracciamento** di tutti i flussi di comunicazione tra zone. Ogni Conduit deve disporre di sistemi di logging, alert e rilevamento anomalie che permettano agli operatori e ai team di sicurezza di identificare comportamenti sospetti in tempo reale.

La segmentazione deve inoltre essere `Adattiva al rischio`: non tutte le Zone hanno lo stesso livello di protezione, e non tutti i Conduit hanno lo stesso grado di controllo. Le zone di Security Level 3-4 (sistema critico, controllo dei processi) richiedono una segmentazione più ristrittiva rispetto alle zone di Security Level 1-2 (supporto, monitoraggio non critico). Allo stesso modo, i Conduit verso reti esterne (Internet, partner, servizi cloud) richiedono controlli più severi rispetto ai Conduit interni tra zone dello stesso impianto. IEC 62443-3-3 fornisce una matrice di requisiti SR che variano con il Security Level, permettendo al progettista di dimensionare la segmentazione in modo proporzionato al contesto.

Infine, la segmentazione deve essere **documentata, governata e verificata**: non è sufficiente implementare Zone e Conduit, occorre mantenersi un inventario aggiornato degli asset per zona, una matrice di comunicazioni autorizzate, una policy di change management per le modifiche ai Conduit, e verifiche periodiche che la configurazione reale sia coerente con l'intenzione progettuale. Questo garantisce che la segmentazione rimanga efficace nel tempo, anche man mano che l'impianto evolve e nuovi sistemi vengono integrati.
