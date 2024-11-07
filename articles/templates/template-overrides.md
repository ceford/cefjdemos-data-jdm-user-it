<!-- Filename: J4.x:Template_Overrides / Display title: Sovrascritture del Modello   -->

## Introduzione

Le estensioni di Joomla definiscono il loro aspetto esteriore con file di template, che contengono markup HTML generato con HTML e PHP, e file CSS che definiscono il layout, lo schema dei colori, i font e così via. Questo potrebbe adattarsi perfettamente alle tue esigenze, specialmente perché puoi modificare l'aspetto con i tuoi stili CSS. A volte desideri mostrare informazioni aggiuntive o forse meno informazioni. Per farlo, hai bisogno di creare un override del template.

Molte delle estensioni di Joomla hanno template di output piuttosto complessi che sono difficili da leggere. È necessario avere una buona comprensione di HTML, PHP e CSS per affrontarne alcune. Pertanto, questo articolo illustra il processo creando un override per il modulo di logout che si trova effettivamente nel modulo di login, mod_login. Il proprietario del sito vorrebbe che il modulo di logout mostrasse l'orario in cui si verificherà il logout automatico dopo un periodo di inattività.   

## Esempio: Sovrascrittura del Template per mod_login

Inizia selezionando **Sistema → Template → Template del Sito** nel menu
dell'Amministratore e poi seleziona l'elemento Cassiopeia Dettagli e File.
Questo aprirà il modulo Template: Personalizza (Cassiopeia):

![personalizza template scheda sito cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

**Importante:** non modificare nessuno dei file forniti come parte del
template Cassiopeia. Al prossimo aggiornamento di Joomla, quei file
potrebbero essere sovrascritti e le tue modifiche andranno perse.

La cartella html è dove si trovano le sovrascritture. Se espandi la cartella
html, vedrai che ci sono già sovrascritture per layout, mod_custom,
mod_menu e tinymce. Espandi ciascuno per vedere cosa contengono.
Al momento non c'è mod_login.

## Creare Override

Seleziona la scheda Crea Override per vedere l'elenco di Moduli, Componenti, Plugin e Layout per i quali puoi creare override:

![scheda override personalizzazione cassiopeia dei modelli](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Seleziona l'elemento mod_login. I file php del template mod_login verranno copiati nella cartella html e verrai riportato alla scheda Editor.
Espandi le cartelle html e mod_login. Vedrai default.php e default_logout.php.

Non desideri il file default.php poiché quello è un override per il modulo di login. Selezionalo e poi il pulsante **Elimina File** nella Barra degli strumenti. Nella finestra di dialogo di avviso, conferma che desideri eliminare il file.

Nota quanto sia facile eliminare i file se cambi idea. E con il pulsante Gestisci Cartelle puoi eliminare anche intere cartelle. Fai attenzione a non eliminare qualcosa che non hai creato tu stesso.

## Modifica default_logout.php

Nella scheda Editor, seleziona il file default_logout.php. Nota i pulsanti in alto a destra: Mostra File Originale e Mostra Differenze. Quest'ultimo è stato impostato su Sì per lo screenshot seguente per mostrare alcune righe di codice aggiunte vicino alla parte superiore del file. Queste righe di codice calcolano quando la sessione utente scadrà dopo il caricamento della pagina contenente il modulo di logout.

![modelli personalizza schede cassiopeia sovrascritture](../../../en/images/templates/cassiopeia-customisation-edit-logout-override.png)

L'area Diff mostra le righe aggiunte con uno sfondo verde e le righe eliminate con uno sfondo rosso. In questo caso non ci sono righe eliminate. Il codice è mostrato qui, nel caso desideri copiarlo per provare tu stesso.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() restituisce già un tempo in secondi
```

Più in basso nel file di override, alla riga 36, sono state aggiunte altre righe per visualizzare il messaggio desiderato:

```html
<p class="text-center">
La tua sessione scadrà alle <br><?php echo $endTime; ?>
</p>
```

Salva e ricarica la pagina del sito contenente il modulo di logout.

![modelli personalizza schede cassiopeia sovrascritture](../../../en/images/templates/cassiopeia-customisation-logout-override-result.png)

Dovresti vedere il modulo di logout cambiare ogni volta che la pagina viene ricaricata. Ma cosa succede se cambi idea? O se hai opzioni diverse per diversi gruppi di Utenti? Benvenuto nei Layout, l'argomento di un articolo separato.

## Altri Override

La scheda Crea Override del modulo Template: Personalizza (Cassiopeia) viene utilizzata per creare qualsiasi elemento dell'output di Joomla per cui è possibile creare override. I nomi delle cartelle degli override iniziano per lo più con com\_, mod\_ o plg\_. Si noti che la seconda parte di una cartella di override del plugin indica il gruppo del plugin. Ecco un esempio di selezione di cartelle di override:

![scheda override personalizza template cassiopeia](../../../en/images/templates/templates-customise-example-override-folder.png)

## Sovrascritture del Layout

I file di layout piccoli sono spesso usati per singoli elementi delle pagine di Joomla! Il pulsante Leggi tutto degli articoli, l'immagine introduttiva e l'immagine completa sono tutti esempi di elementi generati dai propri file di layout. Questi micro-layout si trovano nella cartella /layouts. Ad esempio, nella visualizzazione Blog di Categoria, il file blog_item.php contiene il codice per posizionare il titolo dell'articolo, un'immagine introduttiva, il testo introduttivo e varie altre parti rilevanti della pagina. Lo fa utilizzando una chiamata a LayoutHelper passando il layout da utilizzare come parametro. Questo è un esempio della chiamata per inserire il Titolo dell'Articolo nel layout del blog:

```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

La posizione del file per questo particolare elemento si trova sostituendo i punti con delle barre, anteponendo /layouts/ e aggiungendo .php:

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Quando viene creato un file di override, esso si trova in:

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

## Ulteriori Informazioni

- Nozioni di Base sul Template
- Cartelle e File del Template Cassiopeia
- Personalizzazione del Template Cassiopeia
- Sovrascritture del Template
- Layout del Template
- Cassiopeia Template Semplificato - Uno Studio di Caso - un template semplice basato 
  su Cassiopeia

*Tradotto da openai.com*

