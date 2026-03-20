# Quando applicare la IEC 62443 al mio sistema?

Sto progettando o rimodernando un sistema di automazione dei miei processi produttivi, di controllo e di supervisione del laboratorio, di gestione dei dati di processo: ma nel mio caso, **si applica la IEC 62443**?

Questa è la domanda!

La risposta è più semplice di quanto si possa pensare.
Ma non lasciatevi ingannare dal *"non ho dati rilevanti da proteggere, non gestisco anagrafiche clienti, quindi non serve alcuna sicurezza informatica."*

Ecco: questo è proprio l'approccio sbagliato.

> **Ambito della IEC 62443**
>
> La IEC 62443 si applica ai sistemi **IACS** (*Industrial Automation and Control Systems*), cioè all'insieme di componenti hardware, software, reti, persone e procedure che monitorano o controllano processi fisici industriali.

La domanda di base va scomposta in poche domande puntuali che chiariscono il problema e il campo di applicazione della normativa sulla sicurezza informatica in ambito Operational Technology e di automazione industriale.

Eccole.

**1. Il sistema interagisce con macchine, sensori, attuatori o processi fisici?**

- **NO**: avete risolto il problema: siamo in puro dominio IT, pertanto la IEC 62443 non è il riferimento normativo principale.
- **Sì**: occorre indagare con le prossime domande.

**2. Il sistema gestisce solo dati in lettura senza influenzare direttamente i processi fisici?**

- **Sì**: in questo caso i dati dal campo operativo del sistema sono solo in uscita (sola lettura) e non c'è in alcun modo la possibilità di influenzare l'operatività del processo fisico; siamo ancora in puro dominio IT, pertanto la IEC 62443 non è il riferimento normativo principale. Questo implica però che il sistema **non può**:
  - dare comandi al processo,
  - alterare i dati di misura,
  - alterare il processo che genera i dati di misura,
  - configurare il sistema,
  - bypassare controlli di sicurezza o coerenza dei dati,
  - **rendere effettiva alcuna modifica operativa del processo, neanche involontariamente né per errori incontrollati del sistema**.
- **No**: è possibile fare configurazioni o addirittura inviare comandi; allora occorre indagare ulteriormente con le prossime domande.

**3. Una modifica o un errore nel sistema potrebbe fermare il processo, produrre risultati fisici errati o avere un impatto sulla safety?**

- **No**: in questo caso il sistema può interagire con il processo anche in modifica, ma non in modo così invasivo da produrre risultati potenzialmente errati, arrestare il processo o alterare la safety del processo stesso: sei in presenza di un sistema ibrido IT/OT leggero; consiglio di considerare la IEC 62443 come riferimento, pur mantenendo un Security Level basso.
- **Sì**: ci potrebbero essere impatti sull'operatività o sulla safety: rispondi anche alle prossime domande.

**4. Il sistema può essere modificato localmente collegandosi direttamente al dispositivo di controllo?**

- **Sì**: si introduce il tema dell'**accesso locale diretto**: molti sistemi industriali possono essere modificati collegando laptop, cavo Ethernet, porta seriale o porta USB; questo tipo di accesso permette di:
  - cambiare la logica PLC
  - modificare configurazioni
  - alterare parametri di sicurezza.
È quindi una superficie di attacco **anche senza rete**: per questo la IEC 62443 è rilevante **anche per sistemi isolati**.

- **No**: non c'è accesso diretto alle impostazioni; i problemi possono derivare solo da condizioni anomale: occorre indagare con le prossime domande.

**5. Il sistema può essere raggiunto da altre reti o da accessi remoti?**

- **Sì**: si introduce il rischio di **attacco remoto**:
  - rete aziendale
  - VPN
  - accesso remoto di manutenzione
  - gateway dati.
La connessione a reti esterne aumenta enormemente:
  - superficie di attacco
  - probabilità di compromissione
  - complessità della sicurezza.
È quindi necessario compartimentare in modo opportuno il sistema affinché una compromissione di una parte del software non arrivi allo strato di effettivo controllo del processo: fate riferimento alla IEC 62443, che vi guiderà nella progettazione a ***Zone*** e ***Conduit*** con livelli di sicurezza opportuni.

- **No**: in teoria non può essere raggiunto dall'esterno, ma occorre indagare con la prossima domanda.

**6. Il sistema è interconnesso solo tramite rete locale protetta e isolata?**

- **Sì**: fisicamente isolata, senza Wi-Fi: OT localmente connesso; la IEC 62443 è comunque altamente consigliata, soprattutto se hai risposto Sì alla domanda numero 3, ma puoi usare livelli di sicurezza bassi.
- **No**: il sistema può in effetti essere connesso ad altre reti, come rete di laboratorio o VPN, o può essere connesso via Wi-Fi: OT esternamente connesso, IEC 62443 fortemente raccomandata.

> **Criterio pratico di inclusione**: 
> se un sistema può influenzare, direttamente o indirettamente, il comportamento operativo del processo fisico (comandi, configurazioni, logiche di controllo, disponibilità o integrità dei dati di processo), allora rientra nel perimetro IEC 62443.

## Checklist operativa (5 passi)

Una volta capito che la IEC 62443 è rilevante per il tuo sistema, segui questi passaggi per applicarla già in fase di progettazione:

1. **Definisci il perimetro IACS**: elenca asset, funzioni, interfacce e confini tra dominio IT e dominio OT.
2. **Mappa Zone e Conduit**: segmenta l'architettura in aree omogenee e identifica tutti i canali di comunicazione.
3. **Valuta i rischi e imposta gli obiettivi di sicurezza**: stima impatti e minacce per ogni zona/conduit e definisci il Security Level target.
4. **Traduci gli obiettivi in requisiti tecnici e organizzativi**: controlli di accesso, hardening, gestione patch, monitoraggio, logging e procedure operative.
5. **Pianifica implementazione e verifica**: roadmap a priorità, test di efficacia, riesame periodico e miglioramento continuo.

Approfondiremo questi punti nei prossimi articoli.


----


Stesso articolo in Inglese :

# When Should I Apply IEC 62443 to My System?

I am designing or modernizing an automation system for my production processes, laboratory control and supervision, and process data management: but in my case, **does IEC 62443 apply**?

That is the question.

The answer is simpler than it may seem.
But do not be misled by: *"I don't have relevant data to protect, I don't manage customer records, so I don't need any cybersecurity."*

That is exactly the wrong approach.

> **Scope of IEC 62443**
>
> IEC 62443 applies to **IACS** (*Industrial Automation and Control Systems*), meaning the set of hardware components, software, networks, people, and procedures that monitor or control industrial physical processes.



The core question should be broken down into a few targeted questions that clarify the issue and the scope of this information security standard in Operational Technology and industrial automation.

Here they are.

**1. Does the system interact with machines, sensors, actuators, or physical processes?**

- **NO**: problem solved: this is purely an IT domain, so IEC 62443 is not the main normative reference.
- **Yes**: continue with the next questions.

**2. Does the system manage read-only data without directly influencing physical processes?**

- **Yes**: in this case, data from the operational field is output-only (read-only), and there is no way to influence physical process operations; this is still purely an IT domain, so IEC 62443 is not the main normative reference. However, this implies that the system **cannot**:
  - issue commands to the process,
  - alter measurement data,
  - alter the process that generates measurement data,
  - configure the system,
  - bypass security controls or data consistency checks,
  - **make any operational modification to the process effective, not even unintentionally or due to uncontrolled system errors**.
- **No**: configurations or even commands are possible; therefore, proceed with the next questions.

**3. Could a change or an error in the system stop the process, produce incorrect physical results, or impact safety?**

- **No**: in this case, the system may interact with the process (including modifications), but not in a way invasive enough to generate potentially incorrect results, stop the process, or alter process safety: you are dealing with a light IT/OT hybrid system; I recommend considering IEC 62443 as a reference while keeping a low Security Level.
- **Yes**: there may be impacts on operations or safety; answer the next questions as well.

**4. Can the system be modified locally by connecting directly to the control device?**

- **Yes**: this introduces the issue of **direct local access**: many industrial systems can be modified by connecting a laptop, Ethernet cable, serial port, or USB port; this type of access allows one to:
  - change PLC logic,
  - modify configurations,
  - alter safety parameters.
This is therefore an attack surface **even without a network**: for this reason, IEC 62443 is relevant **even for isolated systems**.

- **No**: there is no direct access to settings; issues may only derive from abnormal conditions: continue with the next questions.

**5. Can the system be reached from other networks or remote access paths?**

- **Yes**: this introduces the risk of **remote attack**:
  - corporate network,
  - VPN,
  - remote maintenance access,
  - data gateways.
Connection to external networks significantly increases:
  - attack surface,
  - likelihood of compromise,
  - security complexity.
It is therefore necessary to properly compartmentalize the system so that a compromise in one software component cannot reach the layer that actually controls the process: refer to IEC 62443, which will guide your ***Zone*** and ***Conduit*** design with appropriate security levels.

- **No**: in theory, it cannot be reached from outside, but proceed with the next question.

**6. Is the system interconnected only through a protected and isolated local network?**

- **Yes**: physically isolated, with no Wi-Fi: locally connected OT; IEC 62443 is still highly recommended, especially if you answered Yes to question 3, but you can use low security levels.
- **No**: the system may in fact be connected to other networks, such as a lab network or VPN, or may be connected via Wi-Fi: externally connected OT, IEC 62443 is strongly recommended.

> **Practical inclusion criterion**:
> if a system can influence, directly or indirectly, the operational behavior of a physical process (commands, configurations, control logic, availability or integrity of process data), then it falls within the IEC 62443 scope.

## Operational Checklist (5 steps)

Once you understand that IEC 62443 is relevant to your system, follow these steps to apply it already during the design phase:

1. **Define the IACS scope**: list assets, functions, interfaces, and boundaries between IT and OT domains.
2. **Map Zones and Conduits**: segment the architecture into homogeneous areas and identify all communication channels.
3. **Assess risks and set security objectives**: estimate impacts and threats for each zone/conduit and define the target Security Level.
4. **Translate objectives into technical and organizational requirements**: access controls, hardening, patch management, monitoring, logging, and operating procedures.
5. **Plan implementation and verification**: priority-based roadmap, effectiveness testing, periodic review, and continuous improvement.

We will dive deeper into these points in upcoming articles.

