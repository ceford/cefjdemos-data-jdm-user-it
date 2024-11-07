<!-- Filename: J6.x:_Article_Options / Display title: Articolo: Modifica - Opzioni  -->

## Introduzione

La parola *Opzioni* è ambigua in Joomla! A volte è intercambiabile con *Parametri* e la maggior parte delle viste elenco componenti ha un pulsante *Opzioni* nella barra degli strumenti. Questo porta a una pagina Opzioni dove vengono impostati i parametri per il componente nel suo complesso. Inoltre, molte schede di modifica degli elementi del componente hanno una scheda etichettata *Opzioni*, utilizzata per impostare i parametri per quello specifico elemento.

Questo articolo riguarda la scheda *Opzioni* nel modulo *Articolo: Modifica*. È dove vengono impostati i parametri che influenzano l'aspetto generale dell'articolo in fase di modifica. Le opzioni per gli articoli nel loro complesso sono trattate in un articolo separato.

## Schermata

La scheda *Opzioni* del modulo *Articolo: Modifica* presenta una serie di pannelli principalmente con la scelta tra *Utilizza Globale (Nascondi o Mostra)*, *Nascondi* o *Mostra*. La seguente schermata parziale mostra il layout generale.

![Scheda opzioni modifica articolo](../../../en/images/articles/articles-edit-options-tab.png)

## Pannello Layout

Un articolo, o parte di esso, può apparire come una singola pagina o in un layout di blog di categoria controllato da un elemento del menu. In un elemento menu di blog, la maggior parte dei campi del layout ha opzioni *Usa Globale*, *Sì/No* o *Mostra/Nascondi* e *Usa Impostazioni Articolo*. Le opzioni in questo pannello non hanno effetto nei layout di blog a meno che non venga selezionata l'opzione *Usa Impostazioni Articolo* nell'elemento del menu.

Altrimenti, queste opzioni influenzano l'aspetto dell'articolo singolo che si sta modificando.

- **Layout** In una installazione predefinita vengono offerte le prime due scelte:
  - **---Dalle Opzioni Globali--- / Usa Globale** Questo si riferisce alla 
    impostazione *Articoli: Opzioni* disponibile dal pulsante *Opzioni* nella
    barra degli strumenti nella vista elenco *Articoli*. Il suo valore *Scegli un Layout* è impostato
    su *Predefinito*.
  - **---Dal Componente--- / Predefinito** Questo si riferisce all'impostazione negli
    *Articoli: Opzioni*. In un'installazione predefinita è effettivamente
    identico all'opzione *Usa Globale*. Ma se esiste un override denominato default.php, allora quell'override verrà utilizzato per il layout.
  - **---Dal Template cassiopeia--- / nomeoverride** Se è stato creato un override del template
    con un nome diverso da *default* apparirà qui e può essere selezionato come layout alternativo.
- **Titolo** È normale mostrare il titolo di un articolo, ma ci possono essere
  circostanze in cui ciò non è appropriato. Selezionare *Nascondi* per omettere
  il titolo dell'articolo dalla visualizzazione della pagina.
- **Titoli Collegati** Il comportamento predefinito è rendere il titolo di un articolo un collegamento
  all'articolo dove appare in layout di blog o elenco. Questa impostazione è
  controllata dall'elemento del menu. Può essere impostata su *Usa Globale (Sì)*,
  *Usa Impostazioni Articolo*, *No* o *Sì*. Se l'elemento del menu è impostato su
  *Usa Impostazioni Articolo* allora verrà utilizzato il valore *Titoli Collegati* nell'articolo.
  Altrimenti questa impostazione non ha effetto. Se il titolo non è collegato,
  si potrebbe usare un link *Leggi di più* per accedere all'articolo da un layout di blog o elenco.
- **Tag** Mostrare o Nascondere i tag nella pagina del singolo articolo.
- **Testo Introduttivo** Mostrare o Nascondere il testo introduttivo nella pagina del singolo articolo. Ci sono
  alcune circostanze in cui potresti desiderare avere un testo introduttivo completamente diverso per i layout di blog che è omesso nel testo completo dell'articolo.
- **Posizione delle Info Articolo** Questo si riferisce al blocco di informazioni su
  un articolo titolato *Dettagli* e contenente le informazioni di *Autore*, *Categoria*,
  *Pubblicato* e *Visualizzazioni*. L'impostazione predefinita è avere questo sopra il
  testo dell'articolo. Impostare su Sotto per spostarlo sotto il testo dell'articolo in una visualizzazione del singolo
  articolo. Se impostato su *Dividi*, l'elemento *Visualizzazioni* si sposta sotto il
  testo dell'articolo.
- **Titolo Info Articolo** Mostrare o Nascondere la parola *Dettagli* sopra l'elenco
  delle informazioni dell'articolo nella visualizzazione del singolo articolo.

## Pannello Categoria

I campi in questo pannello funzionano come ci si aspetterebbe. Nelle visualizzazioni del blog, le impostazioni del menu item prendono il sopravvento a meno che non siano impostate su *Usa Impostazioni Articolo*.

- **Categoria** Mostra o Nascondi il nome della Categoria.
- **Collega Categoria** Collega (Sì o No) il nome della Categoria. Se impostato su *Sì*, il nome della Categoria è collegato al suo blog di categoria.
- **Categoria Padre** Se impostato su Sì, la categoria padre appare come elemento separato sopra la Categoria nelle informazioni dell'articolo *Dettagli* nel layout di un singolo articolo.
- **Collega Categoria Padre** Se impostato su Sì, il nome della Categoria Padre è collegato alla sua pagina blog di categoria.

## Pannello delle Associazioni

Questo pannello è presente solo nei siti multilingue.

- **Associazioni** Se impostato su Mostra, un elemento extra viene posizionato nelle informazioni dell'articolo con l'inizio *Disponibile anche in:* seguito da bandiere che rappresentano le versioni di questo articolo disponibili in altre lingue.
- **Usa bandiere immagine** Questo elemento appare se *Associazioni* è impostato su *Mostra*. L'impostazione predefinita *Sì* visualizza i pulsanti come bandiere linguistiche. L'alternativa *No* visualizza i pulsanti come codici linguistici, ad esempio *en-GB*. 

## Pannello dell'autore

- **Autore** Mostra o nascondi il nome dell'autore di questo articolo nella visualizzazione di un unico articolo. La riga nelle informazioni dell'articolo recita *Scritto da: NomeAutore*
- **Collegamento alla Pagina di Contatto dell'Autore** Sì o no per collegare il NomeAutore alla pagina di contatto dell'autore, se esiste.

## Pannello delle date

Gli articoli di Joomla memorizzano diverse date. Se visualizzate, ciascuna delle seguenti appare come linee separate nelle informazioni dell'articolo per un singolo articolo. Ricorda che i layout dei blog utilizzano le impostazioni dell'elemento di menu a meno che non sia impostato su
*Usa impostazioni articolo*. Il formato della data è 03 novembre 2024, ma può essere modificato ...[Da fare]

- **Data di creazione** Nascosta per impostazione predefinita.
- **Data di modifica** Nascosta per impostazione predefinita.
- **Data di pubblicazione** Visualizzata per impostazione predefinita.

## Pannello delle opzioni

- **Navigazione** Per un articolo che fa parte di una serie di articoli in una categoria, ci sono i pulsanti *Prec* e *Succ* sotto il testo dell'articolo per navigare verso le pagine precedenti o successive. Se impostato su *Nascondi*, i pulsanti di navigazione non vengono visualizzati nelle pagine del singolo articolo.
- **Visualizzazioni** Il numero totale di volte che l'articolo è stato visualizzato come singolo articolo, mostrato nell'elenco delle informazioni dell'articolo.
- **Link non autorizzati** Questo influisce sui layout dei blog, quindi l'elemento di menu del blog della categoria pertinente deve avere il valore *Opzioni: Link non autorizzati* impostato su *Sì* o *Usa le impostazioni dell'articolo*. Quindi se l'*Accesso* di questo articolo è impostato su *Registrato* e l'impostazione nell'articolo non è *No*, il *Testo introduttivo* dell'articolo verrà mostrato nel layout del blog ma l'etichetta del pulsante Leggi di più sarà *Registrati per leggere di più...*. Facendo clic sul link Leggi di più sarà necessario effettuare l'accesso per visualizzare il contenuto completo dell'articolo.
- **Posizione dei link** Questo si riferisce al posizionamento dei link nella scheda Immagini e Link, Link A, B e C. La posizione predefinita è sopra il testo dell'articolo. Questa opzione consente di posizionare i link sotto il testo dell'articolo o di non visualizzarli affatto.
- **Testo Leggi di più** Il testo normale, *Leggi di più:* seguito dal titolo dell'articolo, è preso dalle chiavi/valori di stringa della lingua. Un'override personalizzato per questo articolo può essere inserito qui, per esempio *Vedi l'articolo completo:* seguito dal titolo dell'articolo.
- **Titolo della pagina del browser** Il titolo della pagina è solitamente il titolo dell'articolo. Se questo è scomodo, è possibile inserire qui un titolo alternativo della pagina da usare nella pagina del singolo articolo. Appare nella scheda del browser e nell'area `<head>...</head>` della pagina. Sarà utilizzato dai motori di ricerca.

