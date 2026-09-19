<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "Override dell\u2019elenco delle categorie",
    "description": "Scopri come creare un override del template per migliorare il layout di un elenco di contatti in una categoria ",
    "author": ""
}
-->

## L'elenco dei contatti in una categoria

Il layout predefinito dei contatti in una categoria è controllato da un template nel codice del componente 
com_contacts. Il layout predefinito è simile al seguente:

![comitato culturale che utilizza il layout e lo stile predefiniti](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

Potrebbe essere un'opinione personale, ma per me il layout predefinito dei contatti non è del tutto 
soddisfacente. I miei problemi:

* Le immagini dei ritratti originali erano larghe 500 pixel e risultavano molto dominanti.
* Il nome del contatto non è sufficientemente evidenziato.
* L'elenco puntato dei dati personali non ha un'intestazione e appare isolato.
* Il ruolo della persona non ha un'intestazione.
* I campi dell'indirizzo e del codice postale sono assenti.
* I dati sulla posizione sono incompleti.
* I dati di ciascun contatto sono disposti in una tabella e risultano piuttosto compressi sugli schermi stretti.

Quindi, come posso correggerlo secondo i miei gusti? La mia soluzione consiste nel creare un override del template 
e aggiungere alcuni stili personalizzati. Ecco il risultato:
![comitato aziendale che utilizza una sostituzione del modello e stili personalizzati](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Sostituzione del layout del modello

La cartella com_contact/tmpl/category contiene tre file PHP: default.php,
default_children.php e default_items.php. L'ultimo elemento di questo elenco contiene
il layout della tabella per l'elenco.

I file di sostituzione vengono creati tramite Sistema / Modelli del sito / Dettagli e file
di Cassiopeia / Crea sostituzioni. Selezionare com_contact e quindi category.
La cartella html conterrà quindi com_contact/category con i tre file del modello
menzionati sopra.

### Modifica il file default.php in mydefault.php

Il file `default.php` contiene una riga che specifica quale layout utilizzare per 
ciascun record. Seleziona questo file per modificarlo e **rinominalo** in 
`mydefault.php` (oppure usa qualsiasi prefisso desideri al posto di `my`). Non usare 
un carattere di sottolineatura nel nome del file!

Quando in seguito accederai al modulo Contatti / Categoria / Modifica, il campo Layout
della scheda Opzioni ti consentirà di scegliere tra il layout del componente e il layout
sovrascritto. Sarà simile a questo:

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault

```

### Modifica il file mydefault.php

La riga 20 di `mydefault.php` contiene `$this->subtemplatename = 'items';`.
Modifica `items` in `myitems`, in modo che le righe dalla 18 alla 23 siano le seguenti:

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Modificare il file default_items.php in mydefault_myitems.php

Il file `default_items.php` contiene il layout per ogni contatto. Deve essere
rinominato per mantenere l'opzione di utilizzare il layout originale. La prima
parte del nome è irrilevante. È la parte `myitems`, a cui si fa riferimento nel
file `mydefault.php`, a essere utilizzata per il layout.

### Modificare il file mydefault_myitems.php

La sezione `<table>...</table>` di questo file comprende le righe dalla 85 alla
204. Per la sostituzione del layout, ho sostituito il markup della tabella con il
seguente markup della griglia Bootstrap. Sugli schermi stretti le tre colonne
vengono impilate. Sugli schermi con larghezza superiore a 768 pixel, le colonne
sono affiancate. Il markup modificato ha spostato i campi personalizzati sotto il
nome del contatto.

```
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
                                'alt'   => 'official image of ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <div class="parliament-committee-fields">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
                    <?php echo $item->event->beforeDisplayContent; ?>
                </div>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_POSITION_LABEL'); ?></strong><br>
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
                        <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_ADDRESS_LABEL'); ?></strong><br>
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

## Stile

Le classi di stile Bootstrap possono essere definite nel file `mydefault_myitems.php`.
Ad esempio, `<span class="fs-2">...</span>` viene utilizzato per aumentare la dimensione
del carattere del nome del contatto. È possibile aggiungere altri stili nel file `user.css`, ad esempio
la personalizzazione degli elenchi puntati che compaiono solo all'interno di un tag con
una classe `contactList`.

Ecco gli stili inseriti nel file user.css per ottenere il layout
del Comitato aziendale illustrato sopra.

```
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
div.parliament-committee-fields {
  text-align: left;
  margin-top: 1rem;
}
div.parliament-committee-fields ul.fields-container {
  list-style-type: none;
  padding-left: 0;
}
div.parliament-committee-fields ul.fields-container span.field-label {
  font-weight: 700;
}
```

*Tradotto da openai.com*