<!-- Filename: Article_Images_and_Links / Display title: Articolo: Modifica - Immagini e Collegamenti  -->

## Introduzione

Altri articoli hanno descritto come incorporare immagini e collegamenti nel contenuto di un articolo. Questo articolo descrive l'uso della scheda *Immagini e Collegamenti* per aggiungere due tipi di immagine e fino a tre collegamenti da utilizzare in layout standardizzati. In breve:

- L'*Immagine Intro* è utilizzata nei layout di Blog di Categoria o Lista come un assaggio visivo extra del tipo di contenuto da aspettarsi.
- L'*Immagine dell'Articolo Completo* è posizionata in cima all'articolo completo come introduzione visiva al contenuto.
- I collegamenti: Collegamento A, Collegamento B e Collegamento C sono posizionati sopra il testo dell'articolo.

## Screenshot

Per questo articolo, a partire da un'immagine di una rana arboricola verde larga 1024 pixel, sono state create due immagini più piccole, rispettivamente di 128 e 256 pixel di larghezza. Nota: è meglio preparare le immagini nel tuo strumento preferito di elaborazione delle immagini, come *Gimp*. Le immagini di piccola e media dimensione sono state utilizzate per creare i seguenti screenshot.

![Modulo di modifica articolo, scheda immagini e collegamenti](../../../en/images/articles/articles-edit-images-and-links-tab.png)

## Campi del Modulo

### Immagine Introduttiva

- **Immagine Introduttiva** Seleziona un'immagine adeguata da utilizzare nei layout del blog, dove solitamente apparirà sopra il titolo dell'articolo. Questo è opzionale. Se lasciato vuoto, non ci sarà un'immagine introduttiva nel layout del blog.
- **Descrizione dell'Immagine (Testo Alt)** Inserisci una descrizione appropriata dell'immagine per i lettori di schermo. 
- **Immagine Decorativa** Se non c'è nessuna *Descrizione dell'Immagine* e questo pulsante non è selezionato, la pagina non supererà i test di accessibilità. Se questo pulsante è selezionato, verrà inserito un attributo `alt` vuoto. Questo potrebbe permettere alla pagina di superare i test di accessibilità. È probabilmente meglio utilizzare sempre una buona descrizione breve dell'immagine.
- **Classe dell'Immagine** La classe predefinita è *left*, che significa float-left. Ma qualsiasi altro valore di float qui non avrà effetto perché non può essere usato su elementi di griglia o flex.
- **Didascalia dell'Immagine** Le parole inserite qui appariranno come didascalia sotto l'immagine. **Avvertenza:** Non usare le stesse esatte parole sia per il testo alt che per la didascalia. I lettori di schermo annunceranno l'informazione due volte.
    - Il testo alt dovrebbe fornire una descrizione concisa di ciò che è presente nell'immagine.
    - La didascalia dovrebbe solitamente fornire un contesto per riportare l'immagine al contenuto circostante o richiamare l'attenzione su un particolare pezzo di informazione.

### Immagine Articolo Completo

Gli stessi campi dell'immagine introduttiva ma l'immagine è utilizzata in un contesto diverso. Vedi gli screenshot del sito qui sotto.

### Link A

- **Link A** Incolla l'URL completo della pagina di destinazione. Deve essere utilizzato l'URL completo anche se la pagina di destinazione si trova su questo sito.
- **Testo del Link A** Digita il testo che deve essere usato per il link di destinazione.
- **Finestra di Destinazione URL** Scegli una delle opzioni di destinazione:
  - **Usa Globale (Apri nella finestra madre)**
  - **Apri nella finestra madre** Questo è il comportamento preferito perché si può usare il pulsante *Indietro* del browser per tornare alla pagina precedente.
  - **Apri in una nuova finestra** Alcuni utenti preferiscono questo, ma confonde gli utenti mobili poiché non è ovvio che è stata aperta una nuova finestra e non c'è un pulsante *Indietro*.
  - **Apri in popup** Compare una piccola finestra popup. La finestra principale resta disponibile. Ogni clic sul link apre un'altra istanza della finestra popup.
  - **Apri in modale** Si apre un dialogo modale al centro dello schermo che è inattivo finché non si chiude la finestra del dialogo.

### Link B e C

Esattamente gli stessi dati di inserimento del Link A.

## Screenshot del Sito

Lo screenshot qui sotto mostra un layout di blog di categoria con l'*Immagine Introduttiva*. Potrebbe essere stato meglio utilizzare un'immagine panoramica con la stessa altezza ma una larghezza molto maggiore per sfruttare lo spazio bianco vuoto.

![Pagina del blog della categoria Anfibi](../../../en/images/articles/articles-site-amphibians-blog.png)

Lo screenshot qui sotto mostra la pagina di un singolo articolo con l'*Immagine dell'Articolo Completo* e il Link A. L'immagine è stata allineata a destra e la didascalia visibile aggiunge qualcosa a quanto detto nella Descrizione affinché abbia senso per i lettori di schermo.

![Pagina del singolo articolo Rane](../../../en/images/articles/articles-site-amphibians-frogs.png)

*Tradotto da openai.com*

