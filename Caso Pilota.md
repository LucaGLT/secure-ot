---
tags: []
created: '2026-02-14'
title: 'Caso Pilota'
---

Perfetto. Qui facciamo un passo strutturale: non parliamo di tecnologia, ma di chi è responsabile di cosa, prima e dopo.
Questa mappa è il punto in cui Safety e Cyber iniziano a parlarsi sul serio.


---

Mappa delle responsabilità

Uomo vs Sistema

AS-IS → TO-BE


---

1. Prima: situazione attuale (AS-IS)

Ruolo dell’uomo (operatore / tecnico)

L’operatore oggi è il vero orchestratore del processo.

È responsabile di:

Coordinare l’avvio dei diversi apparati (pressione, temperatura, acquisizione).

Sincronizzare manualmente le fasi del test.

Verificare che i parametri impostati siano corretti.

Riconoscere condizioni anomale durante il test.

Decidere quando interrompere una prova.

Estrarre i dati da più strumenti.

Aggregare i dati e costruire il report finale.

Garantire, di fatto, la coerenza complessiva della prova.


👉 La safety operativa dipende fortemente dal comportamento umano.
👉 Il sistema “esegue”, ma non governa.


---

Ruolo del sistema

Il sistema oggi ha un ruolo esecutivo e passivo.

Si limita a:

Controlli locali tramite PLC o regolatori stand-alone.

Applicare setpoint impostati manualmente.

Generare dati grezzi (log, file, misure).

Attivare protezioni basilari (se presenti) su singoli apparati.


Non fa:

Coordinamento tra sottosistemi.

Validazione globale del processo.

Correlazione automatica dei dati.

Verifica di coerenza di una prova end-to-end.


👉 Il sistema non ha una visione del processo, solo di parti.


---

Conseguenza chiave (AS-IS)

L’errore più pericoloso è l’errore umano.

Il rischio cyber è quasi nullo perché il sistema è isolato.

La ripetibilità è una funzione dell’esperienza dell’operatore.



---

2. Dopo: scenario target (TO-BE)

Qui avviene il cambio di paradigma:
l’uomo non coordina più, ma supervisiona.


---

Ruolo dell’uomo (ridefinito)

L’operatore diventa supervisore e decisore, non esecutore.

È responsabile di:

Selezionare la prova / ricetta di test.

Confermare le condizioni iniziali (pezzo corretto, setup corretto).

Autorizzare l’avvio del ciclo automatico.

Monitorare l’andamento del test (localmente o da remoto).

Intervenire in caso di allarme o evento anomalo.

Validare il risultato finale del test.

Approvare il report generato dal sistema.


Non è più responsabile di:

Sincronizzare manualmente i sottosistemi.

Avviare singolarmente gli apparati.

Raccogliere o aggregare dati.

“Tenere a mente” lo stato del processo.


👉 La responsabilità umana si sposta dal fare al controllare.


---

Ruolo del sistema (ridefinito)

Il sistema diventa regista del processo.

È responsabile di:

Coordinare automaticamente tutti i sottosistemi.

Applicare sequenze temporali coerenti e ripetibili.

Validare parametri prima dell’avvio.

Gestire interlock e condizioni di abilitazione.

Raccogliere dati in modo sincronizzato e correlato.

Associare dati ↔ prova ↔ pezzo ↔ condizioni.

Generare automaticamente il report di test.

Tracciare eventi, allarmi, interventi umani.


👉 Il sistema conosce il processo end-to-end.


---

3. La linea di confine critica: cosa NON deve mai passare al sistema

Qui nasce la convivenza Safety ↔ Cyber.

Sempre in mano al sistema Safety (non IT, non SCADA)

Arresto per condizioni pericolose (pressione, temperatura).

Depressurizzazione sicura.

Interlock fisici (porte, ripari).

Reset di sicurezza solo in presenza fisica.


👉 Nessun PC, tablet o rete decide sulla sicurezza.


---

Sempre in mano all’uomo

Autorizzazione iniziale alla prova.

Decisione finale sulla validità del test.

Gestione delle anomalie non previste.

Accettazione o scarto del pezzo.


👉 L’uomo resta responsabile del giudizio.


---

4. Tabella di sintesi (molto utile in documenti ufficiali)

Attività	AS-IS	TO-BE

Coordinamento apparati	Uomo	Sistema
Avvio sequenze	Uomo	Sistema (con autorizzazione uomo)
Monitoraggio	Uomo	Uomo + Sistema
Gestione sicurezza	Uomo + protezioni locali	Sistema Safety indipendente
Raccolta dati	Uomo	Sistema
Aggregazione dati	Uomo	Sistema
Creazione report	Uomo	Sistema
Validazione risultato	Uomo	Uomo
Accesso remoto	Assente	Supervisionato e limitato



---

5. Implicazione fondamentale (da non perdere)

Nel TO-BE:

Ogni responsabilità che passa dall’uomo al sistema

deve essere specificata,

verificabile,

testabile.


Ogni responsabilità che passa al sistema

diventa automaticamente un tema di Cyber Security.


Ogni responsabilità che resta safety-critical

deve rimanere fuori dalla portata del cyber.



Questa mappa è esattamente ciò che serve per:

scrivere requisiti funzionali,

derivare requisiti di safety,

derivare requisiti di cyber security,

spiegare il progetto a un auditor senza farsi male.


Se vuoi, nel prossimo passo possiamo:

derivare i requisiti direttamente da questa mappa,

oppure costruire una RACI formale (uomo, sistema, safety system, IT).