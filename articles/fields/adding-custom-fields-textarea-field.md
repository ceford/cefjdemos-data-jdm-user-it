<!-- Filename: J3.x:Adding_custom_fields/Textarea_Field / Display title: Campo di Testo -->

## Scopo

Il campo Textarea è un'area per l'inserimento di testo su più linee. Un semplice textarea non dispone di un editor WYSIWYG.

### Opzioni

Le opzioni speciali all'interno di questo campo sono:

- **Righe** L'altezza dell'area di testo visibile in righe. Se omesso, l'altezza è determinata dal browser. Il valore non limita il numero di righe che possono essere inserite. Le righe sono attive nel backend durante la creazione di un articolo, di un contatto o di un componente di terze parti che supporta campi personalizzati. Questa opzione non ha impatto sulle dimensioni del campo nel frontend.
- **Colonne** La larghezza dell'area di testo visibile in caratteri. Se omesso, la larghezza è determinata dal browser. Il valore non limita il numero di caratteri che possono essere inseriti. Le colonne sono attive nel backend durante la creazione di un articolo, di un contatto o di un componente di terze parti che supporta campi personalizzati. Questa opzione non ha impatto sulle dimensioni del campo nel frontend.
- **Lunghezza Massima** Il numero massimo di caratteri che possono essere inseriti.
- **Filtro** Permette al sistema di salvare determinati tag html o dati grezzi.

![creazione del campo textarea](../../../en/images/fields/fields-textarea-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo a scopo dimostrativo. Escludilo nei titoli dei tuoi campi.

## Inserimento Dati

Semplice: inserisci il testo da visualizzare.

![inserimento dati nel campo di testo](../../../en/images/fields/fields-textarea-data-entry.png)

## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

![visualizzazione del campo textarea del sito](../../../en/images/fields/fields-textarea-site.png)

L'etichetta del campo inizia un singolo blocco di testo a meno che non siano stati inseriti tag HTML come `<p>...</p>`.

