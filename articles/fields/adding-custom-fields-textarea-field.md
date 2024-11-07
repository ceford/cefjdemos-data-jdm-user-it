<!-- Filename: J3.x:Adding_custom_fields/Textarea_Field / Display title: Campo di Testo -->
## Scopo

Il campo di testo è un'area per l'inserimento di testo su più linee. Una semplice area di testo non ha un editor WYSIWYG.

### Opzioni

Le opzioni speciali all'interno di questo campo sono:

- **Righe** L'altezza dell'area di testo visibile in linee. Se omesso, l'altezza è determinata dal browser. Il valore non limita il numero di linee che possono essere inserite. Le righe sono attive nel backend durante la creazione di un articolo, un contatto o un componente di terze parti che supporta campi personalizzati. Questa opzione non ha alcun impatto sulla dimensione del campo nel frontend.
- **Colonne** La larghezza dell'area di testo visibile in caratteri. Se omesso, la larghezza è determinata dal browser. Il valore non limita il numero di caratteri che possono essere inseriti. Le colonne sono attive nel backend durante la creazione di un articolo, un contatto o un componente di terze parti che supporta campi personalizzati. Questa opzione non ha alcun impatto sulla dimensione del campo nel frontend.
- **Lunghezza Massima** Il numero massimo di caratteri che possono essere inseriti.
- **Filtro** Consente al sistema di salvare determinati tag html o dati grezzi.

## Inserimento Dati

Semplice: inserisci il testo da visualizzare.


## Visualizzazione dei Dati

Lo screenshot del Sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo, mentre il tuo template è responsabile del design del campo.

Cerca l'elemento **Classificazione**.

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei campi")

L'etichetta del campo inizia un singolo blocco di testo a meno che tu non abbia inserito tag HTML come `<p>...</p>`.

