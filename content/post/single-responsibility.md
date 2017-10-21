---
title: Single Responsibility
subtitle: Single Responsibility.
date: 2017-08-28
tags: ["Clean code", "Software entropy", "Refactoring", "SOLID"]
---

La S dei principi SOLID stà per Single Responsibility Principle (SRP), la sua definizione tradotta in italiano é la seguente:

> Una classe dovrebbe avere uno ed unico motivo per cambiare

Cosa significa?
Significa avere classi più piccole ognuna con una sola responsabilità! Su molti testi si trova consigliato classi di dimensioni che non superano le 100-150 righe di codice al contrario delle "God class" dove ho una classe sola che "fa tutto", invece il consiglio è di avere il codice dove non supera la schermata vedendo tutto senza dovere scrollare col mouse.

In molti libri di design o clean code questo principio viene sovente descritto come coesione dove come obbiettivo si tende a mantenere alta la coesione (o viceversa basso l'accoppiamento) cioe una classe deve coesistere senza dipendere da altre (il meno possibile). Termini differenti ma il principio è sempre lo stesso classi piu piccole, indipendenti (coesione), possibilmente non legate con le altre (accoppiamento). 
Ciò che accade in una catena di montaggio é esattamente la stessa cosa, si cerca di dare una sola responsabilità alle persone, ognuno ha un compito solo e deve saper fare bene quello proprio perché così facendo si evitano errori; piuttosto si tende a concatenare più persone con responsabilità singola (come una fluent API).

I vantaggi della SRP sono:

* Oggetti piccoli e concisi
* Classi più semplici da testare (Unit testing)
* Aumenta la leggibilità
* Manutenzione più semplice
* Basso accoppiamento (low coupling)

Un esempio molto efficace che spiega del perché della granularità più fine delle classi é quello della differenza tra il Duplo [link] e i lego [link semmann].
I Duplo sono dei pezzi di lego ma molto più grossi adatti a bambini dai 3-5 anni; sono stati pensati appositamente per bambini più piccoli dove la loro forma più grande ed incastri più grossi (Interfacce!) ne facilitano l'uso per i bambini piccoli dove nonstante l'età riescono a costruire qualcosa. I lego invece sono pezzi molto più piccoli (SRP) adatti a bambini più grandi (anche quelli cresciuti come il sottoscritto). La loro granularità più fine rispetto ai Duplo mi permette di creare forme molto più complesse a parità di dimensioni.

Molte persone si chiedono se creare classi più piccole quindi un numero maggiore di oggetti da gestire non crea un "overhead" nello sviluppo del progetto! Dipende molto dal tipo di progetto che si affronta, ovvero se il progetto ha una dimensione ridotta, evoluzione e manutenzione molto bassa nel tempo, allora si é un "overhead"! Se invece il progetto al contrario ha una durata molto lunga, continua evoluzione e non si effettua il refactoring pensando anche alla SRP sovente il progetto acquisisce una complessità dove diventa difficile da mantenere, ad ogni richiesta di Business su nuove funzionalità la nostra risposta diventa:

> é un casino!!

Mai successo? Codice sparso per il progetto invece che nelle loro classi di responsabilità? Codice puplicato che viola il principio DRY[]? 

Seguire l'SRP ci aiuta a ragruppare il codice "sparso" che non sapevamo dove mettere oppure si eliminano tutte quelle classi di Utils difficili da trovare e sovente dupplicati perché non ci si ricorda di averlo già fatto oppure é stato fatto da altre persone del team. Le classi di Utils hanno un grosso svantaggio bisogna ricordarsi dove si trovano si fa affidamento sulla memoria dei developer e questa é una pessima idea.
Quando usiamo un API fare . sul oggetto e trovare immediatamente la funzionalità che stavamo cercando non é più semplice ed immediato? 

Eric Evans nel suo Domain Driven Design (DDD) ci dice esattamente questo ovvero di mettere il Behaviour e la logica all'interno del oggetto stesso!

Concludo l'articolo con una domanda:

preferite giocare con i duplo o i lego?



Una possibile tecnica di riparazione potrebbe essere applicare la [Boy Scout Rule](/post/boy-scout-rule)

Libro dei principi SOLID [Agile Principles, Patterns, and Practices in C#](https://www.amazon.com/Agile-Principles-Patterns-Practices-C/dp/0131857258)



