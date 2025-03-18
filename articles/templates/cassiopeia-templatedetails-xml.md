<!-- Filename: J4.x:Cassiopeia_templateDetails.xml / Display title: Cassiopeia templateDetails.xml  -->

## Posizione e Scopo

Puoi vedere un esempio di file `templateDetails.xml` elencato in **Sistema → Modelli del sito → Dettagli e file di Cassiopeia**. Puoi anche modificarlo lì se hai una buona ragione per farlo. Altrimenti, lascialo così com'è! Ogni modello ha un file di questo tipo e un modello figlio inizialmente consiste in una struttura di file che contiene solo questo file.

Il file `templateDetails.xml` contiene i dati di cui Joomla! ha bisogno per gestire e visualizzare il modello. Ciò include i metadati utilizzati per fornire informazioni sul modello, le posizioni delle cartelle e dei file, le posizioni dei moduli del modello e le opzioni di configurazione selezionabili dall'utente. Il contenuto del file templateDetails.xml varierà da modello a modello.

## Cassiopeia templateDetails.xml

I file in formato XML hanno una struttura ben definita. Un file XML deve avere la sintassi corretta altrimenti non funzionerà!

### Formato XML

La prima riga di ogni `templateDetails.xml` deve iniziare con la definizione del doctype XML.

La riga successiva informa Joomla! che i dati in questo file sono per un'estensione di template per il sito. Tutti i dati del template sono contenuti all'interno dei tag di apertura e chiusura.

```xml
<extension type="template" client="site">
...
</extension>
```

### Dati

La prima sezione dei dati del template di solito definisce le informazioni sul template, ad esempio: nomi, date, informazioni di contatto, copyright, numero di versione e descrizione.

```xml
<extension version="3.1" type="template" client="site">
    <name>cassiopeia</name>
    <version>1.0</version>
    <creationDate>2017-02</creationDate>
    <author>Joomla! Project</author>
    <authorEmail>admin@joomla.org</authorEmail>
    <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
    <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
    <inheritable>1</inheritable>
```

Si noti che un template che può avere template figli ha il valore inheritable impostato a 1. I template figli hanno questo valore impostato a 0. Questi dati sono utilizzati nella lista Template: Templates (Sito) come mostrato di seguito.

![lista template siti](../../../en/images/templates/templates-list.png)

La descrizione contiene una chiave di lingua e non la stringa di testo descrittiva effettiva. La chiave viene sostituita dal testo ottenuto da un file di lingua a tempo di esecuzione. I file di lingua sono definiti nella sezione lingue di `templateDetails.xml`.

![form modifica stile template](../../../en/images/templates/templates-edit-style.png)

### Cartelle e File

Le cartelle e i file per il template Cassiopeia sono memorizzati in due posizioni separate. I file php e correlati sono memorizzati nella cartella site/templates. I file media (css, immagini, js e scss) sono memorizzati nella cartella site/media. Queste posizioni sono definite nel file xml come segue:

```xml
    <files>
        <filename>component.php</filename>
        <filename>error.php</filename>
        <filename>index.php</filename>
        <filename>joomla.asset.json</filename>
        <filename>offline.php</filename>
        <filename>templateDetails.xml</filename>
        <folder>html</folder>
    </files>
    <media destination="templates/site/cassiopeia" folder="media">
        <folder>js</folder>
        <folder>css</folder>
        <folder>scss</folder>
        <folder>images</folder>
    </media>
```

Questo è il modello visto in tutti i template moderni di Joomla 4 e 5. La struttura può essere vista nel modulo Template: Personalizza (Cassiopeia):

![pagina personalizzazione template cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

### Posizioni dei Moduli

Le posizioni dei moduli disponibili sono definite come segue:

```xml
    <positions>
        <position>topbar</position>
        <position>below-top</position>
        <position>menu</position>
        <position>search</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
```

Ogni tag crea una posizione modulo disponibile dalla lista posizione in un modulo di modifica form. Il formato semplice della lista posizione significa che può essere personalizzato facilmente. Ad esempio, per aggiungere una nuova posizione modulo alla lista **in un template figlio**, è sufficiente aggiungere un nuovo tag all'interno del tag con un nome univoco utilizzando tutte lettere minuscole senza spazi. Tieni presente che questo aggiunge solo la posizione ai moduli di modifica form e sono necessari ulteriori sviluppi in altri file template per rendere la nuova posizione visibile nel frontend.

Cassiopeia ha abbastanza posizioni nel template! Se pensi di aver bisogno di una in più, probabilmente ti sbagli. Ricorda che un qualsiasi numero di moduli può essere assegnato a una singola posizione e ordinato in ordine nella pagina lista Moduli. Posizioni disponibili:

![diagramma delle posizioni del template Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Puoi anche vedere le posizioni dei moduli in qualsiasi template: da **Sistema → Template del Sito** seleziona il pulsante Opzioni nella barra degli strumenti. Nel modulo Opzioni imposta il campo Anteprima Posizioni Modulo su Abilitato. Salva e Chiudi. Vai al tuo sito e aggiungi ?tp=1 alla fine di qualsiasi URL (o &tp=1 se c'è già un ? nell'URL). Joomla mostrerà tutte le posizioni del template disponibili, anche quelle che non sono state utilizzate:

![posizioni del template Cassiopeia](../../../en/images/templates/templates-template-positions-by-tp.png)

### Lingue

I file di lingua permettono la traduzione di testo statico nel template. Il file tpl_cassiopeia.ini contiene la chiave per le traduzioni di testo che saranno visualizzate dall'Utente. Il file tpl_cassiopeia.sys.ini contiene la chiave per le traduzioni di testo che saranno viste dall'Amministratore.

```xml
    <languages folder="language">
        <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
        <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
    </languages>
```

I file di lingua per la lingua predefinita inglese GB sono memorizzati in site/language/en-GB/. Altre lingue sarebbero memorizzate similmente in file con il codice ISO di lingua appropriato, ad esempio fr-FR per il francese in Francia o de-DE per il tedesco in Germania (che potrebbe essere diverso dal tedesco svizzero e austriaco).

### Opzioni

Un template può offrire opzioni di visualizzazione che possono essere scelte dall'Amministratore nel modulo Template: Modifica Stile. Ad esempio, la scheda Avanzate del template Cassiopeia consente a un Amministratore di cambiare il Brand, aggiungere un Logo, selezionare uno Schema di Font e altro ancora.

![scheda avanzate del modulo modifica stile template](../../../en/images/templates/templates-edit-style-advanced.png)

Le opzioni del template sono definite all'interno di una struttura che crea campi all'interno di fieldset. Ogni fieldset appare come una scheda nel modulo di modifica. Questa è la struttura che crea la scheda Avanzate vista sopra.

```xml
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>
                ...
            </fieldset>
        </fields>
    </config>
```

Le opzioni individuali sono definite con il tag `<field>`. Ogni `<fieldset>` e ciascun parametro `<field>` all'interno di un `<fieldset>`, richiede un nome univoco definito da un attributo **name**. Questo nome definisce il parametro stesso ed è utilizzato per passare le impostazioni ai file del frontend. Ogni parametro contiene anche un attributo **label** e un attributo **description**. Il testo dell'etichetta appare con il parametro nella schermata delle impostazioni per identificare a cosa è destinata l'impostazione e informazioni più dettagliate possono essere incluse nella descrizione.

Un campo parametro può essere praticamente qualsiasi tipo di input di form con opzioni corrispondenti. Questo è selezionato dall'attributo **type**. Eventuali opzioni necessarie, come le scelte a pulsante radio o select, sono definite nei tag `<option>`. I nomi delle classi CSS possono essere definiti con l'attributo **class** e un valore predefinito può essere definito utilizzando l'attributo **default**.

Di seguito sono riportate le definizioni delle opzioni nel template Cassiopeia predefinito. In questo esempio, tutte le Etichette, Descrizioni e Opzioni utilizzano le definizioni delle stringhe di lingua dai file di lingua definiti nella sezione precedente, così come alcune dal core di Joomla!, in modo che possano essere tradotte in lingue diverse secondo necessità.

```xml
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="logoFile"
                    type="media"
                    default=""
                    label="TPL_CASSIOPEIA_LOGO_LABEL"
                    showon="brand:1"
                />

                <field
                    name="siteTitle"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TITLE"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="siteDescription"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TAGLINE_LABEL"
                    description="TPL_CASSIOPEIA_TAGLINE_DESC"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="useFontScheme"
                    type="groupedlist"
                    label="TPL_CASSIOPEIA_FONT_LABEL"
                    default="0"
                    >
                    <option value="0">JNONE</option>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
                        <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (locale)</option>
                    </group>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
                        <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
                        <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
                    </group>
                </field>

                <field
                    name="noteFontScheme"
                    type="note"
                    description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
                    class="alert alert-warning"
                />

                <field
                    name="colorName"
                    type="filelist"
                    label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
                    default="colors_standard"
                    fileFilter="^custom.+[^min]\.css$"
                    exclude="^colors.+"
                    stripext="true"
                    hide_none="true"
                    hide_default="true"
                    directory="media/templates/site/cassiopeia/css/global/"
                    validate="options"
                    >
                    <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
                    <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
                </field>

                <field
                    name="fluidContainer"
                    type="radio"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    label="TPL_CASSIOPEIA_FLUID_LABEL"
                    >
                    <option value="0">TPL_CASSIOPEIA_STATIC</option>
                    <option value="1">TPL_CASSIOPEIA_FLUID</option>
                </field>

                <field
                    name="stickyHeader"
                    type="radio"
                    label="TPL_CASSIOPEIA_STICKY_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="backTop"
                    type="radio"
                    label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>
            </fieldset>
        </fields>
    </config>
```

In questo esempio, il tag `<fieldset name="advanced">` racchiude tutti i parametri e utilizza l'attributo **name** per creare la scheda *Avanzate* nell'interfaccia. Tutto ciò che è necessario per creare un'altra scheda nell'interfaccia è un altro tag `<fieldset>` con un attributo **name** diverso. Tenendo presente questo, è relativamente semplice creare tutte le schede aggiuntive e i parametri necessari in un template.

Uno degli usi potenziali dei parametri extra è negli override o nei layout per template genitore o figlio.

## Sommario

Questo è il file templateDetails.xml utilizzato da Cassiopeia:

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension type="template" client="site">
    <name>cassiopeia</name>
    <version>1.0</version>
    <creationDate>2017-02</creationDate>
    <author>Progetto Joomla!</author>
    <authorEmail>admin@joomla.org</authorEmail>
    <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
    <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
    <inheritable>1</inheritable>
    <files>
        <filename>component.php</filename>
        <filename>error.php</filename>
        <filename>index.php</filename>
        <filename>joomla.asset.json</filename>
        <filename>offline.php</filename>
        <filename>templateDetails.xml</filename>
        <folder>html</folder>
    </files>
    <media destination="templates/site/cassiopeia" folder="media">
        <folder>js</folder>
        <folder>css</folder>
        <folder>scss</folder>
        <folder>images</folder>
    </media>
    <positions>
        <position>topbar</position>
        <position>sotto-top</position>
        <position>menu</position>
        <position>cerca</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumb</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
    <languages folder="language">
        <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
        <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
    </languages>
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="logoFile"
                    type="media"
                    default=""
                    label="TPL_CASSIOPEIA_LOGO_LABEL"
                    showon="brand:1"
                />

                <field
                    name="siteTitle"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TITLE"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="siteDescription"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TAGLINE_LABEL"
                    description="TPL_CASSIOPEIA_TAGLINE_DESC"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="useFontScheme"
                    type="groupedlist"
                    label="TPL_CASSIOPEIA_FONT_LABEL"
                    default="0"
                    >
                    <option value="0">JNONE</option>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
                        <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (locale)</option>
                    </group>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
                        <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
                        <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
                    </group>
                </field>

                <field
                    name="noteFontScheme"
                    type="note"
                    description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
                    class="alert alert-warning"
                />

                <field
                    name="colorName"
                    type="filelist"
                    label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
                    default="colors_standard"
                    fileFilter="^custom.+[^min]\.css$"
                    exclude="^colors.+"
                    stripext="true"
                    hide_none="true"
                    hide_default="true"
                    directory="media/templates/site/cassiopeia/css/global/"
                    validate="options"
                    >
                    <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
                    <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
                </field>

                <field
                    name="fluidContainer"
                    type="radio"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    label="TPL_CASSIOPEIA_FLUID_LABEL"
                    >
                    <option value="0">TPL_CASSIOPEIA_STATIC</option>
                    <option value="1">TPL_CASSIOPEIA_FLUID</option>
                </field>

                <field
                    name="stickyHeader"
                    type="radio"
                    label="TPL_CASSIOPEIA_STICKY_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>

                <field
                    name="backTop"
                    type="radio"
                    label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">JNO</option>
                    <option value="1">JYES</option>
                </field>
            </fieldset>
        </fields>
    </config>
</extension>
```

*Tradotto da openai.com*
