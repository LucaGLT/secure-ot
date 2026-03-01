---
tags: []
created: '2026-03-01'
title: 'perché una norma in più'
---

# Perché avevamo bisogno della IEC 62443 in ambito Embedded Operation Technology?

Negli ultimi anni la cybersecurity è diventata un tema centrale anche nei sistemi embedded e nei contesti industriali. Tuttavia, una domanda emerge spesso tra i professionisti tecnici:

> Se esiste già una vasta letteratura sulla cybersecurity in ambito IT, perché è stata necessaria una norma specifica come la IEC 62443 per l’Operation Technology (OT)?

La risposta non è tecnica in senso stretto. È architetturale e sistemica.

---

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

Un sistema IT è generalmente:

* dinamico
* aggiornabile frequentemente
* replicabile
* virtualizzato
* monitorato 24/7

Un sistema OT embedded è spesso:

* deterministico
* installato per 10–20 anni
* difficilmente aggiornabile
* fisicamente accessibile
* privo di SOC dedicato

Applicare la cybersecurity IT "as is" significa ignorare queste differenze strutturali.

---

## In OT la sicurezza non protegge solo dati

Nel mondo IT la cybersecurity protegge principalmente:

* informazioni
* servizi digitali
* infrastrutture logiche

Nel mondo OT il software controlla:

* attuatori
* energia
* pressione
* temperatura
* movimento

Un attacco informatico può quindi trasformarsi in:

* danno fisico
* fermo impianto
* alterazione di misure
* rischio per operatori

Qui entra in gioco un elemento che in IT enterprise è marginale: l’interazione tra **security e safety**.

In OT, un attacco malevolo può generare lo stesso effetto di un guasto accidentale. Per questo security e safety devono essere progettate in modo coordinato.

---

## Il vero salto logico della IEC 62443

La IEC 62443 non reinventa la crittografia.
Non introduce nuovi algoritmi.
Non sostituisce le best practice IT.

Introduce qualcosa di diverso:

> Un modello architetturale per progettare la sicurezza in sistemi industriali.

I concetti chiave sono:

* Zone
* Conduits
* Security Level (SL)
* Foundational Requirements
* Segmentazione basata sul rischio

La sicurezza non è più un insieme di meccanismi (password, TLS, firewall), ma una proprietà strutturale dell’architettura.

---

## Da protezione del componente a protezione del dominio

La cybersecurity IT tradizionale tende a proteggere endpoint e servizi.

La IEC 62443 sposta l’attenzione su:

* domini di fiducia
* confini architetturali
* controllo dei flussi tra zone
* contenimento della propagazione laterale

Non si tratta di proteggere "il PLC" o "l’HMI".
Si tratta di definire quale livello di sicurezza deve avere una zona e quali controlli devono governare ogni attraversamento di confine.

Questo rende possibile:

* assegnare un Security Level Target (SL-T)
* misurare un Security Level Achieved (SL-A)
* effettuare gap analysis formali
* dimostrare coerenza tra rischio e architettura

---

## Perché non bastano password e cifratura

Password e TLS rispondono solo a una parte del problema:

* autenticazione
* confidenzialità

Ma non rispondono a domande strutturali come:

* Come limito la propagazione da un dispositivo compromesso?
* Come separo dominio IT e dominio OT?
* Come gestisco l’accesso manutentivo temporaneo?
* Come assegno formalmente un livello di protezione a una parte del sistema?

Senza un modello architetturale, la sicurezza resta frammentata.

---

## IT critica e OT: una differenza di biomeccanica

È vero: anche in IT esistono sistemi critici (banche, e-commerce, infrastrutture cloud). Ma tali sistemi sono progettati nativamente con:

* ridondanza massiva
* segmentazione avanzata
* monitoraggio continuo
* team dedicati
* orchestrazione distribuita

Molti sistemi industriali embedded non nascono con queste caratteristiche.

La IEC 62443 fornisce un framework per progettare sicurezza in ambienti che:

* non possono essere patchati frequentemente
* non sono cloud-native
* non dispongono di resilienza distribuita
* hanno cicli di vita molto lunghi

---

## Conclusione

La IEC 62443 non sostituisce la cybersecurity IT.
La integra e la adatta a un contesto diverso.

Non è una norma “in più”.
È un modello di progettazione necessario per sistemi embedded e industriali che governano processi fisici.

In sintesi:

> La cybersecurity IT protegge informazioni.
>
> La IEC 62443 aiuta a progettare sistemi OT che restino sicuri anche quando un attacco diventa evento fisico.

Ed è questo il salto logico e strategico che rende la norma necessaria in ambito Embedded Operation Technology.
