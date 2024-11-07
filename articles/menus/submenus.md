<!-- Filename: J4.x:Submenus / Display title: Sottomenu  -->

## Nozioni di base sui menu

In Joomla, tre elementi contribuiscono alla visualizzazione di un menu per l'utente:

- Un Menu è un contenitore per elementi del menu.
- Un Elemento del Menu è un link a una pagina del sito o a una pagina esterna.
- Un Modulo del Menu fornisce un metodo per allocare il menu a una posizione sulla pagina e per controllare aspetti dell'aspetto o del comportamento del menu o della pagina.

I menu semplici consistono in elenchi di link. A volte, i membri di un elenco hanno relazioni genitore-figlio visualizzate come figli rientrati o elenchi a discesa. Le relazioni genitore-figlio possono essere nidificate a qualsiasi livello. Tuttavia, nidificare oltre due livelli può rendere gli elenchi poco attraenti e scomodi da usare.

Ci sono occasioni in cui potresti voler mostrare i figli di un menu genitore come un sottomenu separato. Un caso d'uso comune è mostrare un sottomenu a sinistra di una pagina, il contenuto della pagina al centro e un sommario della pagina a destra. Questo tutorial spiega come farlo.

### Dati di esempio

Supponiamo che tu abbia una serie di articoli sugli animali. Potrebbero essere animali domestici, un foglio informativo veterinario o uno zoo. Il seguente è un breve esempio di struttura a scopo dimostrativo:

    Animali
        Gatti
            Burmese
            Blu di Russia
        Cani
            Collie
            Pomerania

Gli elenchi potrebbero essere piuttosto lunghi, quindi potresti voler mostrare solo un elenco di razze di gatti su pagine sui gatti e solo un elenco di razze di cani su pagine sui cani. La seguente schermata mostra il layout obiettivo che l'utente vorrebbe raggiungere:

![obiettivi dei sottomenu animali gatti](../../../en/images/menus/submenus-objectives-animals-cats.png)

In questo esempio, quando l'utente seleziona l'elemento del menu Animali, si carica la pagina Animali e il modulo del menu Gatti scompare (anche il modulo Cani non appare). Seleziona l'elemento del menu Gatti e il modulo del menu Gatti appare accanto alla pagina Gatti. Seleziona l'elemento del menu Burmese e appare la pagina Burmese. Seleziona l'elemento del menu Cani e il modulo del menu Gatti viene sostituito da un modulo del menu Cani accanto alla pagina Cani.

Per provare questo tutorial da solo, dovrai creare alcuni articoli, un menu con elementi del menu e tre moduli del menu.

## Creare Articoli

Se sei molto efficiente, puoi creare un articolo e poi creare un elemento di menu dall'articolo. Per fare ciò, prima dovresti creare un nuovo menu e prendere alcuni passaggi extra durante la creazione dell'articolo. Quindi è meglio mantenerlo semplice all'inizio e iniziare con i tuoi nuovi articoli:

- Seleziona **Contenuti** → **Articoli** → **+** dal menu dell'amministratore.
  Oppure seleziona il pulsante `Nuovo` dall'elenco degli articoli.
- Compila il modulo come faresti per qualsiasi articolo.
- Seleziona il pulsante `Salva & Nuovo` al posto di `Salva & Chiudi` per passare al prossimo nuovo articolo.

I dati di esempio mostrati sopra richiedono sette articoli.

## Creare un Nuovo Menu

Dal menu Amministratore:

- Seleziona **Menu** → **Gestisci**.
- Nella pagina dell'elenco dei Menu, seleziona il pulsante `Nuovo` per creare un nuovo menu.
- Nel modulo Menù: Aggiungi, dai al menu un titolo: Animali e un nome univoco: animali.
- In alcuni casi potresti avere bisogno di ricordarti a cosa serve questo menu. Quindi compila il campo di descrizione.
- Salva o Salva & Chiudi.

![nuovo menu sottomenu](../../../en/images/menus/submenus-new-menu.png)

## Creare Elementi di Menu

Ci sono sette elementi di menu da creare.

### Elemento di Menu Animali

I nuovi elementi di menu saranno collocati nel menu Animali.

- Seleziona **Menu **→** Animali **→** +** dal menu dell'Amministratore.
- Compila il modulo Menu: Modifica Elemento.
  - Titolo: Animali
  - Tipo di Elemento di Menu: Articolo Singolo
  - Seleziona Articolo: Animali - questo è l'articolo principale usato per
    introdurre la serie sugli Animali
  - Menu: Animali
  - Genitore: - Nessun Genitore - questa è la radice del menu
- Seleziona **Salva & Nuovo** dal menu a tendina `Salva & Chiudi`.

### Elemento di Menu Gatti

Questo è molto simile all'elemento di menu Animali. Tranne che:

- Il titolo dovrebbe essere Gatti.
- L'articolo selezionato nel campo Seleziona Articolo dovrebbe essere `Gatti`.
- L'Elemento Genitore dovrebbe essere impostato su `Animali`.

### Elemento di Menu Burmese

Ripeti di nuovo. Tranne che:

- Il titolo dovrebbe essere Burmese.
- L'articolo selezionato nel campo Seleziona Articolo dovrebbe essere `Burmese`.
- L'Elemento Genitore dovrebbe essere impostato su `Gatti`.

### Altri Elementi di Menu

Continua fino a quando non avrai sette elementi di menu, uno per ogni articolo.

## Elenco degli Elementi del Menu

Quando hai creato tutti i tuoi elementi del menu, verifica che abbiano le relazioni parent-child corrette e che siano nell'ordine giusto. Puoi ordinare nella colonna Ordinamento (la seconda colonna) e utilizzare le maniglie di trascinamento (ellissi verticali) per spostare gli elementi nell'ordine corretto. Se un elemento ha un genitore sbagliato, seleziona semplicemente il titolo dell'elemento e cambia il genitore nel modulo Menu: Modifica Elemento.

![lista degli elementi del menu dei sottomenu](../../../en/images/menus/submenus-menu-items-list.png)

## Moduli del Menu

A questo punto hai un menu, ma non ha un modulo da assegnare a una posizione sulla pagina. Potresti usare l'intero menu come un menu standard o a tendina. Tuttavia, lo scopo di questo tutorial è dimostrare come creare sottomenu. Per fare ciò, hai bisogno di tre moduli diversi:

- Un modulo Animali per un sottomenu con voci di menu su Animali, Gatti e Cani.
- Un modulo Gatti per un sottomenu con voci di menu sulle razze di gatti.
- Un modulo Cani per un sottomenu con voci di menu sulle razze di cani.

## Modulo Sottomenu Animali

Dal menu Amministratore:

- Seleziona **Contenuto** → **Moduli del Sito** → **+** oppure seleziona `Nuovo` dalla lista
  Moduli (Sito).
- Seleziona il modulo **Menu**.
- Nel modulo di modifica Menu inserisci i seguenti dati:
  - Titolo: Animali
  - Seleziona Menu: Animali
  - Elemento Base: Animali (questo è l'elemento padre del menu)
  - Livello Inizio: 1
  - Livello Fine: 2 (questo limita gli elementi ai menu di Gatti e
    Cani)
  - Posizione: barra laterale-sinistra (o dove preferisci)

![modulo sottomenu animali](../../../en/images/menus/submenus-animals-module.png)

### Assegnazione Menu Animali

I sottomenu vengono generalmente visualizzati solo sulle pagine dove sono rilevanti, in
questo caso solo su tre pagine. Dalla scheda Assegnazione Menu:

- Imposta il campo Assegnazione Modulo su `Solo sulle pagine selezionate`. Questo
  rivela un elenco gerarchico di tutti gli elementi in tutti i menu.
- Seleziona le caselle corrispondenti a Animali, Gatti e Cani.
- Seleziona le caselle corrispondenti alle razze di gatti e cani. Altrimenti il
  sottomenu Animali sparirà dalle pagine sulle razze.
- Assicurati che nessun'altra casella sia selezionata.
- Salva e Chiudi

![assegnazione menu modulo sottomenu animali](../../../en/images/menus/submenus-animals-module-menu-assignment.png)

## Modulo Sottomenu Gatti

Questo è molto simile:

- Seleziona **Contenuto**→**Moduli del Sito**→**+** o seleziona `Nuovo` dall'elenco
  Moduli (Sito).
- Seleziona il modulo **Menu**.
- Nel modulo di modifica Moduli: Menu inserisci i seguenti dati:
  - Titolo: Gatti
  - Seleziona Menu: Animali
  - Voce Base: Gatti (questa è la voce di menu principale)
  - Livello Iniziale: 3
  - Livello Finale: Tutti
  - Posizione: sidebar-left (o dove preferisci)

### Assegnazione Menu Gatti

Dall'Assegnazione Menu

- Imposta il campo Assegnazione Modulo su `Solo sulle pagine selezionate`. Questo
  rivela un elenco gerarchico di tutte le voci in tutti i menu.
- Seleziona le caselle per Gatti, Burmese e Blu di Russia. Assicurati che nessun'altra
  casella sia selezionata.
- Salva e Chiudi

## Modulo Sottomenu Cani

Più dello stesso ...  

## Alias Voce di Menu

Finora tutto bene! Ma non c'è nessun collegamento alla pagina Animali dal Menu Principale o da qualsiasi altro menu del sito. Il modo più semplice per risolvere questo è con un Alias Voce di Menu. In questo esempio, viene effettuata un'entrata nel menu in cima alla pagina, intitolato Menu Blog Principale. Dal menu Amministratore:

- Seleziona **Menu **→** Menu Blog Principale** (o qualunque sia il tuo menu del sito preferito).
- Seleziona il pulsante `Nuovo` dalla Barra degli Strumenti.
- Compila il modulo Modifica Voce Menu
  - Titolo: Animali
  - Alias: creature - c'è già una voce di menu chiamata Animali, quindi devi usare un alias diverso.
  - Tipo di Voce di Menu: Alias Voce di Menu
  - Voce di Menu: Animali - selezionato dall'elenco delle voci di menu esistenti.

![alias sottomenu animali](../../../en/images/menus/submenus-animals-alias.png)

- Salva
- Ordinamento - dopo il salvataggio, l'ordine può essere modificato. In questo esempio è posizionata per prima.

## Controlla il Risultato

Visualizza le pagine nel tuo sito. In questo esempio, la maggior parte delle pagine non mostrerà i sottomenu nella posizione a sinistra. Il link Animali nel menu in alto aprirà la pagina degli animali da cui è possibile navigare verso le pagine dei Gatti o dei Cani:

![sottomenu obiettivi animali cani](../../../en/images/menus/submenus-objectives-animals-dogs.png)

