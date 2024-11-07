<!-- Filename: J4.x:Deleting_an_Article / Display title: Articoli: Elimina -->

## Introduzione

In Joomla, l'eliminazione di un articolo è un processo in due fasi. La prima fase lo invia nel *Cestino* da dove può essere ripristinato. La seconda fase lo elimina dal Cestino dopo di che l'articolo viene rimosso in modo permanente.

## Considerazioni

Considera perché vuoi eliminare l'articolo:

- Non è più necessario? In tal caso, la cancellazione è molto probabilmente la giusta linea d'azione.
- È un articolo che potrebbe essere riutilizzato in futuro? Può essere molto frustrante sapere di aver avuto un articolo che sarebbe stato un buon punto di partenza per un altro, ma l'hai eliminato - considera invece di archiviarlo.

## Spostare l'Articolo nel Cestino

- Seleziona **Contenuto -> Articoli** dal menu dell'Amministratore.
- Spunta la casella per selezionare l'articolo che desideri eliminare. Un articolo **deve** essere selezionato per abilitare il pulsante **Azioni** nella barra degli strumenti.
- Seleziona il pulsante **Azioni** nella Barra degli Strumenti.
- Seleziona **Cestino** nel menu a tendina.

![Articolo selezionato per essere cestinato](../../../en/images/articles/articles-selected-to-trash.png)

Apparirà un messaggio di conferma e l'articolo scomparirà dall'elenco corrente degli articoli poiché normalmente non include gli elementi nel cestino.  

## Filtro per Ripristinare o Eliminare

In questa fase del processo l'articolo non è stato completamente rimosso. Questa è una funzionalità utile nel caso in cui tu abbia eliminato l'articolo per errore.

Per vedere l'elenco degli articoli nel cestino:

- Seleziona il pulsante **Opzioni Filtro** per aprire l'elenco dei filtri.
- Seleziona **Cestinati** dall'elenco *-- Seleziona Stato --*.

![Vista cestino degli articoli](../../../en/images/articles/articles-trash-list.png)

### Per Ripristinare

Se hai cambiato idea, puoi selezionare il simbolo **Cestinati** nella colonna *Stato*. L'articolo tornerà allo stato di *Pubblicato* e scomparirà dall'elenco degli articoli nel cestino.

### Per Eliminare

Seleziona la casella di controllo nella colonna sinistra dei dati dell'articolo. Ciò abiliterà i pulsanti *Azioni* e *Elimina* nella Barra degli strumenti. Il pulsante *Azioni* ti permette di applicare la stessa azione a tutti gli articoli selezionati. Se sei realmente sicuro:

1. Seleziona il pulsante *Elimina* nella Barra degli strumenti. Apparirà una finestra di messaggio:<br>
   <div class="alert alert-light">
   Sei sicuro di voler eliminare? Confermando, verranno eliminati definitivamente gli elementi selezionati!</div>
2. Seleziona **OK** per confermare e l'articolo sarà eliminato dal Cestino. L'articolo sarà eliminato dal database. È andato, definitivamente!
3. Seleziona il pulsante **Cancella** accanto a **Opzioni Filtro** per tornare all'elenco non filtrato degli **Articoli**.

## Consigli

- Ricorda, eliminare un articolo non è la stessa cosa che archiviare un articolo. Una volta eliminato dal Cestino, è andato per sempre.
- Se elimini un articolo per errore ma non l'hai eliminato dal Cestino, puoi cambiarne lo stato. Hai la possibilità di impostarlo come *Archiviato*, *Pubblicato* o *Non pubblicato*.
- Joomla non ti permetterà di salvare più di un articolo con lo stesso alias. Se un articolo è eliminato ma lasciato nel Cestino, esiste ancora. Se provi a salvare un articolo e ricevi un errore che indica che l'alias esiste già, potrebbe essere nel Cestino! Pertanto, dovresti svuotarlo dal cestino oppure puoi inserire un alias diverso per il tuo nuovo articolo.
- Joomla conserva le versioni precedenti di un articolo a meno che la funzione Versioni non sia disabilitata. Se stai eliminando un articolo perché in qualche modo si è "rotto", prova a ripristinarlo a una versione precedente.

