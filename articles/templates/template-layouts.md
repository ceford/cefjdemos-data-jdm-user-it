<!-- Filename: J4.x:Template_Layouts / Display title: Layout dei Modelli  -->

## Strutture dei File di Layout

In un **template**, ogni estensione che genera output HTML colloca il codice di output in un file di template all'interno della struttura dei file dell'estensione, spesso in una cartella chiamata tmpl. Alcuni esempi:

- /modules/mod_login/tmpl/default.php
- /modules/mod_login/tmpl/default_logout.php
- /components/com_content/tmpl/article/default.php
- /plugins/content/vote/tmpl/vote.php

In un **override del template**, viene creato un file con lo stesso nome all'interno della struttura dei file del template e viene utilizzato al posto del file nella struttura dei file dell'estensione. Esempi corrispondenti:

- /templates/cassiopeia/html/mod_login/default.php
- /templates/cassiopeia/html/mod_login/default_logout.php
- /templates/cassiopeia/html/com_content/article/default.php
- /templates/cassiopeia/html/plg_content_vote/vote.php

Questo ti permette di personalizzare l'output in base alle tue esigenze. Tuttavia, non hai la possibilità di scegliere se utilizzare o meno il tuo override. Viene sempre utilizzato.

In un **layout alternativo del template**, crei un file con un nome diverso dall'originale ma nella stessa cartella del template. Il nuovo nome non deve contenere caratteri di sottolineatura. Crei inoltre qualsiasi file che condivida la prima parte del nome originale. Un esempio:

- /templates/cassiopeia/html/mod_login/expires.php
- /templates/cassiopeia/html/mod_login/expires_logout.php

Diventa quindi possibile scegliere se utilizzare il layout predefinito originale o il layout alternativo. La scelta viene fatta nel modulo o nella forma di modifica del componente (scheda Avanzate per i moduli, scheda Opzioni per gli Articoli). Nota che non tutte le estensioni permettono né gli override né i layout alternativi.

**Attenzione:** i plugin non forniscono un meccanismo per selezionare layout alternativi.

## Layout Alternativi del Modulo

Creare un layout alternativo per un modulo è simile a creare un override del template per un modulo. In entrambi i casi, si crea una cartella chiamata `templates/.../html/`. Ad esempio, la cartella per un override del template o layout alternativo di "mod_login" per il template cassiopeia sarebbe `templates/cassiopeia/html/mod_login/`.

Ci sono due differenze importanti tra un override del template e un layout alternativo. La prima è il nome del file. Per l'override del template si nominerebbe il file `default.php` per corrispondere al nome del file core. Per un layout alternativo, si utilizza un nome diverso. L'unica regola è che **il nome del file non deve contenere alcun trattino basso**.

La seconda importante differenza è che, a differenza dei file di override del template che vengono utilizzati automaticamente ogni volta che il modulo viene visualizzato usando il template con l'override, un file di layout alternativo viene usato solo se lo si seleziona come parametro nelle impostazioni del modulo.

### Un esempio pratico - mod_login

- Vai su **Sistema** → **Template del Sito** → **Dettagli e File di Cassiopeia**
- Seleziona la scheda **Crea Overrides**.
- Dalla lista dei Moduli seleziona l'elemento **mod_login**.
- Nella scheda Editor, seleziona **html** → **mod_login** per vedere le copie appena create dei template di output di mod_login.
- Rinomina **default.php** in qualcos'altro senza un trattino basso, ad esempio **expires.php**.
- Rinomina **default_logout.php** in **expires_logout.php**.

Ora hai due file con esattamente lo stesso contenuto degli originali. Cambia il contenuto di expires_logout.php per aggiungere un messaggio che informa l'utente sull'ora in cui la sessione scadrà dopo ogni caricamento della pagina.

Alla riga 16, immediatamente sotto le istruzioni di uso esistenti, aggiungi quanto segue:

```php
use Joomla\CMS\Factory;

date_default_timezone_set('Europe/London');
$config = Factory::getContainer()->get('config');
$lifetime = $config->get('lifetime', 0);
$time = time() + $lifetime * 60;
$endTime = date('H:i:s', $time); // time() restituisce un tempo in secondi già
```

E alla riga 36, immediatamente dopo la riga contenente un'istruzione endif, aggiungi questo codice:

```html
<p class="text-center">
La tua sessione scadrà alle <br><?php echo $endTime; ?>
</p>
```

Chiudi i file di Cassiopeia. Seleziona **Contenuto** → **Moduli del Sito** e apri il modulo Login. Nella scheda Avanzato, nell'elemento Layout troverai che hai una scelta tra **-- Dal Modulo -- / Default** e **-- Dal Template Cassiopeia -- / expires**.

![modulo login che mostra layout alternativi](../../../en/images/templates/layouts-module-login.png)

Un modo in cui potresti utilizzare questa funzione è avere due moduli di Login, uno con accesso Pubblico e l'altro con accesso Super Utenti. In quest'ultimo seleziona l'opzione **expires** e solo i Super Utenti vedranno il promemoria del tempo di scadenza della sessione.

È importante capire che se specificato nella schermata dei parametri del modulo, un file di layout alternativo per un modulo verrà utilizzato per quel modulo indipendentemente dal template utilizzato per visualizzare la pagina in cui il modulo è mostrato. È pertanto responsabilità dell'amministratore assicurarsi che il file di layout funzioni come desiderato in qualsiasi template in cui questo modulo possa essere mostrato.

### Traduzione

Puoi tradurre il nome del file usando le Sovrascrizioni di Lingua. Prova la seguente procedura:

- Seleziona **Sistema** → **Pannello di Gestione** → **Sovrascrizioni di Lingua**
- Seleziona la tua lingua e la posizione Amministratore.
- Seleziona il pulsante **Nuovo** e compila il modulo. In questo esempio la chiave della lingua è **TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES** e il testo potrebbe essere **Login / Logout con tempo di scadenza**
- Salva e chiudi, poi torna al modulo Login.

![form modifica sovrascrizione lingue](../../../en/images/templates/layouts-language-override-form.png)

Il campo del modulo di selezione del layout con **expires** tradotto:

![modulo layout alternativi selezione](../../../en/images/templates/layouts-example-translated.png)

## Layout alternativi dei componenti

I layout alternativi dei componenti funzionano in modo simile ai layout dei moduli. Un file viene posizionato nella stessa cartella in cui si posizionerebbe un file di override del template. Ad esempio, per creare un layout alternativo per un articolo per il template "cassiopeia", si deve inserire un file nella cartella `templates/cassiopeia/html/com_content/article/`. Come per i layout dei moduli, il file non deve avere lo stesso nome del file core e non deve includere underscore nel nome. Inoltre, non dovrebbe esserci un file XML con lo stesso nome in questa cartella. (Discuteremo i file XML più avanti nella sezione sui Layout alternativi degli elementi di menu).

È possibile impostare un valore globale per i layout dei componenti nella finestra Opzioni del componente. Ad esempio, nella finestra Opzioni dell’Articolo, c'è un parametro *Scegli un Layout* come mostrato di seguito:

![modulo opzioni articoli con elenco di layout alternativi](../../../en/images/templates/layouts-articles-options.png)

Come per i layout dei moduli, i layout dei componenti sono mostrati come opzioni di parametro nella schermata di modifica individuale del componente. Ad esempio, per un articolo, il parametro appare nella scheda Opzioni di Modifica Articoli come mostrato di seguito.

![modulo modifica articoli che mostra l'elenco dei layout alternativi](../../../en/images/templates/layout-article-edit.png)

Come per altri parametri, l'impostazione Usa Globale utilizzerà il valore dall’opzione parametro. L'impostazione Dal predefinito del componente utilizzerà il layout predefinito del componente. I layout alternativi che hai creato per diversi template sono mostrati sotto ciascuna intestazione di template.

I nomi dei file possono essere tradotti. La riga seguente:
```ini
    TPL_CASSIOPEIA_COM_CONTENT_ARTICLE_LAYOUT_MYLAYOUT="Solo Titolo Senza XML"
```
tradurrà un file chiamato "mylayout.php" come "Solo Titolo Senza XML".

È possibile avere più di un file per un layout. Il file iniziale deve essere nominato senza underscore e gli eventuali file aggiuntivi devono avere degli underscore.

I layout alternativi dei componenti possono essere utilizzati con articoli, contatti o feed di notizie.

I layout alternativi dei componenti vengono usati solo quando si verificano due condizioni: (1) sono specificati nei parametri del componente; e (2) non esiste un elemento di menu per questo specifico componente. Ad esempio, se hai uno o più elementi di menu di tipo "Articolo Singolo" impostati per un determinato articolo, il layout alternativo per quell'articolo non verrà utilizzato. Invece, verrà utilizzato il layout specificato nell'elemento di menu. Questo è coerente con il modo generale in cui funzionano i parametri dei componenti, dove il più specifico (in questo caso un elemento di menu per un singolo articolo) sovrascrive il meno specifico (in questo caso, i parametri dell'articolo).

## Layout alternativi delle categorie

I layout alternativi delle categorie funzionano come i layout dei componenti. Le regole per specificare i file di layout sono le stesse. L'unica differenza è che la cartella è quella delle categorie, non quella dei componenti. Ad esempio, un layout alternativo di categoria per cassiopeia andrebbe nella cartella `templates/cassiopeia/html/com_contact/category`.

Puoi impostare i layout delle categorie a livello globale, nella schermata Opzioni di ciascun componente. Di seguito è riportato un esempio tratto da Contatti: Opzioni / Modulo Categoria:

![modulo opzioni componente contatti che mostra layout alternativi](../../../en/images/templates/layouts-contacts-options.png)

I layout alternativi delle categorie appaiono quando aggiungi o modifichi una categoria nel Componente: Modifica Categoria / Formulario Opzioni, come mostrato di seguito.

![modulo opzioni componente contatti che mostra layout alternativi](../../../en/images/templates/layouts-contacts-category-options.png)

I layout alternativi delle categorie possono essere utilizzati per articoli, banner, contatti e feed di notizie.

Come per i layout dei componenti, un layout di categoria verrà utilizzato solo se:

1. è selezionato nei parametri globali o di categoria.
2. non esiste un elemento di menu specifico per la categoria.

Se è stato configurato un elemento di menu per una categoria specifica, verrà utilizzato il layout selezionato nel menu anziché il layout alternativo della categoria.

## Categoria Articolo Blog e Elenco

Per gli articoli, sono disponibili due layout principali di categoria: Blog ed Elenco. Ognuno di questi layout appare nella scheda Categoria del modulo Opzioni Articoli sotto l'intestazione "Dal Componente". Layout alternativi appaiono anche nella lista, permettendo di selezionare i layout di Blog, Elenco o altri template alternativi come layout di categoria predefiniti, sia a livello globale che durante la modifica di una singola categoria di articoli.

![opzioni del modulo componente contatti che mostrano layout alternativi](../../../en/images/templates/layouts-articles-options-category.png)

Questo significa che, come per altre opzioni di layout, puoi controllare se i link delle categorie di articoli utilizzano i layout blog o elenco. È importante comprendere che, come altri parametri di layout, questa opzione avrà effetto solo quando non c'è un elemento di menu a singola categoria per la categoria.

## Elementi di Menu Alternativi

Gli Elementi di Menu Alternativi hanno una differenza importante rispetto agli altri. Per creare un layout alternativo di un elemento di menu, è necessario includere un file XML il cui nome corrisponde al file di layout iniziale. Per esempio, per creare un elemento di menu alternativo chiamato "mioarticolo" per un articolo nel template cassiopeia, dovresti creare due file nella cartella `templates/cassiopeia/html/com_content/article` chiamati `mioarticolo.php` e `mioarticolo.xml`. Se desideri includere più file di layout, aggiungeresti questi file con trattini bassi nei nomi dei file.

Il file XML segue lo stesso formato dei file XML degli Elementi di Menu fondamentali. Questo permette non solo di creare un layout personalizzato per questo elemento di menu, ma consente anche di creare parametri personalizzati. Ad esempio, potresti nascondere alcuni parametri o aggiungere nuovi parametri.

Gli Elementi di Menu Alternativi appaiono quando selezioni un Tipo di Elemento di Menu come mostrato sotto.

![lista di selezione elemento di menu](../../../en/images/templates/layouts-menu-blog-menu-creation.png)

Gli Elementi di Menu Alternativi vengono utilizzati e funzionano allo stesso modo degli elementi di menu standard. Poiché sono già basati su layout personalizzati, le sovrascritture dei template non si applicano agli elementi di menu alternativi.

Come indicato sopra, i layout degli elementi di menu hanno la precedenza sui layout alternativi di componenti o categorie.

La traduzione degli elementi di menu alternativi viene effettuata con i seguenti tag nei file XML. Il formato è `"TPL_"<nome template>_<componente>_<vista>_<nome elemento di menu>_<tipo di tag>`. Ad esempio, queste righe sotto tradurranno il titolo, l'opzione e la descrizione per un elemento di menu alternativo chiamato "catmenuitem".
```
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE="Layout Personalizzato Categoria cassiopeia"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION="cassiopeia Custom"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC="Descrizione per layout personalizzato categoria cassiopeia."
```
Questi stringhe devono essere aggiunti a
`administrator/language/overrides/en-GB.override.ini` ma puoi usare il modulo Language Overrides descritto sopra.

Il file catmenuitem.xml inizierebbe con:

```xml
<?xml version="1.0" encoding="utf-8"?>
<metadata>
   <layout title="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE" option="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION">
      <help
         key = "JHELP_MENUS_MENU_ITEM_ARTICLE_SINGLE_ARTICLE"
      />
      <message>
         <![CDATA[TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC]]>
      </message>
   </layout>
```

## Controllo del Modello per Voci di Menu Alternative

Come discusso sopra, la presenza di un file XML rende un layout alternativo una voce di menu. Il formato del file XML è lo stesso del formato per i file XML delle voci di menu core. Con questo file XML, puoi aggiungere i parametri che desideri includere per questa voce di menu. Possono essere gli stessi di una delle voci di menu core, oppure puoi omettere parametri core o aggiungerne di nuovi. Nota che se aggiungi nuovi parametri, questi possono essere utilizzati nel file di layout ma non saranno usati nei file del modello o della vista core.

È anche possibile sovrascrivere le impostazioni dei parametri per i parametri core. Un esempio di ciò è controllare con quali modelli un layout di voce di menu alternativa può essere visualizzato. In alcuni casi, potresti voler consentire che una voce di menu personalizzata venga visualizzata con qualsiasi modello per il sito. In altri casi, potresti desiderare limitare il layout della voce di menu a un modello specifico. In questa situazione, basterebbe aggiungere il seguente parametro al file XML della voce di menu:

```xml
<fields>
  <field
    name="template_style_id"
    type="templatestyle"
    label="COM_MENUS_ITEM_FIELD_TEMPLATE_LABEL"
    description="COM_MENUS_ITEM_FIELD_TEMPLATE_DESC"
    filter="int"
    template="cassiopeia"
    class="inputbox">
  </field>
</fields>
```

Questo sovrascriverà il parametro core `template_style_id`. Impostare il template uguale a "cassiopeia" in questo caso limiterà l'utente a selezionare solo stili di template per il template "cassiopeia".

## Ulteriori Informazioni

- Elementi
  di Base del Template
- Cartelle e File del Template
  Cassiopeia
- Personalizzazione del Template
  Cassiopeia
- Override del
  Template
- Layout del
  Template
- Template Cassiopeia Semplificato - Uno Studio di Caso -
  un semplice template basato su Cassiopeia

*Tradotto da openai.com*

