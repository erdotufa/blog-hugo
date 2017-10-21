---
title: Liskov substitution
subtitle: La teoria delle finestre rotte.
date: 2017-07-05
draft: true
tags: ["Clean code", "Software entropy", "Refactoring", "SOLID"]
bigimg: [{src: "/img/james-sutton-195612.jpg", desc: "Broken windows"}]
---

La L dei principi SOLID stà per Liskov Substitution Principle (LSP), la sua definizione tradotta in italiano é la seguente:

> Le classi derivate devono sempre poter essere sostituite dalle classi da cui queste derivano (superclassi) in maniera trasparente.


Cosa significa?
Significa avere classi più piccole ognuna con una sola responsabilità! Su molti testi si trova consigliato classi di dimensioni che non superano le 100-150 righe di codice al contrario delle "God class" dove ho una classe sola che "fa tutto", invece il consiglio è di avere il codice dove non supera la schermata vedendo tutto senza dovere scrollare col mouse.


I vantaggi della SRP sono:

* Polimorfismo
* Strategy
* Decorator (interceptor)
* Visitor (double dispatch)
* Plugin
* Publish–subscribe


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

Libro dei principi

https://it.wikipedia.org/wiki/Teoria_delle_finestre_rotte
http://www.unitresorrentina.org/foto/24-forum/85-la-teoria-delle-finestre-rotte


Image <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="http://unsplash.com/@jamessutton_photography?utm_campaign=photographer-credit" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from James Sutton"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">James Sutton</span></a>

