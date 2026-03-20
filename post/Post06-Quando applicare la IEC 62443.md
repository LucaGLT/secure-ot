# Quando applicare la IEC 62443 al mio sistema?

Sto progettando o rimodernando un sistema di automazione dei miei processi produttivi, di controllo e di supervisione del laboratorio, di gestione dei dati di processo: ma nel mio caso, **si applica la IEC 62443**?

Questa è la domanda!

La risposta è più semplice di quanto si possa pensare.
Ma non lasciatevi ingannare dal *"non ho dati rilevanti da proteggere, non gestisco anagrafiche clienti, quindi non serve alcuna sicurezza informatica."*

Ecco: questo è proprio l'approccio sbagliato.

> **Ambito della IEC 62443**
>
> La IEC 62443 si applica ai sistemi **IACS** (*Industrial Automation and Control Systems*), cioè all'insieme di componenti hardware, software, reti, persone e procedure che monitorano o controllano processi fisici industriali.
>
> **Criterio pratico di inclusione**: se un sistema può influenzare, direttamente o indirettamente, il comportamento operativo del processo fisico (comandi, configurazioni, logiche di controllo, disponibilità o integrità dei dati di processo), allora rientra nel perimetro IEC 62443.

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

## Checklist operativa (5 passi)

Una volta capito che la IEC 62443 è rilevante per il tuo sistema, segui questi passaggi per applicarla già in fase di progettazione:

1. **Definisci il perimetro IACS**: elenca asset, funzioni, interfacce e confini tra dominio IT e dominio OT.
2. **Mappa Zone e Conduit**: segmenta l'architettura in aree omogenee e identifica tutti i canali di comunicazione.
3. **Valuta i rischi e imposta gli obiettivi di sicurezza**: stima impatti e minacce per ogni zona/conduit e definisci il Security Level target.
4. **Traduci gli obiettivi in requisiti tecnici e organizzativi**: controlli di accesso, hardening, gestione patch, monitoraggio, logging e procedure operative.
5. **Pianifica implementazione e verifica**: roadmap a priorità, test di efficacia, riesame periodico e miglioramento continuo.

Approfondiremo questi punti nei prossimi articoli.
