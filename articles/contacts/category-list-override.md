<!-- Filename: category-list-override.md / Display title: Elenco delle Categorie Sovrascritte  -->

## Voce di Menu "Elenca Contatti in una Categoria"

Può essere un'opinione personale, ma per me il layout predefinito dell'elenco delle categorie di Contatti non è del tutto soddisfacente. I miei problemi:

* Le foto dei contatti sono troppo grandi, poco meno di 500 pixel di larghezza.
* Il nome del contatto non è sufficientemente enfatizzato.
* L'elenco puntato dei dettagli personali non ha un'intestazione e sembra isolato.
* La posizione non ha un'intestazione, quindi può sembrare isolata.
* I campi dell'indirizzo e del codice postale sono assenti.
* I dati sulla posizione sono incompleti.
* La dichiarazione personale è mancante.
* L'elenco è disposto in una tabella che si adatta un po' meglio su schermi stretti ma è piuttosto affollato.

Allora, come risolverlo a mio piacimento?

## Stile

L'immagine ha lo stile CSS `contact-thumbnail img-thumbnail`. Gli Strumenti
per Sviluppatori del browser indicano che img-thumbnail è impostato su `max-width: 100%;`
ma contact-thumbnail non viene utilizzato. L'unica occorrenza di questo stile
in tutto il sito si trova in questa posizione, quindi sembra sicuro impostare un override in
user.css per limitare la larghezza dell'immagine. E la dimensione del font del nome di contatto può essere
aumentata utilizzando il tag `a` racchiudente:

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
```
L'elenco puntato dei campi personalizzati può essere migliorato rimuovendo i punti e
la spaziatura selezionando solo gli elenchi puntati che appaiono all'interno di un tag che ha una
classe di contactList:
```
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```
![business committee stilizzato](../../../en/images/contacts/contact-business-committee-styled.png)

Questo è tutto ciò che si può fare con lo stile. Meglio, ma ancora non abbastanza.
Per aggiungere più elementi e modificare il layout sarà necessario un override del layout.

## Sovrascrittura del Layout del Template

La cartella com_contact/tmpl/category contiene tre file PHP: default.php, default_children.php e default_items.php. L'ultimo della lista contiene il layout della tabella per l'elenco.

I file di sovrascrittura vengono creati tramite Sistema / Template Sito / Cassiopeia Dettagli e File / Crea Sovrascritture. Seleziona com_contact e poi category. La cartella html contiene quindi com_contact/category con i tre file del template menzionati sopra. Il default_items.php è quello da selezionare per l'editing. Le righe da 83 a 203 contengono la tabella utilizzata per il layout.

Potrebbe non essere ovvio, ma $this->items è un array di membri della categoria e ogni membro contiene effettivamente tutti i dati di ciascun elemento, non solo quelli menzionati nelle impostazioni del menu.

Il seguente è un sostituto per la sezione `<table>...</table>` del file default_items.php utilizzando una griglia Bootstrap. Su schermi stretti le tre colonne sono impilate. Su schermi più larghi di 768 pixel le colonne sono affiancate. Ulteriori spiegazioni seguono il codice.

```php
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'immagine ufficiale di ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong>Posizione</strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong>Indirizzo</strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```

### Spiegazione

L'elenco di contatti potrebbe contenere elementi che non sono pubblicati, o che hanno date di inizio e fine non attuali. Devono essere esclusi dalla visualizzazione e serve un conteggio separato per mantenere l'alternanza dei colori di sfondo in ogni riga.

Il tag img è reso come:
```html
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg"
alt="immagine ufficiale di Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
La classe `<span class="fs-2">...</span>` imposta il nome del contatto a dimensione font 2, che sarebbe la stessa di Heading 2.

L'elemento `show_suburb_headings` viene utilizzato come proxy per mostrare l'intero indirizzo poiché alcuni degli elementi indirizzo singoli non hanno selettori Mostra/Nascondi nell'elemento del menu.

### Stile Extra

La versione a griglia dell'elenco contatti necessita di uno stile aggiuntivo in user.css:
```css
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}

a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}

#contactList ul {
  list-style-type: none;
  padding-left: 0;
}

.cat-list-row0 {
  background-color: #efefef;
}

.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
```

### Risultato

![gridded business committee](../../../en/images/contacts/contact-business-committee-grid.png)

*Tradotto da openai.com*

