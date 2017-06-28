---
title: Boy Scout Rule!
subtitle: Always leave the campground cleaner than you found it.
date: 2017-06-20
tags: ["Clean code", "Software entropy"]
bigimg: [{src: "/img/zach-betten2-40145.jpg", desc: "Boy Scout Rule"}]
---


I boy scout americani hanno una regola/principio, lasciare il campo più in ordine di come lo si ha trovato inizialmente.
Lo stesso principio è stato ripreso dallo ["Zio Bob" Robert C. Martin](https://it.wikipedia.org/wiki/Robert_Cecil_Martin) il quale lo ha applicato al software nel seguente modo:

>**Lasciate il codice più pulito di come lo avete ritrovato!**

Molte volte ci capita di riguardare parti del codice scritto in passato ed innorridire per la sua scarsa qualità! Quante volte vi sarà capitato?

La tendenza del programmatore e di volere riscrivere quella parte il più in fretta possibile per non rivederlo più,
ma riscriverlo potrebbe avere un costo eccessivo, modificare del codice esistente potrebbe introdurre nuovi bug su parti esistenti, 
sopratutto se fatto di fretta. Il management potrebbe non approvare un budget per questa fase perchè per loro il risultato
finale è attualmente funzionante! Loro non vedono questo problema mentre per noi developer diventa un peso, un pensiero fisso (tanto da non dormire più la notte :P)
Ecco che la "Boy Scout Rule" ci viene in soccorso in questo caso.

Questo significa che devo rinunciare all'ossessione di farlo tutto in una volta sola, ma bisogna fare uno sforzo quotidiano con l'obbiettivo di "smantellarlo" progressivamente. 
È sufficiente mettere dei commenti sulle modifiche che si vogliono applicare in futuro, come ad esempio:

```C#
// ToDo : Convertire la sequenza di loop e if in query Linq
// ToDo : Rinominare il metodo in ... 
// ToDO : Rinominare property in ...
```


Se si applica la "Boy Scout Rule" quotidianamente e diventa un principio da seguire a livello di team,
si migliora progressivamente il design, si evita il degrado del software col passare del tempo [(entropia del software)](https://en.wikipedia.org/wiki/Software_entropy) e la nostra mente si libera da questo peso aumentando la nostra produttività!!! Per noi Dev è un fattore psicologico, sapere che lo sistemeremo anche se a lungo termine ci rassicura. 
Sono sufficienti anche piccoli refactoring come il rename dei campi e metodi, oppure splittare un metodo lungo in due più piccoli. 
L'importante non è la quantita di refactoring che si effettua ma mentenere la costanza!


Links

http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule
http://deviq.com/boy-scout-rule

Image <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="http://unsplash.com/@bettenz?utm_campaign=photographer-credit" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Zach Betten"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Zach Betten</span></a>

