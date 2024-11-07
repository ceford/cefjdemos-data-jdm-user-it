<!-- Filename: J3.x:Adding_custom_fields/Editor_Field / Display title: Campo dell'editore -->

## Scopo

Il campo Editor consente l'inserimento dati WYSIWYG per alcuni contenuti correlati all'articolo, in aggiunta al contenuto principale.


## Creazione del Campo

Opzioni speciali all'interno di questo campo sono

- **Pulsanti** Mostra o Nascondi il menu a discesa del contenuto CMS. Per il testo supplementare dell'articolo potrebbe non essere appropriato mostrare alcuni o tutti i pulsanti nella lista. Il valore predefinito del plugin è Nascondi.
- **Nascondi Pulsanti** Se *Pulsanti* è impostato su *Sì* o il valore predefinito del plugin è *Mostra*, nascondi i pulsanti selezionati nel menu a discesa del contenuto CMS.
- **Larghezza e Altezza** i valori includono lo spazio occupato dalla barra degli strumenti dell'editor quindi è probabilmente meglio lasciarli vuoti inizialmente.
- **Larghezza** Il valore della larghezza definisce la larghezza dell'editor WYSIWYG in % o pixel. Il valore predefinito è 100%.
- **Altezza** Il valore per l'altezza definisce l'altezza (in pixel) dell'editor WYSIWYG. Il valore predefinito per questo è 250px. Il valore può essere rappresentato come una frazione dell'altezza del viewport, ad esempio 50vh.
- **Filtro** Consente al sistema di salvare determinati tag html o dati non elaborati.

## Inserimento Dati

Nella scheda di modifica dell'Articolo, il campo Editor supplementare è simile al campo Editor del contenuto principale.

![campo editor](../../../en/images/fields/fields-editor-entry.png "Campo Editor")

## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo, mentre il tuo template è responsabile del design del campo.

Nella visualizzazione dell'articolo, il testo inserito appare sotto il titolo, ma come parte dell'elenco puntato per quell'elemento di campo.

Cerca l'elemento **Note di Coltivazione**.

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei campi")

