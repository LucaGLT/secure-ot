# LinkedIn Editorial Roadmap -- 12 Weeks

## Forging Security: From Architecture to IEC 62443

------------------------------------------------------------------------

## Week 1 -- Security Is Not an Add-On

### Metaphor

A label taped onto a PCB.

### Concept

Security cannot be attached at the end of development. 

### Application

Early architectural decisions define trust boundaries and attack surface.

### Call-to-Action

If final security validations disappeared tomorrow,how much resilience would remain in your architecture?

[x] Done

------------------------------------------------------------------------

## Week 2 -- Security Is Forged, Not Tested

### Metaphor

The forging of a katana blade.

### Concept

Robustness is the outcome of a disciplined, sequential process.

### Application

Secure design must be embedded in lifecycle decisions, not deferred to testing.

### Call-to-Action

Is resilience forged by design --- or certified at the end?

[x] Done

------------------------------------------------------------------------

## Week 3 -- Stima della reworking

### Premessa

Nel mio lavoro Prima di inziare un progetto, devo pianificarlo per stimare l'effort e per stabilire quanto verrà a costare.
Da questo dipende il prezzo al cliente.

Stimo la fase di progettazione, lo sviluppo. la fase di test execution e anche la fase di rilavorazione post test.

### Domanda

MA quanto deve essere stimata la rilavorazione rispetto allo sviluppo?

100% significa che puoi buttare via tutto e riscrivere da zero. compresa la tua reputazione da progettista

50% è ancora alto e genere nu prezzo non competitivo

10% potrebbe essere un buon compromesso.

Ma questo, con una certa approssimazione, significa che come progettista stai garantendo che il 90% dei test avranno successo ancora prima di inziare i test.

Ci hai mai pensato?

### Call-to-Action

Il CLiente ti potrebbe chiedere: sei certo che il 90% dei test passeranno?
Come convinci il tuo cliente di questa tua certezza?

[x] Done

------------------------------------------------------------------------

# Transition to IEC 62443 Journey

------------------------------------------------------------------------

## Week 4+5 -- Why IEC 62443 Exists

### Domanda

Perché avevamo bisogno della IEC 62443 in ambito Embedded Operation Technology?

### Metaphor

Progettare il sistema di sicurezza di un museo non è la stessa cosa che progettare il sistema di sicurezza di una diga.

Prima ancora di chiederti come proteggere, dovresti porti due domande fondamentali:

Che cosa stai proteggendo?
Che cosa succede se la protezione fallisce?

In un museo, un fallimento significa la perdita di opere irripetibili, secoli di creatività umana, identità culturale, memoria collettiva che possono essere danneggiati o sottratti.

In una diga, un fallimento significa la perdita di controllo su un sistema che accumula e rilascia energia sottoforma di masse d'acqua, rischiando impatti a catena, danni fisici e potenziali rischi per le persone.

Entrambi richiedono sicurezza, ma la natura del rischio è diversa.

E quando cambia la natura di ciò che proteggi, cambia anche l’architettura della protezione.

Potremmo chiederci: Con così tanta letteratura e best practice già disponibili nella Cybersecurity IT, avevamo davvero bisogno di una nuova norma come la IEC 62443 per i sistemi embedded in ambito Operational Technology?

Approfodisci con questo articolo: LINK

-----

What are you protecting?

Designing the security system of a museum is not the same as designing the security system of a dam.

Before asking how to protect, you should ask two fundamental questions:

What are you protecting?
What happens if protection fails?

In a museum, failure means the loss of irreplaceable works of art, centuries of human creativity, cultural identity, and collective memory that can be damaged or stolen.

In a dam, failure means the loss of control over a system that stores and releases energy in the form of massive bodies of water, risking cascading effects, physical damage, and potential harm to people.

Both require security. But the nature of the risk is different.

And when the nature of what you protect changes, the architecture of protection must change as well.

With so much literature and best practice already available in IT cybersecurity, did we really need a new standard like IEC 62443 for embedded systems in Operational Technology?

Explore the full discussion in this article: LINK

[x] Draft del post
[x] Scrivere Articolo (vedi file Post\Post05-perché una norma in più.md ) -> Done
[x] Pubblicare Articolo -> Done
[x] Mettere link Articolo su post e Schedule -> Done

### Concept

OT environments require a different security logic than IT.

### Application

Understand industrial context before applying security frameworks.

### Call-to-Action

Are you applying IT logic to OT problems?

------------------------------------------------------------------------

## Week 6 -- Zones & Conduits

### Metaphor

Compartments in a ship preventing flooding.

### Concept

Segmentation reduces systemic risk.

### Application

Design clear communication paths and isolate critical assets.

### Call-to-Action

If one zone fails, how far does the impact travel in your system?

------------------------------------------------------------------------

## Week 7 -- Security Levels (SL)

### Metaphor

Hardness and flexibility balanced in a blade.

### Concept

Security levels reflect risk tolerance, not marketing targets.

### Application

Define SL based on threat modeling and operational context.

### Call-to-Action

Are your security levels aligned with real threats --- or compliance expectations?

------------------------------------------------------------------------

## Week 8 -- Foundational Requirements

### Metaphor

The core structural elements of a bridge.

### Concept

Identity, integrity, and availability are systemic properties.

### Application

Translate FR into design constraints, not checklist items.

### Call-to-Action

Which foundational requirement drives your architecture the most?

------------------------------------------------------------------------

## Week 9 -- Secure Development Lifecycle (IEC 62443-4-1)

### Metaphor

A controlled production line with quality gates.

### Concept

Process discipline defines outcome quality.

### Application

Embed security reviews in development milestones.

### Call-to-Action

If your process defines quality, who forges security in your SDLC?

------------------------------------------------------------------------

## Week 10 -- Component Requirements (IEC 62443-4-2)

### Metaphor

Reinforced joints in structural engineering.

### Concept

Components must enforce security functions by design.

### Application

Implement authentication, integrity and secure boot at component level.

### Call-to-Action

Are your components secure by capability --- or by configuration?

------------------------------------------------------------------------

## Week 11 -- Lifecycle & Patch Management

### Metaphor

Maintenance of a bridge over decades.

### Concept

Security continues beyond release.

### Application

Define update policies, vulnerability handling and ownership.

### Call-to-Action

Is your lifecycle strategy proactive --- or reactive?

------------------------------------------------------------------------

## Week 12 -- Governance & Responsibility

### Metaphor

The master swordsmith overseeing the entire forge.

### Concept

Security ownership must be clearly defined.

### Application

Align engineering, IT and leadership responsibilities.

### Call-to-Action

Who truly owns security in your organization --- design, IT, or governance?
