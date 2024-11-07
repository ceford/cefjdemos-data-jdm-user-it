<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Campo del Calendario -->

## Scopo

Il campo del Calendario fornisce una casella di testo per l'inserimento di una data. Un'icona accanto alla casella di testo richiama un selezionatore di calendario a comparsa, che può essere utilizzato per selezionare una data da un calendario grafico.

## Creazione del Campo

I parametri comuni dei campi sono descritti in un articolo separato.

* **Titolo** È possibile avere diversi campi di data in un articolo, quindi è necessario prestare attenzione nell'impostare il titolo per evitare ambiguità nel risultato.
* **Etichetta** Questo è ciò che viene visualizzato nel risultato. Se lasciato vuoto, viene impostato dal contenuto del campo Titolo, ma può essere modificato.
* **Mostra Ora** Se impostato su *Sì* l'ora viene aggiunta al campo data, al selettore di data e alla data di output. **Attenzione**: Anche se non specifichi l'ora nella data di default, l'ora viene visualizzata quando l'opzione *Mostra ora* è attiva.
* **Segnaposto** Può essere impostato su un formato di data come *AAAA-MM-GG* per ricordare agli utenti il formato richiesto e/o un promemoria di quale sia la finalità della data, come *Data di arrivo*.

## Inserimento Dati

L'uso del campo Calendario è semplice. Puoi digitare la data nel formato richiesto o selezionare una data usando il selettore di date. È necessario fare attenzione quando si digitano le date. Un errore nella data viene corretto al salvataggio in una nuova data. Ad esempio, una data del 2024-14-02 viene corretta al 2025-02-02.

Il seguente screenshot mostra una data di Acquisizione:

![inserimento data di acquisizione](../../../en/images/fields/fields-date-entry.png "Data di Acquisizione")

I campi appaiono in un articolo solo se sono popolati nel modulo di inserimento dati dell'articolo.

## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

Cerca l'elemento **Data di acquisizione**.

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei campi")

I formati di data sono localizzati utilizzando stringhe di lingua.

