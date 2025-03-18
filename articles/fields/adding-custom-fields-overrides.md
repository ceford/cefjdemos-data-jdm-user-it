<!-- Filename: J3.x:Adding_custom_fields/Overrides / Display title: Sovrascritture del Modello -->

## Visualizzazione Automatica del Campo

Ciascuno dei campi disponibili ha un'opzione etichettata *Visualizzazione Automatica* che può essere impostata su una delle seguenti:

* Dopo il Titolo
* Prima del Contenuto Visualizzato
* Dopo il Contenuto Visualizzato
* Non visualizzare automaticamente

Se si seleziona l'ultima di queste opzioni, il campo non viene visualizzato a meno che non si crei una sovrascrittura del template per gestirne la visualizzazione autonomamente. In alternativa, è possibile aggiungere `{field ID}` in un articolo per posizionare il campo ovunque si desideri. Tuttavia, bisogna ricordarsi di farlo in ogni articolo.

Questo esempio mostra come creare una sovrascrittura del template per un Contatto. I metodi si applicano anche ai componenti di Contenuto e Utente.

## Creare un Template Override

Dal menu Amministratore:

* Seleziona **Sistema / Template del Sito / Dettagli e File di Cassiopeia**
* Seleziona la scheda **Crea Override**.
* Seleziona **com_contact** dal pannello *Componenti*
* Seleziona **Contatto** dall'elenco delle visualizzazioni disponibili. Questo è il layout per un singolo contatto.

Nel pannello **Editor**:
* Seleziona **html / com_contact / contact / default.php**, che è il file
che imposta il layout generale della pagina del singolo contatto.
* Scorri questo file e nota una serie di blocchi `<php if (...) : ?>`.
Ognuno mostrerà o nasconderà una sezione di testo a seconda delle impostazioni del contatto.
* Nota le righe contenenti
```
    <?php echo $this->item->event->afterDisplayTitle; ?> (riga 73)
    <?php echo $this->item->event->beforeDisplayContent; ?> (riga 98)
    <?php echo $this->item->event->afterDisplayContent; ?> (riga 189)
```
Una di queste variabili, o nessuna di esse, è popolata a seconda del valore del
campo Visualizzazione Automatica.

## Utilizzo dei campi nel tuo override

Hai tutti i campi corrispondenti all'elemento corrente accessibili tramite la proprietà `$this->item->jcfields`, che è un array che contiene i seguenti dati per ogni campo (questo esempio è per un campo Editor):

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => article-editor
                [name] => article-editor
                [checked_out] => 0
                [checked_out_time] => 0000-00-00 00:00:00
                [note] =>
                [state] => 1
                [access] => 1
                [created_time] => 2017-04-07 12:08:59
                [created_user_id] => 856
                [ordering] => 0
                [language] => *
                [fieldparams] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [buttons] =>
                                [width] =>
                                [height] =>
                                [filter] =>
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [params] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [hint] =>
                                [render_class] =>
                                [class] =>
                                [showlabel] => 1
                                [disabled] => 0
                                [readonly] => 0
                                [show_on] =>
                                [display] => 2
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [type] => editor
                [default_value] =>
                [context] => com_content.article
                [group_id] => 0
                [label] => article-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Public
                [author_name] => Super User
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Visualizzare il campo

La funzione `FieldsHelper::render()` è utilizzata per visualizzare ciascun campo. Innanzitutto, aggiungi un'istruzione
`use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;` alla lista delle istruzioni `use` nella parte superiore del file di override:

```php
defined('_JEXEC') or die;

use Joomla\CMS\Helper\ContentHelper;
use Joomla\CMS\HTML\HTMLHelper;
use Joomla\CMS\Language\Text;
use Joomla\CMS\Layout\FileLayout;
use Joomla\CMS\Layout\LayoutHelper;
use Joomla\CMS\Plugin\PluginHelper;
use Joomla\CMS\Router\Route;
use Joomla\Component\Contact\Site\Helper\RouteHelper;
use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;
```

Poi, ovunque desideri posizionare i campi nel tuo template, utilizza il seguente codice:
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Oppure per un override grezzo, che non traduce l'etichetta:

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Caricamento di campi individuali

Per aggiungere campi individuali al tuo contenuto, inizia scegliendo nomi specifici per i tuoi campi personalizzati, utilizzando il campo **Nome**, che verrà usato per fare riferimento direttamente al tuo campo nel codice di override. Nella scheda `Opzioni`, seleziona **No** nel campo `Visualizzazione automatica` per impedirne la visualizzazione automatica in una delle posizioni standard.

Quindi, per abilitare l'accesso diretto per nome ai campi personalizzati in un override, posiziona il codice qui sotto all'inizio del tuo file. Dovresti fare questo per ogni file PHP di override su cui desideri posizionare campi personalizzati individuali.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

Infine, dovresti aggiungere il codice di posizionamento del campo nel punto in cui vuoi che l'etichetta o il valore del campo sia mostrato.

Per aggiungere l'**etichetta** del campo al tuo override, inserisci il codice qui sotto, sostituendo `name-of-field` con il nome del campo.

```php
<?php echo $this->item->jcFields['name-of-field']->label; ?>:&nbsp;
```

Per aggiungere il **valore** del campo al tuo override, inserisci il codice qui sotto, sostituendo `name-of-field` con il nome del campo.

```php
<?php echo $this->item->jcFields['name-of-field']->rawvalue; ?>
```

Puoi aggiungere questo codice a qualsiasi parte del tuo override. Esempi: Il contenuto di un div, l'attributo src in un tag `img`, all'interno di un attributo di classe CSS, ecc.
