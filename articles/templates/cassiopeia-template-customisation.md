<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Personalizzazione di Cassiopeia -->

## Introduzione

Cassiopeia è il template fornito con Joomla 4. È un eccellente template
**accessibile** e **reattivo** per scopi generali. Può essere personalizzato
tramite le opzioni del template e il file *user.css* da utenti con una minima conoscenza di HTML e CSS.

L'illustrazione seguente mostra l'aspetto di un sito Joomla 4 con
un articolo e alcuni elementi di menu creati.

![Vista articolo singolo di Cassiopeia](../../../en/images/templates/cassiopeia-customisation-article-view.png)

## Modelli: Modifica Stile

Puoi sperimentare l'aspetto del sito aprendo il modulo Modifica Stile. Vai a **Sistema → Modelli → Stili del Modello del Sito** e seleziona il titolo del modello nella colonna Stile, Cassiopeia - Predefinito. La scheda Avanzata contiene le impostazioni che puoi regolare:

![Scheda avanzata modifica stile Cassiopeia](../../../en/images/templates/cassiopeia-customisation-edit-style.png)

Per provare le opzioni, apri una scheda o finestra del browser con l'interfaccia Amministratore e una seconda scheda o finestra con l'interfaccia del Sito e passa avanti e indietro dopo ogni modifica salvata.

### Marchio

- **Sì** il predefinito. La barra del logo Cassiopeia contenente un Logo o Nome del Marchio viene visualizzata con uno sfondo scuro, blu per impostazione predefinita.
- **No** La barra del logo non viene visualizzata. Le opzioni per selezionare un Logo, Titolo e Slogan scompaiono.

L'immagine del marchio predefinita è la parola Cassiopeia come immagine in un file SVG. È quello che viene visualizzato nella prima illustrazione sopra.

Potresti impostare il Marchio su No se desideri fornire il branding in un modulo HTML personalizzato.

### Logo

- **Nessuno** L'immagine del logo Cassiopeia predefinita verrà utilizzata a meno che non sia definito un Titolo.
- **Immagine Logo** Il Logo selezionato apparirà al posto del logo Cassiopeia anche se è definito un Titolo.

### Titolo (alternativo al logo)

- **Il Mio Nome del Marchio** Se presente e non hai selezionato un'immagine Logo, le parole nel campo Titolo appariranno ma sottolineate nella barra superiore blu.

### Slogan

- **Sempre al tuo servizio** Se presente, le parole nel campo dello slogan appariranno in un piccolo carattere sotto l'immagine del logo o il Nome del Marchio.

![Marchio Cassiopeia con slogan](../../../en/images/templates/cassiopeia-customisation-brand-with-tagline.png)

### Schema dei Font

- **Nessuno** il predefinito. Viene utilizzata la famiglia di caratteri specificata nel foglio di stile del modello, il che di solito significa che il sito utilizzerà i caratteri con cui hai familiarità disponibili sul tuo computer.
- **Altri** Verrà utilizzata una famiglia di caratteri presente nella gerarchia della cartella del modello o scaricata dal web. Puoi vedere l'aspetto modificato del testo su una pagina quando ricarichi il sito dopo aver cambiato questa opzione.

### Tema Colore

- **Standard** Un colore di sfondo blu scuro per la barra del Marchio e altre caratteristiche come il pulsante di Login.
- **Alternativo** Un colore di sfondo bordeaux al posto del blu scuro.

![Schema colore alternativo Cassiopeia](../../../en/images/templates/cassiopeia-customisation-alt-color-scheme.png)

### Layout

- **Statico** il predefinito. La larghezza massima è impostata a 1320px. Su schermi più larghi il margine diventa solo più ampio.
- **Fluido** Non c'è una larghezza massima.

La vista su un dispositivo mobile con schermo stretto:

![Vista mobile Cassiopeia](../../../en/images/templates/cassiopeia-customisation-mobile-view.png)

### Intestazione Appiccicosa

- **No** il predefinito. Gli elementi dell'intestazione e il contenuto scorrono verso l'alto fuori dal viewport.
- **Sì** Tranne su schermi stretti, gli elementi dell'intestazione restano fissi in cima al viewport mentre i contenuti scorrono verso l'alto. Questo è evidente solo dove il contenuto della pagina è più alto del viewport.

### Collegamento Indietro in Alto

- **No** il predefinito. Non c'è alcun collegamento Indietro in Alto.
- **Sì** Dove il contenuto è più alto del viewport, in basso a destra della pagina c'è un pulsante contrassegnato da un chevron verso l'alto. Selezionalo per tornare all'inizio della pagina.

![Torna all'inizio Cassiopeia](../../../en/images/templates/cassiopeia-customisation-back-to-top.png)

## Posizioni del Template Cassiopeia

Mentre costruisci un sito con Cassiopeia, diventa davvero utile conoscere le
posizioni che puoi utilizzare per i moduli. Alcune sono descrittive, come *menu* e *bottom-a*, ma non è così ovvio dove si trovano finché non le usi. Questa illustrazione dovrebbe aiutarti:

![Posizioni del template Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Prova quanto segue:

### Sposta il Modulo Menu nella Posizione *menu*

Un sito Joomla 4 appena installato ha un menu nella posizione *sidebar-right*,
come si vede nella prima illustrazione sopra. Per questo tutorial sono stati aggiunti alcuni elementi di menu, uno dei quali è un genitore con due elementi figlio. Per spostare questo menu nella posizione menu, vai su **Contenuti**→**Moduli del Sito** nel menu dell'Amministratore. Nell'elenco ci sono tre moduli, tra cui il Menu Principale. Selezionalo per aprire il modulo di modifica Moduli: Menu.

Nel tab del Modulo, cambia il campo Posizione a Menu \[menu\]. Salva e dai un'occhiata al risultato nella visualizzazione del Sito. Il menu sembra a posto, ma gli elementi figlio non ci sono.

Nel modulo di modifica del menu seleziona il tab Avanzato e scorri verso il basso fino al campo Layout. È un elenco a discesa con quattro opzioni. --Da Modulo-- / Default è selezionato di default. Prova le altre opzioni e visualizza il risultato. (Ricorda di *Salvare* nel modulo di modifica e ricaricare nella vista del Sito). Nessuna delle opzioni --Da Modulo-- mostra gli elementi del menu figlio, ma entrambe le opzioni --Da Template Cassiopeia-- sì.

![Posizioni menu Cassiopeia](../../../en/images/templates/cassiopeia-customisation-menu-position.png)

Quindi che differenza fa **Collapsible**?

- Dropdown Collassabile: Su dispositivi mobili con schermo stretto, il menu
  si riduce a un'icona hamburger fino a quando non viene selezionato. Alla selezione, si espande per mostrare un elenco verticale.
- Dropdown: Il menu appare sempre come un elenco verticale.

### Sposta il Modulo Menu nella Posizione *topbar*

Nel tab Modulo del modulo di modifica, imposta la Posizione su Barra Superiore \[topbar\] e dai un'occhiata al risultato. C'è un problema - il menu è posizionato più a sinistra rispetto a quando era nella posizione menu. Questo perché la posizione menu e la posizione del logo hanno una classe CSS di *grid-child* ma la barra superiore no. Questo può essere risolto con una voce nel file *user.css*, come di seguito. 

## Personalizzare Cassiopeia

E se non ti piacesse il colore di sfondo blu scuro dell'intestazione? Supponiamo che tu preferisca un tema verde scuro. Per risolvere questo problema, è necessaria una piccola conoscenza di CSS. Vai a **Sistema**→**Modelli del Sito**→**Dettagli e File di Cassiopeia** per aprire il modulo Template: Personalizza (Cassiopeia).

L'illustrazione di seguito mostra due gruppi di cartelle. Il primo gruppo consiste delle cartelle e dei file del template che non dovresti modificare, ma ai quali puoi aggiungere. In particolare, puoi aggiungere file HTML di override del template alla cartella *html*. Il secondo gruppo contiene i file multimediali del template che non dovresti modificare. Tuttavia, puoi aggiungere un file *user.css* alla cartella *css* e/o un file *user.js* alla cartella *js*. Questo sarebbe utile se volessi apportare alcune semplici modifiche all'aspetto del sito.

![Modifica file di Cassiopeia](../../../en/images/templates/cassiopeia-customisation-edit-files.png)

Nota che non c'è un file *user.css* presente nella cartella *css*. Questo è un file che crei tu stesso per poter sovrascrivere gli stili già definiti. Se non è presente, crealo ora selezionando la cartella *css* e poi il pulsante *Nuovo*. Nella finestra di dialogo "Nuovo File", seleziona la cartella *css*, altrimenti il nuovo file apparirà nel posto sbagliato. Inserisci user (in minuscolo e senza *.css*) nel campo Nome File e seleziona *.css* dal campo Tipo File. Seleziona il pulsante Crea per creare il file. Se *user.css* è già presente, selezionalo per aprire il modulo di modifica.

### Intestazioni

Come primo semplice esempio, cambia il colore delle intestazioni in verde scuro. Le intestazioni sono tag nel range *h1, h2, h3, h4, h5* e *h6*. Nel file *user.css* inserisci la definizione dello stile:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Salva e ricarica il sito per vedere il risultato. Il titolo della pagina o dell'articolo dovrebbe essere verde scuro. Se non lo è, controlla ciò che hai digitato. La lingua formale per la documentazione di Joomla è l'inglese britannico, quindi colour invece di color come in inglese americano. Ma in CSS deve essere color. La punteggiatura è corretta?

Non è così ovvio che alcuni tag, diversi dalle intestazioni, possano essere stilizzati per sembrare intestazioni. Aggiungi quindi questo:
```css
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Nota qui che il punto (.) iniziale è un selettore di classe, ad esempio Dummy H1 - quindi c'è un punto nel file CSS ma non nel nome della classe.

### Sfondo dell'Intestazione

Nel tab del browser contenente il sito, apri gli Strumenti per Sviluppatori del tuo browser, in questo esempio Firefox, e seleziona il tag dell'intestazione.

![Strumenti per sviluppatori di Cassiopeia](../../../en/images/templates/cassiopeia-customisation-developer-tools.png)

Questo mostra gli stili utilizzati. Lo stile container-header è dove vengono impostati il background-color e il background-image. Devono essere sovrascritti nel file *user.css*. Prova questo:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### Stile *topbar*

Ricorda quel commento riguardo al menu troppo spostato a sinistra nella topbar? Questo accade perché non ha una larghezza massima e margini appropriati impostati. Inserisci questo nel file *user.css* per correggerlo:
```css
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Questo è il tema verde funzionante:

![Tema verde di Cassiopeia](../../../en/images/templates/cassiopeia-customisation-green-theme.png)

### Accessibilità

Nota che deve esserci un contrasto sufficiente tra i colori di sfondo e in primo piano per soddisfare gli standard di accessibilità web. Puoi controllare il tuo contrasto al WebAIM Contrast Checker. Il verde scuro è \#006400.

## Overrides

La scheda Crea Overrides nella form Template: Personalizza (Cassiopeia) mostra l'elenco delle estensioni per le quali puoi creare un override. Nota i diversi simboli: seleziona un simbolo di cartella per mostrare un elenco delle cartelle e dei file che contiene; seleziona un simbolo multi-file per creare immediatamente un override per quella estensione; l'elemento creato scompare dall'elenco - seleziona la scheda Editor e individua l'override creato nella cartella *html*. Potrebbero essere creati più di un file - i file creati vengono copiati dall'estensione originale pronti per essere modificati. Per questo, hai bisogno di conoscere un po' di HTML e PHP!

Questa è la scheda Crea Overrides:

![Cassiopeia crea overrides](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Se stai solo sperimentando e non vuoi davvero un override, puoi *Chiudere* la form di modifica, selezionare il pulsante Gestisci Cartelle nella barra degli strumenti e selezionare il pulsante Elimina nella parte inferiore della form modale Gestisci Cartelle.

Gli overrides riguardano davvero la personalizzazione delle estensioni piuttosto che del template Cassiopeia e questa è un'altra storia.

## Modelli Figlio

Se desideri apportare modifiche più sostanziali all'aspetto del sito, puoi creare un modello figlio. Questo copia solo una piccola selezione di cartelle e file che puoi modificare o a cui puoi aggiungere elementi, ma continua a utilizzare le cartelle e i file del modello genitore. Utilizzando modelli figlio, potresti avere alcune pagine con un colore di tema e altre pagine con un secondo colore di tema. I modelli figlio sono trattati altrove. Questa è un'illustrazione della struttura dei file in un figlio di Cassiopeia:

![File del modello figlio di Cassiopeia](../../../en/images/templates/cassiopeia-customisation-child-template-files.png)

*Tradotto da openai.com*

