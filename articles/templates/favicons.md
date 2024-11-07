<!-- Filename: J4.x:Favicons / Display title: Favicon -->

## Le Favicon di Joomla!

Le favicon sono le piccole icone che appaiono nella scheda del browser accanto al nome del tuo sito. Vicino alla parte superiore del file template index.php ci sono tre istruzioni per caricare le favicon nella pagina:
```php
    // I browser supportano le favicon SVG
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Per il template Cassiopeia, Joomla cercherà le favicon nelle seguenti posizioni:

1.  **media/templates/site/cassiopeia/images** - non si trovano lì, quindi Joomla cercherà nella posizione successiva.
2.  **media/system/images** - si trovano lì, quindi Joomla le utilizzerà da qui.

Se desideri utilizzare le tue proprie favicon invece delle favicon di Joomla, le carichi nella prima posizione: **media/templates/site/cassiopeia/images**. Puoi farlo utilizzando il modulo Template: Customise. Non saranno influenzate da alcun aggiornamento del template Cassiopeia.

Le favicon sono talvolta usate a dimensioni maggiori e in posti diversi dalla scheda del browser. Ad esempio, questo è uno screenshot di una parte della pagina di avvio di Firefox che mostra alcune delle posizioni preferite dell'utente:

![esempi di favicon dalla pagina di avvio di firefox](../../../en/images/templates/favicons-firefox-start-collection.png)

Tutti i browser moderni supportano le icone SVG, quindi dovresti dare priorità alla creazione di un'icona SVG.

## Informazioni su SVG

SVG è l'acronimo di Scalable Vector Graphics. Un file SVG contiene testo in un formato che definisce le posizioni e le forme delle linee con i colori delle linee, i colori di riempimento e così via. Il seguente screenshot mostra il file *joomla-favicon.svg* aperto in un editor di testo. I numeri di riga sono creati dall'editor di testo e non sono presenti nel file. Le linee lunghe rappresentano curve e qui sono troncate per scopi di visualizzazione.

![contenuto del testo del favicon di joomla](../../../en/images/templates/favicons-joomla-favicon-svg-text.png)

Per creare un file SVG è necessario utilizzare un'applicazione adeguata come Inkscape. Applicazioni grafiche raster come Photoshop o GIMP non sono adatte. Se si preferisce progettare un'icona in un'applicazione grafica raster, o si dispone di un logo grafico raster esistente che può essere adattato per un'icona, è possibile importare il file PNG risultante in Inkscape e tracciarlo per produrre un file SVG. L'immagine tracciata deve essere eliminata dopo il tracciamento!

La creazione effettiva di un favicon SVG è al di fuori del campo di applicazione di questo articolo. La creazione di un file *favicon.ico* standard a partire da un file *joomla-favicon.svg* è molto semplice: molti siti lo offrono online gratuitamente.

## Come Creare Favicons

Se desideri creare i tuoi favicons, il modo migliore per farlo è creare un favicon SVG e poi utilizzare uno strumento online per generare tutti gli altri formati utilizzando quello come input. In questo esempio, è necessario un'icona adatta a un template figlio chiamato Cassiopeia Green. L'icona deve essere quadrata e non troppo elaborata, poiché la dimensione minima di visualizzazione è 16x16 pixel. Alcuni dispositivi necessitano di risoluzioni più alte, come 32x32 o 180x180, e Google raccomanda multipli di 48x48 pixel. Se inizi con un SVG, non devi preoccuparti di nulla di questo - basta creare un'immagine quasi quadrata con un design appropriato. In questo esempio, il favicon sarà le lettere *J4* in verde scuro.

### Inkscape

Inkscape è un'applicazione gratuita, Open Source, multipiattaforma, di grafica vettoriale usata per lavorare con file SVG. Funziona su Linux, Mac e Windows. Vai sul sito di Inkscape (inkscape.org) per scaricare una copia per la tua piattaforma. Le seguenti illustrazioni mostrano la schermata di Inkscape a metà delle istruzioni seguenti.

![inkscape con favicon in preparazione](../../../en/images/templates/favicons-inkscape-favicon.png)

### Creare un SVG

1.  Avvia Inkscape e rendi la finestra di dimensioni confortevoli: seleziona Visualizza / Zoom / Pagina di Zoom
2.  Seleziona lo Strumento Testo, indicato con la lettera A nella Toolbar a sinistra
3.  Seleziona Arial, Normale, 48 e px
4.  Trascina per definire un riquadro in qualsiasi punto della pagina
5.  Digita il testo: J4
6.  Seleziona Visualizza / Selezione Zoom
7.  Seleziona Tracciato / Oggetto a Tracciato - nessun cambiamento visibile ma le parole non sono più testo
8.  Seleziona File / Proprietà del Documento
9.  Seleziona Ridimensiona al Contenuto
10. Zoom indietro per una visione migliore - ma assicurati che tutte le lettere siano ancora selezionate
11. Imposta il riquadro dell'altezza al valore uguale alla larghezza. Scrivilo!
12. Chiudi la finestra di dialogo delle Proprietà del Documento
13. Visualizza / Zoom Pagina di nuovo - i caratteri devono essere centrati
14. Modifica / Seleziona Tutto
15. Oggetti / Allinea e Distribuisci
16. Sposta la selezione come gruppo / Relativo alla Pagina / Centro sull'asse orizzontale - dovresti vedere J4 spostarsi verso il punto centrale verticale
17. Seleziona Riempimento e Tratto a destra - il pannello di destra ha un elenco a discesa indicato con una freccia rivolta verso il basso
18. Nel pannello Riempimento e Tratto, seleziona Riempimento e il primo quadrato riempito
19. Nel pannello RGB inserisci 006400ff nel campo RGBA vicino al fondo a destra - il codice per lo stile CSS *darkgreen*
20. File / Salva
21. Nella finestra di dialogo Salva, inserisci un nome file adatto, per esempio green-favicon-j4.svg
22. Seleziona una posizione adeguata, per esempio *~/Documents/joomla-dev/svgs*
23. Seleziona SVG Ottimizzato (*.svg*) dall'elenco a discesa in fondo al modulo.
24. Seleziona *Salva*
25. Seleziona *OK* per tutti i Predefiniti nel modulo di Output SVG Ottimizzato
26. Chiudi l'SVG su cui stai lavorando - c'è un'opportunità per salvare l'immagine in formato Inkscape ma non è davvero necessario farlo.

### Modificare l'SVG con un Editor di Testo

Avvia il tuo editor di testo preferito per apportare alcune modifiche che non erano possibili in Inkscape.

1.  Apri il tuo file SVG appena creato - nota che la prima riga è una specifica XML
2.  Puoi eliminare la seconda riga - un commento contenente Creato con Inkscape
3.  Se presente, puoi eliminare la riga contenente in quanto non c'è testo
4.  Apri il file originale joomla-favicon.svg - si trova in *joomla_root/media/system/images*
5.  Copia il blocco di stile e incollalo nel tuo SVG sulla riga successiva alla dichiarazione SVG
6.  Chiudi il file originale *joomla-favicon-svg* per evitare modifiche accidentali
7.  Nel blocco di stile del tuo file SVG, cambia path {fill: \#000;} in path {fill: \#006400;}, il valore nella riga
8.  Rimuovi *fill="#006400"* dalla riga
9.  Salva
10. Apri l'immagine nel tuo browser. Per Firefox è File / Apri File...

Dovresti vedere l'immagine nel tuo browser. L'esempio mostra J4 in un quadrato di 47 pixel. La fase successiva è creare gli altri tipi di icone che ti servono usando l'SVG appena creato come master.

### Elaborazione Online

Vai sul sito di Real Favicon Generator. Ci sono altri siti disponibili, ma questo sembra particolarmente completo.

1.  Seleziona il pulsante etichettato *Seleziona la tua immagine Favicon*
2.  Il sito ti mostrerà la tua Immagine Master. Dice anche *La tua immagine non è quadrata (688x512). Possiamo correggere questo aggiungendo margini trasparenti*
3.  Seleziona il pulsante *Continua con questa immagine* sotto l'immagine Master.
4.  Ci sono sottomoduli con sfondo azzurro per diversi tipi di icona - compila ciascuno di essi controllando che l'anteprima sia di tuo gradimento.
5.  È meglio attenersi ai predefiniti delle Opzioni del Generatore di Favicon a meno che tu non sappia di meglio. Eccetto:
6.  Percorso, seleziona l'opzione Non posso... e inserisci: *media/templates/cassiopeia-green/images*
7.  Seleziona il pulsante *Genera i tuoi Favicons e Codice HTML*
8.  Dopo una breve attesa, appare un nuovo modulo, seleziona il pulsante Scarica il tuo pacchetto: pacchetto *Favicon*
9.  Salva il download ...
10. Seleziona e copia il blocco di link da salvare da qualche parte.
11. Chiudi il sito di elaborazione online

Il download è un file *zip* contenente 10 elementi: *favicon.ico*, *safari-pinned-tab.svg*, sei file PNG, *browserconfig.xml* e *site.webmanifest*.

### Implementazione

Per utilizzare il set standard di favicons di Joomla, è necessario rinominare e spostare le icone in *joomla_root/media/templates/yourtemplate/images*:

- La tua immagine SVG master, *green-favicon-j4.svg*, deve essere rinominata in *joomla-favicon.svg*
- Il file *safari-pinned-tab.svg* scaricato deve essere rinominato in *joomla-favicon-pinned.svg*
- Il file *favicon.ico* scaricato deve solo essere spostato

### Il Blocco di Link

Il blocco di link copiato in precedenza contiene:

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Probabilmente non è necessario farne uso!

*Tradotto da openai.com*

