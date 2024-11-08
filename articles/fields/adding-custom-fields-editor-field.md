<!-- Filename: J3.x:Adding_custom_fields/Editor_Field / Display title: Campo dell'editor -->

## Scopo

Il campo Editor consente l'immissione di dati WYSIWYG per alcuni contenuti correlati agli articoli in aggiunta al contenuto principale.


## Creazione del Campo

Le opzioni speciali all'interno di questo campo sono

- **Buttons** Mostra o Nascondi il menu a tendina dei Contenuti CMS. Per il testo supplementare degli articoli, potrebbe non essere appropriato mostrare alcuni o tutti i pulsanti nella lista. Il plugin predefinito è Nascondi.
- **Nascondi Pulsanti** Se *Buttons* è impostato su *Sì* o il plugin predefinito è *Mostra*, nascondi i pulsanti selezionati nel menu a tendina dei Contenuti CMS.
- **Larghezza e Altezza** i valori includono lo spazio occupato dalla barra degli strumenti dell'editor, quindi probabilmente è meglio lasciarli vuoti inizialmente.
- **Larghezza** Il valore per la larghezza definisce la larghezza dell'editor WYSIWYG in % o pixel. Il valore predefinito è 100%.
- **Altezza** Il valore per l'altezza definisce l'altezza (in pixel) dell'editor WYSIWYG. Il valore predefinito per questo è 250px. Il valore può essere rappresentato come una frazione dell'altezza della finestra, ad esempio 50vh.
- **Filtro** Permetti al sistema di salvare determinati tag html o dati grezzi.

![Creazione del campo dell'editor](../../../en/images/fields/fields-editor-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo a scopo dimostrativo. Evita di includerlo nei titoli dei tuoi campi.

## Inserimento Dati

Nel modulo di modifica dell'Articolo, il campo Editor supplementare è simile al campo Editor del contenuto principale.

![inserimento dati campo editor](../../../en/images/fields/fields-editor-data-entry.png)


## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

Nella visualizzazione dell'articolo, il testo inserito appare sotto il titolo ma fa parte dell'elenco puntato per quell'elemento del campo.

Cerca l'elemento **Note di Coltivazione**.

![visualizzazione del campo editor sul sito](../../../en/images/fields/fields-editor-site.png)

*Tradotto da openai.com*

