<!-- Filename: J4.x:Home_Page_in_Different_Style / Display title: Pagina Principale in Stile Diverso  -->

## Pagina Iniziale del Sito

Una Pagina Iniziale del sito può essere selezionata da qualsiasi tipo di voce di menu selezionando un'icona grigia nella colonna Home di qualsiasi elenco di voci di menu. Prova a fare una modifica! Visualizza la modifica nel tuo sito in un'altra scheda o finestra del browser. Puoi facilmente tornare indietro. Se desideri una Pagina Iniziale distintiva, potresti scegliere un tipo di voce di menu Articolo Singolo, un tipo di voce di menu Blog di Categoria, un tipo di voce di menu Articoli in Evidenza, o qualcos'altro.

Supponiamo che tu voglia dare alla tua Pagina Iniziale un aspetto distintivo, un po' diverso da tutte le altre pagine del tuo sito. Ci sono molti metodi diversi disponibili per personalizzare l'aspetto di una Pagina Iniziale:

- Tramite moduli assegnati solo alla Pagina Iniziale.
- Tramite stili personalizzati.
- Tramite un Override o Layout del template.
- Tramite un template separato o un template figlio utilizzato solo per la voce di menu della Pagina Iniziale.
- Altro...?

## Esempio: Dati Campione Cassiopeia

I dati campione di Cassiopeia creano una pagina Home utilizzando un tipo di voce di menu **Articoli in Evidenza**. È disposta con l'aspetto mostrato nello screenshot qui sotto (sono state apportate alcune piccole modifiche agli articoli individuali per ottenere uno screenshot migliore qui).

![pagina home usando cassiopeia e dati campione](../../../en/images/templates/templates-home-page-style-cassiopeia-sample-data.png)

Ecco come è stato ottenuto il layout:

### Modulo Immagine

La grande immagine sotto la barra menu si trova in un modulo personalizzato chiamato Immagine assegnato alla posizione banner nel template Cassiopeia.

![modulo personalizzato utilizzato nello stile dei dati campione](../../../en/images/templates/templates-home-page-style-custom-module-image.png)

Nella scheda Assegnazione Menu il modulo è assegnato solo a Home:

![scheda assegnazione menu modulo personalizzato](../../../en/images/templates/templates-home-page-style-custom-module-menu-assignment.png)

L'immagine di sfondo è selezionata nella scheda Opzioni del modulo: Modulo personalizzato nel form di modifica.

Nella scheda Avanzato / campo Layout, viene selezionato l'elemento `banner`. Il layout del banner è un layout del template:

### Layout del Template

Il layout predefinito del modulo in `siteroot/modules/mod_custom/tmpl/default.php` non visualizza il modulo come desiderato. Esiste un layout alternativo in `siteroot/templates/cassiopeia/html/mod_custom/banner.php`. Poiché `banner.php` non è presente nel codice del modulo personalizzato, funziona come un layout che puoi selezionare piuttosto che come un override che viene sempre utilizzato. Nel modulo Immagine puoi selezionare il layout predefinito, Salvare e ricaricare il sito per vedere la differenza. Cambia nuovamente al layout banner e salva per ripristinare il comportamento normale.

Esistono articoli separati su Overrides e Layouts.

### Modulo Newsflash

Sotto la grande immagine ci sono tre piccoli box ognuno con un'immagine e del testo sotto. Sono creati utilizzando un modulo Articoli - Newsflash nella posizione template top-a. Il modulo è impostato per visualizzare 3 elementi. La sua Assegnazione Menu è solo Home. La scheda Avanzato ha Layout impostato su orizzontale e Stile Modulo impostato su noCard.

![modulo newsflash](../../../en/images/templates/templates-home-page-style-newsflash-module-image.png)

Questo conclude la spiegazione di come è stata creata la pagina Home dei dati campione di Cassiopeia.  

## Più Opzioni

Potresti voler fare di più. Uno schema di colori diverso per la pagina iniziale, o un watermark, o un layout personalizzato. Ecco alcune idee:

### Visualizzazione della Pagina

Nei menu: nel modulo Modifica Elemento per il menu Home, seleziona la scheda Visualizzazione della Pagina. Il campo Classe della Pagina è solitamente vuoto. Qualsiasi cosa inserita qui diventa una classe aggiuntiva nell'elemento

della pagina. Ad esempio, inserendo `fancyhome` si ottiene quanto segue nell'output della pagina iniziale per quella singola pagina:
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Puoi quindi creare un file user.css tramite **Sistema**→**Template del Sito**→**Cassiopeia Dettagli e File**. Seleziona il pulsante `Nuovo File` e crea user.css nella cartella css. Quindi inserisci gli stili nel modulo di modifica user.css. Esempio:
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Questo conferirà alla pagina iniziale uno sfondo verde pallido. Usa \#f8f8ff; per uno sfondo blu pallido o \#ffffee per giallo pallido. Puoi fare tutti i tipi di altre cose con il tuo stile fancyhome, ma hai bisogno di una buona conoscenza pratica del css.

### Template Alternativi per la Prima Pagina

Puoi installare template del sito alternativi, ottenuti da fornitori di template terzi. E puoi creare template figlio che si comportano in modo simile. In entrambi i casi puoi scegliere quale template deve essere il predefinito per tutte le pagine e quale deve essere usato solo per la pagina iniziale.

- Seleziona **Sistema→Stili Temi del Sito** nel menu Amministratore.
- Seleziona il template che desideri utilizzare per la pagina iniziale. Deve essere uno di quelli non selezionati come template predefinito.
- Nella scheda Assegnazione Menu, seleziona solo l'elemento del menu Home. Tutto ciò che non è selezionato qui continuerà ad usare il tuo template predefinito.
- Potresti selezionare alcune opzioni nella scheda Avanzate, ma variano con ogni template e non sono trattate qui.

Ci sono altri articoli sulla personalizzazione di Cassiopeia.

*Tradotto da openai.com*

