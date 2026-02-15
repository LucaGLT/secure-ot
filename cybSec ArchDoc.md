---
tags: []
created: '2026-02-13'
title: 'cybSec ArchDoc'
---

# Cybersecurity Architecture Definition

## Risk-Informed Baseline for Embedded Industrial Systems

> **DOCUMENTO COMMENTATO**
> Questo file rappresenta la versione *commentata* dello scheletro del documento.
> Le sezioni contengono **note guida** destinate all’autore (o al team) per orientare la scrittura del contenuto finale.
> Le note dovranno essere **rimosse** nella versione finale del documento.

---

## Capitolo 1 – Contesto, Scopo e Baseline di Rischio

> **Nota generale Capitolo 1**
> Questo capitolo ha uno scopo **analitico**, non progettuale.
> Qui NON si descrivono soluzioni tecniche.
> L’obiettivo è costruire una *baseline di rischio condivisa* che renda inevitabili (e difendibili) le decisioni del Capitolo 2.

### 1.1 Scopo del documento

> **Guida alla scrittura**
>
> * Spiegare perché il documento esiste e quale problema risolve.
> * Dichiarare che il documento definisce una *baseline architetturale*.
> * Specificare esplicitamente cosa NON è (manuale di implementazione, SDLC, compliance document).

---

### 1.2 Ambito di applicazione

> **Guida alla scrittura**
>
> * Definire chiaramente il dominio: embedded industrial systems.
> * Evitare esempi consumer o IT puri.
> * Specificare che l’architettura è applicabile a famiglie di prodotti, non a un singolo device.

---

### 1.3 Contesto operativo del sistema

> **Guida alla scrittura**
>
> * Descrivere l’ambiente di installazione (impianto, fabbrica, campo).
> * Indicare durata tipica del ciclo di vita.
> * Evidenziare interazioni con backend, SCADA, strumenti di manutenzione.
> * Non parlare ancora di protocolli o soluzioni.

---

### 1.4 Confini del sistema

> **Guida alla scrittura**
>
> * Chiarire cosa è in scope e cosa è out of scope.
> * Esplicitare che la rete esterna e l’impianto non sono implicitamente trusted.
> * Questo paragrafo serve a evitare fraintendimenti futuri.

---

### 1.5 Assunzioni e vincoli

> **Guida alla scrittura**
>
> * Elencare solo assunzioni rilevanti per la sicurezza.
> * Esempi: accesso fisico possibile, OTA necessario, risorse embedded limitate.
> * Le assunzioni devono essere *difendibili*, non ottimistiche.

---

### 1.6 Baseline di rischio

> **Nota generale sezione 1.6**
> Questa sezione raccoglie tutta l’analisi del rischio.
> Deve essere chiara, sintetica e direttamente collegabile alle decisioni architetturali successive.

#### 1.6.1 Asset critici

> **Guida alla scrittura**
>
> * Elencare solo asset che, se compromessi, generano impatti reali.
> * Motivare perché ogni asset è critico.
> * Evitare elenchi troppo lunghi.

---

#### 1.6.2 Profili di attaccante

> **Guida alla scrittura**
>
> * Considerare solo attaccanti realistici per il contesto industriale.
> * Includere insider e manutentori.
> * Evitare attaccanti ipotetici non giustificati.

---

#### 1.6.3 Superficie d’attacco

> **Guida alla scrittura**
>
> * Suddividere chiaramente: fisica, rete, software, update.
> * Questo paragrafo deve rendere evidente “da dove si entra”.

---

#### 1.6.4 Scenari di minaccia prioritari

> **Guida alla scrittura**
>
> * Descrivere pochi scenari ma rilevanti.
> * Ogni scenario deve avere una conseguenza chiara.
> * Questi scenari guideranno le scelte del Capitolo 2.

---

#### 1.6.5 Criteri di priorità e impatto

> **Guida alla scrittura**
>
> * Spiegare come vengono valutati i rischi (impatto operativo, safety, continuità).
> * Non usare metriche complesse se non necessarie.

---

#### 1.6.6 Rischio accettato ed esclusioni

> **Guida alla scrittura**
>
> * Dichiarare apertamente cosa NON viene mitigato.
> * Motivare sempre il rischio accettato.
> * Questo è un segno di maturità architetturale.

---

## Capitolo 2 – Cybersecurity Architecture (Baseline)

> **Nota generale Capitolo 2**
> Questo capitolo è **decisionale**.
> Ogni sezione deve rispondere alla domanda: “come mitighiamo gli scenari del Capitolo 1?”.

### 2.1 Scopo del capitolo e principi architetturali

> **Guida alla scrittura**
>
> * Ribadire che l’architettura è risk-informed.
> * Elencare pochi principi chiave (separazione fiducia, contenimento danno).

---

### 2.2 Visione architetturale di alto livello

> **Guida alla scrittura**
>
> * Descrivere l’architettura per domini, non per componenti.
> * Introdurre il concetto di strati di fiducia.
> * Inserire uno schema concettuale.

---

### 2.3 Root of Trust

> **Guida alla scrittura**
>
> * Usare la definizione formale già concordata.
> * Chiarire cosa è trusted e cosa no.
> * Evitare dettagli implementativi.

---

### 2.4 Secure Boot e catena di fiducia

> **Guida alla scrittura**
>
> * Descrivere la sequenza di verifiche.
> * Spiegare cosa succede in caso di fallimento.
> * Collegare esplicitamente agli scenari di minaccia.

---

### 2.5 Identità del dispositivo

> **Guida alla scrittura**
>
> * Spiegare perché l’identità è per-device.
> * Evidenziare il contenimento del danno.
> * Non entrare in PKI operative.

---

### 2.6 Comunicazioni sicure

> **Guida alla scrittura**
>
> * Dichiarare esplicitamente la rete non trusted.
> * Spiegare autenticazione e gestione delle sessioni.
> * Evitare dettagli di protocollo.

---

### 2.7 Aggiornamento firmware e recovery

> **Guida alla scrittura**
>
> * Descrivere il modello di update.
> * Evidenziare rollback e recovery.
> * Collegare alla Root of Trust.

---

### 2.8 Gestione del ciclo di vita e del debug

> **Guida alla scrittura**
>
> * Distinguere sviluppo, produzione, RMA.
> * Evidenziare il debug come rischio.
> * Non descrivere processi organizzativi.

---

### 2.9 Tracciabilità tra baseline di rischio e architettura

> **Guida alla scrittura**
>
> * Rendere esplicito il collegamento rischio → decisione.
> * Questa sezione chiude il cerchio del documento.

---

> **Nota finale**
> Una volta completato il contenuto e rimosse tutte le note guida, il documento deve essere verificato contro la **Definition of Done** prima di essere congelato come baseline.
