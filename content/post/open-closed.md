---
title: Open-Closed
subtitle: Open-Closed.
date: 2017-09-07
tags: ["Clean code", "Software entropy", "Refactoring", "SOLID"]
---

La O dei principi SOLID stà per Open Closed Principle (OCP), la sua definizione tradotta in italiano é la seguente:

> Una qualsiasi entità software (classe, modulo,  funzione, ecc.) dovrebbe avere meccanismi che permettono di estenderne il comportamento senza apportare modifiche al codice preesistente.  Quindi Aperte alle estensioni ma chiuse alle modifiche; da qui il nome Open-Closed.


Questo insieme alla SRP è un'altro principio molto importante. Ma come si fa ad estendere una funzionalità senza modificare il codice esistente?

> It Depends "Socrate"

Ci sono varie tecniche che si possono utilizzare.
Lo strategy pattern ad esempio è una tecnica molto utilizzata per rendere il nostro software estensibile. 
Riprendiamo l'esempio del copy program nella versione agile. rif al articolo intro

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

Viene utilizzata la tecnica dello strategy nella parte di Reading questo mi permette di aggiungere una nuova fonte (device) di lettura (quindi open al estensione) ma la cosa più importante è che non devo modificare la funzione Copy (quindi Closed), l'importante e che mantengo valida l'interfaccia.

Il decorator (interceptor) pattern ad esempio mi permette di decorare una funzionalità esistente senza dovere modificare il codice esiste. Difatti alcune volte siamo obbligati ad usare il decorator quando dobbiamo lavorare su un componente black-box sviluppato da terze parti di cui non si ha accesso al codice e si vuole aggiungere la funzionalità di log.

Un altro pattern utilizzato è il visitor sovente con la tecnica di double-dispatch. Il visitor è una specie di pattern matching dei linguaggi functional; molto simile al decorator come principio mi permette di estendere le funzionalità di un oggetto senza aggiungere direttamente il codice all' oggetto. Un esempio di utilizzo classico del visitor è quando si vuole creare una parte di Reporting di una visualizzazione tabellare dove si ha un oggetto "Cell" al quale posso aggiungere un metodo "Print" che prepara la cella e la formatta correttamente per essere stampata. Questa è la soluzione più semplice quella che ci viene spontanea ma stiamo violando la SRP!
Cosa accade se ora vogliamo esportare in PDF? Aggiungiamo un'altro metodo "ExportPdf"? E se dobbiamo convertire la tabella in JSON? È compito/responsabilità della cella conoscere il comportamento in stampa? Su questo argomento ho sempre discusso molto con altri sviluppatori dove ognuno ha un punto di vista differente. Cosa succede se vogliamo riutilizzare l'oggetto cella in un'altro progetto? Dobbiamo riportare anche tutti i riferimenti di librerie che ho dovuto aggiungere per formattare la cella in JSON! Ecco che il Visitor ci viene in aiuto se vogliamo mantenere la SRP.
Un'altro esempio di implementazione di questo pattern si trova nel codice di Roslyn (link) dove in fase di compilazione e parsing del codice (Visiting) posso aggiungere delle mie regole personali sui vari tipi di nodi che vengono percorsi. Il Team di Roslyn ha deciso di implementare come responsabilità (SRP) la parte di visiting permettendo ad altri di estendere ed aggiungere le proprie regole, cosa che sarebbe impossibile per il Team di implemetare tutti i casi possibili.

Solitamente tutti i meccanismi e/o architetture a plugin sono fatti per rendere il software open-closed.

Un altro meccanismo molto efficace è usare un publish-subscribe che oltre a creare uno slegame tra i componenti mi permette di estendere alcune parti semplicemente aggiungendo un nuovo "Handler". Ad esempio posso creare un LogHandler che intecetta determinati eventi (o tutti) esistenti e li logga senza dover andare a modificare parti di codice esistenti creando un LogService ad esempio ed iniettandolo in tutti i punti dove si vuole loggare quindi modificherei il codice esistente. 
Oggigiorno si sente molto parlare di architettura Microservices. Io dopo una riflessione sono arrivato alla conclusione che in questo tipo di architettura troviamo sia la SRP che la OCP.
Ogni singolo servizio/processo dovrebbe avere una singola responsabilità ed essere indipendente dagli altri (SRP). I vari processi solitamente comunicano tramite un Pub-Sub (Bus), posso estendere i miei processi replicandoli N volte oppure, posso aggiungere un nuovo processo che fa da Log centralizzato esattamente come l'esempio del Handler precedente.

Osservate lo schema seguente

![Monolith application VS Microservices](/img/MonolithVSMicroservices.png)

Trovate un analogia?
