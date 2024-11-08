<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Campo Calendario -->

## Scopo

Il campo Calendario fornisce una casella di testo per l'inserimento di una data. Un'icona accanto alla casella di testo attiva un selettore di calendario a comparsa, che può essere utilizzato per scegliere una data da un calendario grafico.

## Creazione del Campo

I parametri comuni dei campi sono descritti in un articolo separato.

* **Titolo** Puoi avere diversi campi di data in un articolo, quindi è necessario prestare attenzione nell'impostare il titolo per evitare ambiguità nell'output.
* **Etichetta** Questo è ciò che viene visualizzato nell'output. Se lasciato vuoto, viene impostato dal contenuto del campo Titolo, ma può essere modificato.
* **Mostra Ora** Se impostato su *Sì*, l'ora viene aggiunta al campo data, al selettore di data e alla data di output. **Attenzione**: Anche se non specifichi l'ora nella data predefinita, l'ora viene visualizzata quando l'opzione *Mostra ora* è attiva.
* **Segnaposto** Questo si trova nella scheda Opzioni. Può essere impostato su un formato data come *AAAA-MM-GG* per ricordare agli utenti il formato richiesto e/o un promemoria per cosa serve la data, ad esempio *Data di arrivo*.

![creazione campo calendario](../../../en/images/fields/fields-calendar-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo per scopi dimostrativi. Omettilo nei titoli dei tuoi campi.

## Inserimento Dati

L'uso del campo Calendario è semplice. Puoi digitare la data nel formato richiesto o selezionare una data utilizzando il selettore di date. È necessaria attenzione nel digitare le date. Un errore nella data viene corretto al salvataggio con una nuova data. Ad esempio, una data del 2024-14-02 viene corretta a 2025-02-02.

Lo screenshot seguente mostra una data di Acquisizione:

![inserimento dati campo calendario](../../../en/images/fields/fields-calendar-data-entry.png)

I campi appaiono in un articolo solo se sono popolati nel modulo di inserimento dati dell'articolo.

## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

![visualizzazione del campo calendario del sito](../../../en/images/fields/fields-calendar-site.png)

I formati di data sono localizzati utilizzando stringhe di lingua.

*Tradotto da openai.com*

