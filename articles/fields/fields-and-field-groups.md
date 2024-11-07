<!-- Filename: J4.x:Fields_and_Field_Groups / Display title: Campi e Gruppi di Campi -->

## Introduzione

I campi sono usati per visualizzare attributi aggiuntivi di Articoli, Contatti o Utenti. I dati vengono inseriti in un modulo di modifica dell'amministratore e visualizzati nel sito. Un esempio:

Supponiamo che tu scriva articoli su aspetti della natura, a volte fiori, a volte animali. Un campo che potresti voler registrare e visualizzare per entrambi è il Nome Latino, che richiede un campo di testo. Un altro potrebbe essere l'Habitat: Bosco, Stagno, Prato, e così via, che richiede un elenco a discesa. Per i fiori potresti voler registrare la Stagione di Fioritura utilizzando 4 caselle di controllo, una per ogni stagione, o 12 caselle di controllo, una per ogni mese.

I campi vuoti nel modulo di input non vengono visualizzati nell'output del sito, quindi potresti mantenere tutti i campi in un lungo elenco. Tuttavia, solitamente è meglio utilizzare categorie per i tuoi Articoli, diciamo Fiori e Animali. I campi possono essere assegnati a più di una categoria. Quindi i campi Nome Latino e Habitat verrebbero assegnati a entrambi, ma la Stagione di Fioritura verrebbe assegnata solo alla categoria dei Fiori.

Se un campo non è assegnato a un gruppo, apparirà nel modulo di modifica sotto una scheda Campi. Se un campo è assegnato a un gruppo, apparirà in una scheda con quel nome. Quindi per il gruppo dei Fiori sembra appropriato creare un gruppo di campi chiamato Dati sui Fiori (o semplicemente Fiori, anche se usare lo stesso nome per cose diverse può creare confusione). E per gli altri campi comuni potresti usare un gruppo Natura.

## Un Esempio Pratico - Note sulla Natura

Per gli articoli sulla Natura, la categoria dell'articolo e le sotto-categorie per ciascun ramo del mondo vivente potrebbero apparire come nel seguente esempio:

![Categorie degli articoli sulla natura](../../../en/images/fields/fields-articles-categories-list.png)

Alcune caratteristiche evidenti della Natura da notare:

- La categoria Natura è per gli articoli che trattano della natura in generale piuttosto che di tipi specifici di piante o animali.
- Le sotto-categorie sono per articoli più specifici e potrebbero necessitare delle loro proprie sotto-categorie.
- Tutte le forme di vita hanno Nomi comuni e Nomi latini.
- Fiori e Alberi hanno una Stagione di Fioritura, Altezza e Ampiezza, ma Uccelli e Mammiferi no.
- Gli Uccelli hanno Apertura Alare e Lunghezza, mentre i Mammiferi hanno Altezza e Lunghezza.
- Il Colore può essere costante o variabile.

Il punto qui è che potrebbe essere necessario impostare Campi o Gruppi di Campi per caratteristiche comuni, come il Nome Latino, e separati Gruppi di Campi per ciascuna categoria di natura.

## Gruppi di Campi

Creare Gruppi di Campi per gli Articoli è molto semplice:

- Seleziona **Contenuto → Gruppi di Campi** dal menu dell'Amministratore
- Seleziona il pulsante **Nuovo** nella barra degli strumenti.
- Inserisci un **Titolo** appropriato.
- Inserisci una **Descrizione**. Questa appare sotto il campo nel modulo di modifica
  dell'articolo quando è selezionata l'opzione *Attiva Aiuto Inlinea*.
- Seleziona **Salva & Chiudi** dalla barra degli strumenti.

![Elenco dei gruppi di campi di contenuto](../../../en/images/fields/fields-field-groups-list.png)

### Ordinamento

Nel modulo di inserimento dati dell'articolo, i gruppi di campi appariranno nell'ordine
visualizzato in questo elenco. Trascina e rilascia gli elementi per cambiare l'ordine.

## Campi

Per creare un nuovo Campo articolo, seleziona **Contenuto → Campi** dal menu
dell'Amministratore e compila il modulo. Alcuni esempi sono illustrati
di seguito.

### Testo - Nome Latino

Nota che nello screenshot qui sotto questo campo è stato assegnato al gruppo Campo Natura e alla categoria Natura. Questo assicura che appaia sempre negli articoli della categoria Natura e in qualsiasi sotto-categoria.

![Campo di testo - nome latino nel gruppo natura](../../../en/images/fields/fields-latin-name.png)

### Caselle di controllo - Stagione di Fioritura

Le caselle di controllo appaiono nel modulo di Modifica Articolo per far selezionare la stagione di fioritura. Nella visualizzazione dell'articolo verranno elencate solo le stagioni selezionate. Ad esempio, se selezioni Primavera ed Estate, l'output mostrerà: Stagione di Fioritura: Primavera, Estate.

Nota che in questo screenshot il Campo è stato assegnato al gruppo Fiori e alla Categoria Fiori. Ciò dovrebbe garantire che il campo sia presente solo negli articoli sui fiori.

![Campo caselle di controllo - stagione di fioritura](../../../en/images/fields/fields-flowering-season.png)

### Colore - Color

Per confondere un po', il nome del tipo di campo è Color (ortografia USA), ma l'etichetta nella documentazione è Colour (ortografia britannica).

![Campo di colore](../../../en/images/fields/fields-colour.png)

Il Campo di Colore è assegnato al gruppo di campi Natura e alla categoria Natura poiché non è unico per i fiori.

### Intero - Resistenza

La resistenza di una pianta può essere rappresentata come un intero da 1 a 7. Non esiste un campo per un numero reale, quindi lunghezza e larghezza potrebbero essere interi con una scala (cm, m o ft) inclusa nell'etichetta. Ci sono le impostazioni di *Prefisso* e *Suffisso* nella scheda *Opzioni*. Se non c'è un limite superiore evidente, lascia vuoto il campo *Ultimo:*.

![Campo di resistenza](../../../en/images/fields/fields-hardiness.png)

La resistenza RHS è una proprietà di solito applicata ai fiori!

C'è un problema con il campo intero. Ha sempre un valore e quindi appare sempre nell'output. Puoi aggirare questo problema con una sovrascrittura del modello per *Plugin / Intero*. Ad esempio, potresti usare un valore sopra o sotto i limiti previsti per omettere il campo dall'output.

## Modulo di Modifica Articolo

Quando si apre un modulo Articoli: Nuovo, la Categoria predefinita è
Non categorizzato e le schede del modulo non includono Campi e Fiori.
Seleziona la categoria Fiori e il modulo viene ricaricato con quelle schede
presenti.

### Scheda Natura

![Scheda natura articolo bluebell](../../../en/images/fields/field-article-bluebell-nature-tab.png)

- **Nome Latino** Questo è un campo di inserimento testo, quindi si tratta semplicemente di digitare
  il nome latino della forma di vita di cui tratta l'articolo. Tuttavia, la categoria Natura
  copre la vita in generale così come specifici animali o piante. Quindi questo
  non è un campo *richiesto*.
- **Colore** Il campo di selezione colore può accettare sia un inserimento da tastiera di un
  valore di colore esadecimale sia un colore selezionato dallo strumento di scelta colore. Il numero esadecimale
  è xrrggbb dove rr sono i valori rossi, gg sono i valori verdi e bb sono i valori blu.
  In uscita, il sito visualizza il valore esadecimale, che non è molto utile!

### Scheda Fiori

![Scheda fiori articolo bluebell](../../../en/images/fields/field-article-bluebell-flowers-tab.png)

- **Stagione di Fioritura** Il campo con casella di controllo - i giacinti sono fiori ben noti 
  in primavera, quindi la selezione di una casella di controllo è appropriata.
- **Resistenza** Il campo intero. C'è un problema qui - non c'è un metodo
  disponibile per lasciare questo campo vuoto. Quindi è sempre presente nell'output,
  anche per articoli più generali sui fiori dove non è appropriato. C'è una soluzione alternativa che coinvolge un override del template.

## Risultato del Sito

Dai un'occhiata al risultato visualizzato nel tuo sito. In questo esempio è stato creato un singolo elemento di menu dell'articolo:

![Visualizzazione sito dell'articolo Bluebell](../../../en/images/fields/field-article-bluebell-site.png)

### Il Colore esadecimale

Il display predefinito dei dati è il valore del colore esadecimale, che non è molto utile. La soluzione semplice è creare un override del template per il plugin dei campi / colore, come mostrato nello screenshot qui sopra.

Basta sostituire questa riga:
```
echo htmlentities($value);
```
con queste righe:
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
E il valore esadecimale sarà preceduto da un campione con il colore di sfondo del valore.

