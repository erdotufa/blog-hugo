---
title: I principi SOLID
subtitle: I principi SOLID.
date: 2017-08-05
tags: ["Clean code", "Software entropy", "Refactoring", "SOLID"]
---

Nei progetti informatici il software e la sua qualità degradano con il passare del tempo, si dice che il software marcisce ("Software Rots").
Questo degrado su molti testi di informatica viene descritto come "entropia del software".

A cosa é dovuto? </br>
La maggioranza dei progetti parte da un idea apparentemente "semplice", ed é questa la "fregatura", perché non resta mai così! Solitamente ad inizio attività partiamo sempre tutti con un buon design pensando: stavolta non sbaglio !

Individuiamo qualche design pattern da utilizzare (siamo gasatissimi) ed arriviamo con orgoglio a concludere il progetto, vantandoci magari di essere dei "clean coder" perchè abbiamo curato il design della nostra applicazione ed abbiamo rispettato (piu o meno) tutte le tempistiche ed i requisiti. 

Quindi dove si trova la "trappola"??? 

Non si considera mai che i requisiti cambiano o cambieranno... e cambiano sempre! La cosa peggiore é che cambiano sempre quando si pensa di avere finito e si vorrebbe cambiare attività, ed é forse questo l'effetto più devastante su di noi!

Ma cosa accede veramente?
Ci sono vari scenari possibili, in seguito ne elenco alcuni.

Un possibile scenario potrebbe essere il nostro capo che prima aveva visto il nostro lavoro sempre di sfuggita non dedicandoci mai l'attenzione necessaria e cambia idea dopo averlo visto e provato più attentamente; ovviamente quando pensiamo di avere finito. 
Oppure cambia idea il management che fino a quel momento non aveva mai visto l'applicazione. Oppure arrivano i primi feedback dagli utenti che iniziano ad utilizzare il prodotto chiedendo: 
si potrebbe aggiungere questo? Servirebbe quell'altro, sarebbe utile se si potesse fare anche questa cosa! </br>
Se si tratta di un applicazione interna finiamo per odiare i nostri colleghi, tanto da cambiare direzione se li incrociamo nei corridoi per evitare che ci fanno altre nuove richieste.
Una sola domanda ruota nella nostra mente: perché sempre alla fine???

Cosa possiamo fare per evitare questo problema?

Riprendo un esempio molto divertente dal libro Agile principles e patterns che "Uncle Bob" ce lo descrive cosi: (ovviamente il tutto viene raccontato in modo esagerato ed in alcune parti l'ho modificato rispetto al originale)

## The copy program

La settimana inizia subito con un nuovo progetto, il nostro capo viene da noi e ci chiede di fare un programma che legge i caratteri digitati sulla tastiera e li invia alla stampante.
Avete un po di tempo ed iniziate a pensare a come potrebbe essere il design della nuova applicazione. Poco dopo vi ricordate che dovete partecipare ad un meeting di lunga durata e lasciate la scrivania per andarci. Al pomeriggio ci attente un altro stand-up meeting che si allunga più del dovuto e la prima giornata termina...però siamo soddisfatti perché riusciti ad effetuare il primo step, quello del design. 

Martedì decidiamo di recarci presto in ufficio per evitare distrazioni ed iniziare a lavorare sul nostro programma. Creiamo il progetto e scrivamo le seguenti 10 righe di codice molto soddisfatti.

```C#
public class Copier
{
    public static void Copy()
    {
        int c;
        while((c=Keyboard.Read()) != -1)
            Printer.Write(c);
    }
}
```

Il tempo di fare il primo salvataggio, ricordiamo di essere in ritardo per un importantissimo "quality-meeting" quindi lasciamo l'ufficio un altra volta e nella fretta ci prendiamo anche un caffé per concigliare il sonno durante il meeting.

Mercoledì decidiamo di arrivare ancora presto in ufficio per provare se il nostro programma funziona. Accendiamo il pc, facciamo partire tutte le nostre applicazioni, apriamo il nostro source code editor preferito e carichiamo il progetto. Il tutto compila per la prima volta senza nemmeno un errore, Woow una cosa che non succede spesso. Ma il trionfo dura poco il nostro capo ci chiama per un meeting improvviso non schedulato...

Giovedì passiamo la mattinata nel capire il problema di un cliente tra debugging e log. Finalmente riusciamo a lanciare il nostro programma che funziona al primo tentativo. Hoho esultiamo di nuovo, funziona al primo colpo! Ma improvvisamente veniamo interrotti nuovamente perché, uno stagista ha cancellato il master source code dal server. Ovviamente l'ultimo backup risale a 3 mesi prima e, ci sono 94 backup incrementali da ripristinare.

Venerdì giornata libera e finalmente nonstante la stanchezza settimanale riusciamo a testare il programma e deployarlo in produzione. Un altra volta la nostra reputazione di programmatore d'asso e salva!!

Come si diceva precedentemente i requisiti cambiano sempre!
Qualche mese dopo il nostro capo viene da noi e ci chiede di modificare il nostro programma facendo in modo che le letture vengano effettuate da schede perforate (tecnologia all'avanguardia)invece che dalla tastiera. Ci pensiamo su un attimo e gli rispondiamo che il nostro programma non era stato pensato per essere usato con le schede perforate, modificarlo rovinerebbe l'eleganza del nostro codice che siamo contrari a questa modifica, e lui ribatte che questa modifica e strettamente necessaria perchè gli utenti ne hanno veramente bisogno.

A questo punto parte una lunga riflessione, potrei copiare il codice e creare una nuova funzione molto simile ma violerei il principio DRY e vorrei evitarlo, passare un parametro alla funzione sarebbe una soluzione migliore ma dopo un indagine scopriamo che altri in azienda hanno utilizzato il nostro codice come API per costruire altri programmi quindi modificare l'interfaccia implicherebbe una modifica e ricompilazione e il testing di tutti i prodotti che hanno usato il nostro codice, settimane di lavoro per una modifica anche questa soluzione non sembra percorribile. Ci viene in mente una soluzione mettiamo una booleana globale la ptFlag se impostata la lettura viene effettuata da lettore schede altrimenti dalla tastiera. L'interfaccia non é cambiata l'esistente continua a funzionare e chi vuole utilizzare questa nuova funzionalità basta che imposta la globale ed il gioco e fatto. Riguardo il codice e mi convinco che in fondo la modifica non é cosi invasiva e decido di mantenerla.  


```C#
public class Copier
{
    //remember to reset this flag
    public static bool ptFlag = false;
    public static void Copy()
    {
        int c;
        while((c=(ptFlag ? PaperTape.Read() : Keyboard.Read())) != -1)
            Printer.Write(c);
    }
}
```

Nelle settimane successive il nostro capo si ripresenta nuovamente e ci informa che i nostri clienti hanno la necessità di stampare su schede perforate invece che sulla stampante. Cosi come lo abbiamo modificato la volta precedente di farlo anche stavolta non gli importa del nostro design per portare avanti il business serve anche questa modifica! Ahhhh i clienti se non ci fossero loro a rovinarci i design delle nostre applicazioni sarebbe tutto più semplice.

Stufo di questo progetto metto una seconda booleana e anche questa e fatta.  

```C#
public class Copier
{
    //remember to reset these flags
    public static bool ptFlag = false;
    public static bool punchFlag = false;
    public static void Copy()
    {
        int c;
        while((c=(ptFlag ? PaperTape.Read() : Keyboard.Read())) != -1)
            punchFlag ? PaperTape.Punch(c) : Printer.Write(c);
    }
}

```

Ora se ci fermiamo a riflettere un attimo il nostro software é gia degradato dopo appena 2 modifiche. Cosa succederebbe se arrivasse un altra richiesta di lettura e scrittura da un altro device? Il nostro programma anche se di poche righe di codice inizierebbe ad avere una complessita di condizioni con And e Or difficile da gestire e a questo bisogna aggiungere quella di configurazione iniziale mettere uno a true l'altro a false. Ogni buon programmatore sa che aggiungere delle condizioni come quelle non sono mai una buona soluzione ma con la scusa delle fretta finiamo tutti (o quasi) per farlo.

Ma quindi come si fa a gestire questo tipo di problema?

L'errore lo abbiamo fatto quando é stata inserita la prima booleana. Una booleana inserisce una condizione mentre quello che dobbiamo fare é cercare un astrazione. 
L'esempio riportato di sotto nel libro viene definito come Agile design

```C#
public interface Reader
{
    int Read();
}
public class KeyboardReader : Reader
{
    public int Read() {return Keyboard.Read();}
}
public class Copier
{
    public static Reader reader = new KeyboardReader();
    public static void Copy()
    {
        int c;
        while((c=(reader.Read())) != -1)
            Printer.Write(c);
    }
}
```

Infatti sarebbe bastato introdurre una piccola astrazione, invece che leggere direttamente dalla tastiera si potrebbe passare dal interfaccia Reader. A questo punto il nostro codice non sa se le letture vengono fatte dalla tastiera o dal lettore di schede perforate sa che ci sarà una classe con la responsabilita di leggere e di ritornare un int perché in fondo quello che interessa a noi non é avere informazioni sul tipo di lettore. Con questa soluzione il nostro programma e facilmente estendibile a qualsiasi tipo di lettore, é sufficiente creare una nuova classe che incapsula la funzionalità di lettura di un nuovo device implementando l'interfaccia Reader. Questa soluzione inoltre permette ad altri team di utilizzare il nostro Copier implementando l'interfaccia Reader all'interno del proprio progetto senza dover attendere che questa estensione venga implementata da noi.


Per combattere l'entropia del software, lo stesso autore del libro ovvero "lo zio Bob Martin" ha coniato l'acronimo S.O.L.I.D. mettendo insieme principi già esistenti.
Il SOLID non é un pattern o la soluzione a tutti i problemi del software ma sono dei principi/regole indipendenti dal linguaggio di programmazione che ci aiutano a creare un agile design come quello del esempio precedent.  


L'acronimo SOLID sta per :

* [Single Responsibility Principle (SRP)](/post/single-responsibility)
* [Open-Closed Principle (OCP)](/post/open-closed)
* Liskov Substitution Principle (LSP)
* Interface Segregation Principle (ISP)
* Dependency Inversion Principle (DIP)


Attenzione il SOLID é una delle possibili tecniche per combattere l'entropia del software non é l'unico. Un'altra tecnica ad esempio é il Domain Driven Design(DDD)


