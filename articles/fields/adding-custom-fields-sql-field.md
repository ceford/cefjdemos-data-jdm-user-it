<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Campo SQL -->

## Scopo

Il campo SQL fornisce un elenco a discesa di voci ottenute da una query del database. Per utilizzare questo campo, devi sapere come costruire una query e dovresti testarla in phpMyAdmin.


## Creazione del Campo

Le opzioni speciali all'interno di questo campo sono:

- **Multiplo** Permetti la selezione di valori multipli. Se impostato su *Sì*, la lista visualizza 4 elementi. Altrimenti visualizza 1 elemento. In entrambi i casi c'è una lunga lista da scorrere per effettuare le selezioni - se attivato.
- **Query** La query SQL che fornirà i dati per la lista a discesa. La query deve restituire due colonne; una chiamata 'value' che conterrà i valori degli elementi della lista; l'altra chiamata 'text' contenente il testo nella lista a discesa.

In questo esempio è utilizzata una tabella contenente una lista di nomi di paesi. Questa è la query:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Campo SQL](../../../en/images/fields/fields-sql.png "Campo SQL")

## Inserimento Dati

Semplice - selezionare dall'elenco.


## Visualizzazione dei Dati

Il seguente screenshot del sito mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

Cerca l'elemento **Paese di Origine**.

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei campi")

L'output è un singolo elemento o un elenco di elementi separati da virgola (nomi di paesi) che segue l'etichetta del campo (Paese di Origine).

*Tradotto da openai.com*

