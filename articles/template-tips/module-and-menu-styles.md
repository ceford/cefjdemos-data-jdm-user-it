<!-- Filename: J4.x:Module_and_Menu_Styles / Display title: Stili di Modulo e Menu  -->

## Informazioni sui Cascading Style Sheets

Una pagina web generata da Joomla! è costituita da tag HTML con attributi di stile sotto forma di dichiarazioni di classe. Ad esempio, un intestazione all'interno di un articolo potrebbe essere `<h3 class="special-warning">Attenzione!</h3>`. Quell'intestazione potrebbe apparire con un carattere più grande, colori diversi per il testo e lo sfondo, e magari un bordo e un'icona di avvertimento. Gli stili di classe sarebbero definiti nel file user.css nel modello, in questo modo:
```css
    h3.special-warning {
      color: #900;
      background-color: #fee;
      border: 1px solid #900;
      padding: 1rem;
      font-size: 2rem;
    }
```
Questo funziona perché il foglio di stile user.css viene caricato per ultimo e qualsiasi stile esso contenga ha la precedenza sugli stessi stili nei file css caricati precedentemente. Lo stile `special-warning` non si applica ad altri tag `<h3>`, ma solo a quelli con questa specifica classe. Funziona all'interno di un articolo perché lì inserisci tu stesso il nome della classe.

Ma cosa succede se vuoi stilizzare un modulo o un'intera pagina? Ad esempio, potresti applicare colori di sfondo diversi a diversi moduli o pagine. Oppure potresti stilizzare l'intestazione della tua pagina principale in modo diverso rispetto alle intestazioni di altre pagine. Tutto questo può essere ottenuto aggiungendo nomi di classe nel modulo di modifica del modulo o nel modulo di modifica del menu. Le classi di stile vengono poi inserite nel file user.css.

## Stili del Modulo

Questo semplice esempio applica stili personalizzati al modulo di Login e al suo titolo. Lo screenshot seguente mostra i nomi degli stili inseriti nella scheda Avanzate del modulo di modifica Login. La Classe Modulo è stata impostata su `make-me-light-green` e la Classe Header è stata impostata su `make-me-dark-green`. Nota che puoi includere segni meno o sottolineature nei nomi delle classi, ma gli spazi separano nomi di classi diversi.

![modulo di modifica login scheda avanzate che mostra la classe personalizzata](../../../en/images/templates/templates-edit-module-style.png)

Le seguenti dichiarazioni di stile sono utilizzate nel file user.css:
```css
    .make-me-light-green {
      background-color: #efe;
      border-color: darkgreen;
    }
    .make-me-dark-green {
      color: darkgreen;
      border-color: #264f71;
    }
```
Attenzione al punto (.) che viene utilizzato in css per definire una classe con quel nome. Il punto non deve essere usato nel modulo di inserimento dati. Il risultato in questo esempio è il seguente:

![aspetto del sito del modulo personalizzato con strumenti di sviluppo](../../../en/images/templates/templates-edit-module-style-result.png)

Il fondo dell'immagine mostra il pannello degli Strumenti per Sviluppatori del browser con il tag `<div>` di chiusura del modulo Login selezionato. Puoi vedere che lo stile personalizzato Classe Modulo è stato aggiunto agli stili già definiti nel template del modulo. La linea successiva mostra il tag `<h3>`, anch'esso con la Classe Header personalizzata aggiunta agli stili già definiti.

Potrebbe piacerti o meno questo stile del modulo! Ma questa è solo una lezione su come farlo, non su quale sia uno schema di colori efficace!

## Stili di Pagina

Ci sono diversi modi per personalizzare l'aspetto generale di una pagina.
Tutto funziona tramite il modulo Menu: Modifica Elemento:

- La scheda Dettagli ha un'opzione Stile Modello da cui è possibile selezionare
  un modello specifico da utilizzare.
- La scheda Layout Blog ha un campo Classe Articolo in Evidenza e Classe Articolo
  in cui è possibile digitare il nome di una classe.
- La scheda Opzioni ha un campo Scegli un Layout da cui è possibile scegliere
  tra i layout disponibili per tutti gli elementi.
- La scheda Tipo di Link ha campi per una Classe Link, una Classe Icona Link e
  una Classe Immagine.
- La scheda Visualizzazione Pagina ha campi per una Classe Pagina.

È proprio l'ultima di questa lista che viene trattata in questo articolo. Cosa
succede inserendo `make-me-aliceblue` in questo campo? E nel file user.css viene inserito quanto segue:
```css
    .make-me-aliceblue {
      background-color: aliceblue;
    }
```
La classe viene aggiunta al tag body della pagina:

![aspetto del sito della pagina personalizzata con strumenti per sviluppatori](../../../en/images/templates/templates-edit-page-class-result.png)

*Tradotto da openai.com*
