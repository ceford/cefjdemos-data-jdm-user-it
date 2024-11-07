<!-- Filename: J4.x:How_to_Archive_an_Article / Display title: Articoli: Archivio  -->

## Introduzione

Con la crescita dei contenuti del tuo sito web, è probabile che alcuni di questi contenuti debbano essere aggiornati o sostituiti. Potresti decidere di depubblicare alcuni articoli, ma potresti avere la necessità di mantenerli in modo che le persone possano ancora visualizzarli.

Joomla! semplifica il processo di archiviazione degli articoli permettendoti di cambiare lo stato di un articolo in **Archiviato**. Un vantaggio dell'archiviazione è che rende più facile la gestione dei contenuti, ed è strutturata per anno.

Questo approccio basato sullo stato è una parte fondamentale della capacità di Joomla di gestire i contenuti in modo efficace ed efficiente. Una volta archiviati, Joomla fornisce metodi per accedere e visualizzare i contenuti archiviati.

## Archiviazione degli Articoli

Puoi archiviare un articolo in diversi luoghi:

- Un articolo precedente su
  [Aggiungere un Articolo](jdocmnaual?article=user/getting-started/adding-an-article)
  mostrava una schermata della pagina dell'elenco *Articoli* con un articolo selezionato e 
  l'elenco *Azioni* nella Toolbar aperta per mostrare le opzioni disponibili. Una di 
  queste è *Archivia*. Questo è probabilmente il modo migliore per archiviare un articolo. Nota 
  che puoi archiviare più articoli contemporaneamente. Selezionando uno o più articoli, 
  abiliterai l'elenco a discesa **Azioni**.
- Ogni articolo ha un'impostazione *Stato* nel modulo di modifica dell'articolo. 
  L'opzione *Archiviato* può essere impostata lì.
- All'interno di un tipo di voce di menu *Singolo Articolo*. Il campo *Seleziona Articolo* ha un'opzione 
  *Modifica* che apre un modulo a comparsa *Modifica Articolo* dove il campo *Stato* 
  può essere impostato come in un normale modulo di modifica dell'articolo. La voce di menu singolo 
  collega comunque all'articolo archiviato.

Gli articoli archiviati non compaiono più nell'elenco *predefinito* degli Articoli. Seleziona il 
pulsante *Opzioni Filtro* e poi *Archiviato* dal filtro *- Seleziona Stato -* 
per vedere l'elenco degli articoli archiviati.

## Visualizzazione del sito degli articoli archiviati

Una volta che gli articoli sono stati archiviati, ci sono diversi modi per visualizzarli dal frontend del sito.

### Tramite un menu

Esiste un tipo di voce di menu [Articoli Archiviati](jdocmanual?article=user/menus/menu-item-type-archived-articles) che puoi usare per creare un collegamento nel tuo menu agli articoli archiviati.

### Tramite un modulo

Esiste un modulo [Articoli – Archiviati](jdocmanual?article=user/modules/articles-archived-module) che puoi utilizzare per visualizzare in una delle posizioni del modulo del modello del tuo sito web.

Lo screenshot seguente mostra una pagina di *Articoli Archiviati* ottenuta con una voce di menu. Ci sono filtri per *Mese* e *Anno* e un limite di elenco con impostazioni da 5 a 100 e Tutti. Fai sempre attenzione a usare *Tutti*. Se restituisci migliaia di risultati, la tua pagina potrebbe essere lenta da caricare e non rispondere. Potresti esaurire il tempo o la memoria, portando al ritorno di un errore del server.

![Visualizzazione della pagina degli articoli archiviati](../../../en/images/articles/articles-archived-site.png)

Alla base della colonna di destra si trova il modulo *Articoli Archiviati*.  

## Ripristinare Articoli Archiviati

Per ripristinare un articolo archiviato si applica lo stesso processo: lo stato dell'articolo viene modificato da **Archiviato** a **Pubblicato**.  

## Suggerimenti

* Ricorda che gli articoli archiviati sono filtrati dalla visualizzazione nell'elenco degli *Articoli*. Devi cambiare il filtro *Stato* su *Archiviati* per visualizzarli.
* L'archiviazione non rimuove un articolo dalla pubblicazione.
* Puoi anche archiviare articoli dal frontend quando sei connesso per la modifica frontend.

*Tradotto da openai.com*

