---
title: Ereditarietà VS Composizione
subtitle: Inheritance VS Compositioning
date: 2018-06-14
tags: ["Clean code", "Software design", "Dependency Inversion"]
#bigimg: [{src: "/img/zach-betten2-40145.jpg", desc: "Boy Scout Rule"}]
---


Una domanda che affligge la nostra mente da developer da molti anni è questa:

>Devo ereditare o comporre?

Ho sempre visto molta confusione su questo argomento tra programmatori io stesso mi ero trovato in questa situazione.

>Perché accade ciò?

Provo a dare una spiegazione in base alla mia personale esperienza. Quando si passa da semplici "smanettoni" di codice a una programmazione più "seria" si inizia a leggere libri di Clean Code, seguire blog di tizio e caio, andare alle conferenze,
eccetera. Si finisce sempre in esempi dove viene fatto vedere che l'ereditarietà (sto parlando di linguaggi dove la multi ereditarietà non è permessa) crea complessità, trasformarlo in composizione semplifica il nostro design e favorisce il riutilizzo del codice; si conclude che la composizione è molto meglio dell'ereditarietà.

Yahoooo pensate ho trovato finalmente un "Silver Bullet"a questo problema!
Il primo pensiero che vi passa per la testa è devo fare refactoring di tutto ma spesso questo non è possibile (per fortuna), allora il secondo pensiero diventa nella prossima attività di sviluppo farò così!!!

Inizia un nuovo ciclo di sviluppo ed entusiasti si parte a fare tutto a composizione, ma, ad un certo punto ci si accorge che qualcosa non va, sembra che bisogna forzare il design e ci si accorge che il nostro sistema a lego non si "incastra" come pensavamo! Mai capitato?
Se anche voi avete avuto questa sensazione significa che avete sbagliato pensiero esattamente come me!!!

>Cosa è successo?? 

Semplice abbiamo sbagliato astrazione!
Ci sono situazioni in cui l'ereditarietà e più corretta in altre la composizione.

>E quindi come ne veniamo fuori?

Esiste una soluzione molto semplice (che probabilmente già conosci ma sul momento quanto sei davanti al problema non ti viene in mente) basta farsi la domanda il mio oggetto È un/una, oppure Ha quindi e composto (Is A, Has A) durante la modellazione.
Se pensiamo al classico esempio da libro, dove abbiamo la classe Gatto che eredita da Animale, per capire quale è più corretto usare basta chiedersi: 
il gatto è un animale oppure il gatto ha un animale? Ecco che immediatamente si intuisce che uno dei due non ha nessun senso.
Ma questo è un caso semplice direte, ci sono situazioni dove non è così ovvio!
In situazioni dove non si riesce a dare la risposta immediatamente un altro modo è chiedersi: 

>La mia classe o componente software Foo avrebbe modo di esistere da sola?
La posso utilizzare in modo indipendente? Ha una sua forte identità?
Se si allora è più favorevole alla composizione,  altrimenti è un astrazione! 

Riprendendo l'esempio della classe Animale si capisce immediatamente che non può essere usata come classe indipendente perché non esiste concettualmente ma è solo un’astrazione quindi l'ereditarietà e quella più corretta come soluzione!

Se invece si pensa alla classe Logger questa ha una propria identità quella di scrivere il Log ed è indipendente, quindi ha senso che venga utilizzata in composizione per essere iniettata in altri servizi/classi.
Un esempio semplice per capire il principio di composizione è pensare ad un’automobile. L'automobile è una composizione di diverse parti meccaniche tra cui motore, telaio, carrozzeria, ruote ecc., ed ognuna di queste parti può essere rimpiazzata da altre; ad esempio la stessa identica auto può essere costruita con un motore di cilindrata maggiore, lo stesso per le ruote (importante è che viene mantenuto lo stesso interfacciamento), ed allo stesso tempo le varie parti possono comporre anche altre auto di marche o modelli o altri veicoli completamente differenti. Questo principio è conosciuto come Dependendcy Inversion.

Esistono situazioni invece dove la mia classe utilizza tutti e due i metodi ovvero eredita determinate funzionalità e viene composta da altre,
un esempio classico (ma che nessuno ci pensa perché troppo ovvio) è quella del Controller di un API web, dove eredito dalla classe base ApiController ad esempio
e mi faccio iniettare i servizi come quello del Logger dal Dependency Resolver (o Dependency Injection Container).

La mia conclusione è che nel software non esiste il giusto o sbagliato, ci sono soluzioni che funzionano meglio di altre e che ci semplificano il lavoro e la manutenzione. Una soluzione può essere giusta oggi e sbagliata domani, lo stesso Eric Evans (inventore del DDD) diceva che non esiste un modello esatto, tutto si evolve e si evolve in modo imprevedibile perchè il business è in continua evoluzione.
Il nostro lavoro è trovare la migliore modellazione che soddisfi le nostre esigenze.
Partite dai miei consigli che vi saranno sicuramente utili ed esperimentate!
