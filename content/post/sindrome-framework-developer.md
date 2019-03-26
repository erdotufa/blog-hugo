---
title: Sindrome da Framework Developer
subtitle: Se l'unica cosa che hai è un martello tratterai tutto come se fosse un chiodo!
date: 2019-03-25
draft: false
tags: ["Software entropy", "Software design", "Design patterns"]
bigimg: [{src: "/img/miops-trigger-552190-unsplash.jpg", desc: "The golden hammer"}]
---

 Dopo un pò di esperienza noi sviluppatori ci sentiamo come i supereroi, iniziamo qualche lettura di libri su design patterns, clean code, seguire blog, twitter o personaggi famosi conosciuti durante qualche conferenza; dimenticando completamente di avere un proprio cervello da usare, e di un'altra cosa molto importante, ovvero: 
 
 >il contesto in cui ci troviamo ed il nostro tipo di prodotto!!!

Presi dall'entusiasmo iniziamo a pensare a tutto con design patterns ed a sviluppare qualsiasi cosa pensando come se fosse un framework.
Se il progetto é piccolo e tende a restare così, potrebbe essere un buon modo per sperimentare approcci nuovi e trovare nuove strategie di sviluppo.
Su progetti grossi o che tendono a diventare complessi in breve tempo, lavorare in questa modalità potrebbe essere molto pericoloso e creare quello che viene chiamato “Needless Complexity”.

Complicare qualcosa di semplice è sempre possibile, ma cosa succede, se il prodotto deve diventare complesso o dobbiamo aggiungere nuove funzionalità ad una parte dove abbiamo aggiunto complessità inutile?
Diventa ingestibile in poco tempo ed il design molto rigido! Il codice diventa ["Legacy Code"](https://en.wikipedia.org/wiki/Legacy_code) in breve tempo, la famosa [“big ball of mud”](https://en.wikipedia.org/wiki/Big_ball_of_mud).

È molto più semplice, evolvere il design di un'applicazione e trovare la giusta architettura man mano che la complessità aumenta, oppure durante il refactoring, separando il codice, creando layer nuovi ma al momento opportuno; piuttosto che tentare di mettere insieme qualcosa che è diventata complessa e sparsa inutilmente.

Un'altra cosa sovente di questa sindrome la si trova in un'estrema separazione dei concetti, ma poi il numero di riutilizzo delle funzioni non c’è! (attenzione non sto parlando della separazione dei metodi all'interno di un layer per favorire la lettura o ridurre la complessità di un metodo, piuttosto del codice sparso in centinaia di utils o servizi all'interno del progetto).

L'obiettivo principale dei design patterns (lo [Strategy](https://en.wikipedia.org/wiki/Strategy_pattern) ad esempio) è creare un astrazione per favorire il riutilizzo del codice, riducendo le varie duplicazioni, ma se il riutilizzo non c'è, serve veramente scervellarsi inutilmente per un design, tentando di prevedere il futuro, per poi scoprire che questo design è sbagliato perché i requisiti futuri sono completamente diversi da quello che immaginavamo noi developer?

Avete mai guardato il codice del vostro framework/libreria preferito?
È sempre così clean come pensate? Oppure seguono o hanno seguito un’evoluzione?

Non vi è mai capitato di farvi la domanda:

>non capisco perchè in questa libreria non hanno implementato un determinato pattern?

Per poi vederlo apparire un anno dopo perché nel frattempo si é evoluta? 
A me personalmente sì, ed anche più volte!

Il caso più classico forse, è quello di immaginarsi qualcosa di molto complesso in principio, successivamente guardare il codice e pensare: 

>maah tutto qua??? Pensavo fosse molto più complesso di così ed invece...

Se vi riconoscete in questi sintomi (o conoscete qualcuno) significa semplicemente che vi manca l'esperienza e/o la parte ["software craftsmanship"](https://en.wikipedia.org/wiki/Software_craftsmanship).

Da dove iniziare se vi trovate in questa situazione?

Ogni tanto fare uno sforzo maggiore nel non fare le cose sempre nello stesso modo  per abitudine, ma cercare delle soluzioni alternative e migliori!
Attenzione a non esagerare con l'opposto altrimenti vi ritrovate in questa sindrome.

Risorse utili:

* [Principi SOLID](/post/solid-principles)
* Guardare il codice della propria libreria/framework preferito
* [Agile Principles, Patterns, and Practices in C#](https://www.amazon.com/Agile-Principles-Patterns-Practices-PRACTS-ebook/dp/B0051TM4GI/ref=pd_sim_351_6/164-0957370-8645367?_encoding=UTF8&pd_rd_i=B0051TM4GI&pd_rd_r=134300eb-4ff9-11e9-8022-3521c0a11248&pd_rd_w=nmGxL&pd_rd_wg=Y5rKm&pf_rd_p=90485860-83e9-4fd9-b838-b28a9b7fda30&pf_rd_r=54RSWYMDBT3C948FKKTX&psc=1&refRID=54RSWYMDBT3C948FKKTX)
* [The Pragmatic Programmer: From Journeyman to Master](https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master-ebook/dp/B003GCTQAE/ref=sr_1_1?crid=ZLB6UVU0XX93&keywords=pragmatic+programmer&qid=1553626834&s=digital-text&sprefix=pragmatic%2Cdigital-text%2C223&sr=1-1)

Photo by MIOPS Trigger on Unsplash
<a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@miops?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from MIOPS Trigger"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-2px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M10 9V0h12v9H10zm12 5h10v18H0V14h10v9h12v-9z"></path></svg></span><span style="display:inline-block;padding:2px 3px">MIOPS Trigger</span></a>