---
title: Metodi imbuto
subtitle: Faccio tutto io!
date: 2018-06-21
tags: ["Clean code", "Software entropy","Refactoring"]
bigimg: [{src: "/img/xiang-hu-322627-unsplash.jpg", desc: "The funnel"}]
---

Un problema ricorrente nello sviluppo sono le concatenazioni delle operazioni dove si finisce frequentemente nello stesso punto/metodo/funzione!

Solitamente accade questo:

si scrive una funzione e si inizia a riutilizzarla nei vari punti del progetto, man mano che la riutilizziamo si inizia ad aggiungere parametri, condizioni, 
codice nuovo che serve ad 8 dei 10 punti dove viene utilizzata ma nei 2 casi dove non serve passiamo booleane (con valori di default) per gestire queste eccezioni.

La nostra funzione diventa qualcosa di ingestibile in poco tempo ed il nostro codice perde estensibilità, 
aumenta la sua rigidità e la possibilità di introdurre nuovi bugs, quindi, diminuisce la nostra produzione!

Ho avuto più volte dibattiti e discussioni con amici e colleghi su questo argomento, alcuni sostengono che ci deve essere un punto
unico dove convogliare tutta la funzionalità. Io non sono molto d'accordo con questa filosofia. 
Ci può essere un punto solo dove gestire/aggiungere una funzionalità solo se questa non invalida lo scopo del metodo ovvero la sua responsabilità [(SRP)](/post/single-responsibility), molte volte le condizioni che aggiungiamo (IF) lo fanno!

La cosa più importante è, avere layer/moduli ben organizzati dove ritroviamo facilmente queste "pseudo" duplicazioni e si possono rivedere e refactorizzare più facilmente essendo isolate, piuttosto che avere un metodo imbuto ingestibile, oppure, logiche simili sparse in giro per il progetto!

Una tecnica molto apprezzata e quella del [fluent interface](https://martinfowler.com/bliki/FluentInterface.html) (attenzione non è il [builder pattern](https://en.wikipedia.org/wiki/Builder_pattern)), dove si creano tante piccole funzionalità
e si concatenano insieme per crearne altre più complesse, un po' come in una catena di montaggio dove ogni punto ha una singola responsabilità. 
Con questa tecnica se voglio escludere una parte di codice, invece di aggiungere una condizione (IF) che mi esclude quella parte, creo una variante dove quel blocco non esiste nella mia catena. 

L'immagine della catena di montaggio è la più efficace per capire questa tecnica, dove posso sempre facilmente riorganizzare la mia pipeline, spostare prima o dopo le varie operazioni, aggiungerne di nuove facilmente, crearne altre parallele simili ed efficaci! Anche con questa tecnica è sempre importante mantenere le varie concatenazioni in un layer separato.

**La mia conclusione è che ci troviamo sempre in queste condizioni (capita ancora anche a me) per la fretta di aggiungere nuove funzionalità
e scarso refactoring; quando questo sintomo diventa molto frequente, si entra nell'effetto [Broken Window](/post/broken-windows) e nemmeno la [Boyscout Rule](/post/boy-scout-rule) ci aiuta più!**

Photo by Xiang Hu on Unsplash
<a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@iamthewind?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Xiang Hu"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px">Xiang Hu</span></a>