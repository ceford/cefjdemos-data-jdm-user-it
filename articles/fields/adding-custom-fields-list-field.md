<!-- Filename: J3.x:Adding_custom_fields/List_Field / Display title: Campo Elenco -->

## Scopo

Il tipo di campo del modulo a elenco fornisce un menu a discesa o una casella di elenco di voci definite dall'utente. Se il campo ha un valore salvato, questo viene selezionato quando la pagina viene caricata per la prima volta. Altrimenti, viene selezionato il valore predefinito (se presente).

## Creazione del Campo

Le opzioni speciali all'interno di questo campo sono:

- **Multiplo** Consente di selezionare valori multipli. Se impostato su *No*, un elemento viene visualizzato nella lista. Se impostato su *Sì*, tre elementi vengono visualizzati. La lista scorre per consentire la selezione di uno o più elementi.
- **Valori dell'elenco** Aggiungi elementi secondo necessità e utilizza l'icona di trascinamento per cambiare il loro ordine. Inizia l'elenco con il Testo impostato su *- Seleziona -* e Valore vuoto. Questo fornisce un predefinito vuoto che risulta nell'assenza di questo elenco dall'Articolo.
- **Classe del Campo** Imposta su *w-auto* per rendere la lista abbastanza larga per il suo elenco di etichette.

![Creazione del campo elenco](../../../en/images/fields/fields-list-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo a scopo dimostrativo. Lasciatelo fuori dai vostri titoli di campo.

## Inserimento dati

Semplice: basta selezionare un elemento dall'elenco o più elementi se *Multiplo* è *Sì*.

![Inserimento dati campo elenco](../../../en/images/fields/fields-list-data-entry.png)


## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

L'output è un singolo elemento o un elenco separato da virgole.

![visualizzazione campo elenco sito](../../../en/images/fields/fields-list-site.png)

*Tradotto da openai.com*

