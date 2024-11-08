<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Campo SQL -->

## Scopo

Il campo SQL fornisce un elenco a discesa di voci ottenute da una query di database. Per utilizzare questo campo, è necessario sapere come costruire una query e si dovrebbe testarla in phpMyAdmin.


## Creazione del Campo

Le opzioni speciali all'interno di questo campo sono:

- **Multiplo** Consente di selezionare valori multipli. Se impostato su *Sì*, la lista visualizza 4 elementi. Altrimenti, visualizza 1 elemento. In entrambi i casi c'è un lungo elenco da scorrere per effettuare le selezioni - se attivato.
- **Query** La query SQL che fornirà i dati per l'elenco a discesa. La query deve restituire due colonne; una chiamata 'value' che conterrà i valori degli elementi dell'elenco; l'altra chiamata 'text' contenente il testo nella lista a discesa.

In questo esempio viene utilizzata una tabella contenente un elenco di nomi di paesi. Questa è la query:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Creazione del Campo SQL](../../../en/images/fields/fields-sql-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo a scopo dimostrativo. Non inserirlo nei tuoi titoli di campo.

## Inserimento Dati

Semplice - seleziona dall'elenco.

![Inserimento dati campo SQL](../../../en/images/fields/fields-sql-data-entry.png)

## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

![Visualizzazione del campo SQL sul sito](../../../en/images/fields/fields-sql-site.png)

L'output è un singolo elemento o un elenco separato da virgole di elementi (nomi dei paesi) che segue l'etichetta del campo (Paese di origine).

*Tradotto da openai.com*

