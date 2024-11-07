<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-display.md / Display title: Visualizzazione delle Notizie -->

## Il Modulo di Visualizzazione dei Feed

È disponibile un modulo principale *Visualizzazione dei Feed* per mostrare le notizie da altri siti. Lo screenshot seguente mostra il modulo di inserimento dati con l'URL del feed di notizie degli Annunci Joomla. Nota che il Conteggio delle Parole è impostato a 100. Altrimenti, la lunghezza di un annuncio può essere eccessiva per un modulo nella barra laterale.

![Inserimento dati modulo di visualizzazione dei feed](../../../en/images/news-feeds/news-joomla-news-form.png "Inserimento dati modulo di visualizzazione dei feed")

Il risultato può essere brutto ma può essere migliorato con alcuni stili personalizzati in user.css:

![Inserimento dati modulo di visualizzazione dei feed](../../../en/images/news-feeds/news-joomla-news-display.png "Inserimento dati modulo di visualizzazione dei feed")   

## Pagine di Visualizzazione Feed

In alternativa alla visualizzazione delle notizie in un modulo, puoi creare un elemento di menu per visualizzare un feed di notizie in una pagina web. Dal menu dell'Amministratore:

* Seleziona **Componenti / NewsFeeds / Feeds**. Potresti prima creare una Categoria per le notizie.
* Seleziona il pulsante **Nuovo** nella *Toolbar*.
* Compila il modulo **Feed di Notizie: Modifica**:
    - Il **Link** è il collegamento RSS copiato da una fonte remota.
    - La **Descrizione** è facoltativa.
    - La scheda **Opzioni** ha elementi per controllare la *Visualizzazione* del feed.
* **Salva & Chiudi**

![Inserimento dati del componente NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Inserimento dati del componente NewsFeed")

Crea un elemento di menu a partire dal menu dell'Amministratore:

* Seleziona **Menu / Menu Principale** o qualsiasi altro menu per questo elemento.
* Seleziona **Nuovo** dalla Toolbar del *Menu: Voci*.
* Nel **Tipo di Voce di Menu** usa il pulsante **Seleziona** per trovare e selezionare *News Feeds / Singolo Feed di Notizie*.
* Compila il resto del modulo come appropriato.
* **Salva & Chiudi**

![Inserimento dati voce di menu NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Inserimento dati voce di menu NewsFeed")

Verifica: vai al menu del Sito e seleziona l'elemento del menu Feed.

![Visualizzazione NewsFeed](../../../en/images/news-feeds/news-feed-display.png "Visualizzazione NewsFeed")

Ogni elemento nel feed è un `<li>` all'interno di un tag `<ul>` quindi per impostazione predefinita appare segnato da un punto. Questo non è così evidente se gli elementi sono lunghi. Puoi applicare i tuoi stili in *user.css*. Il seguente codice posizionerà ogni elemento in una casella distinta:

```
ul.com-newsfeeds-newsfeed__items {
  list-style-type: none;
  padding-left: 0;
}

ul.com-newsfeeds-newsfeed__items > li {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 2px solid navy;
}
```
Che appare così:

![Visualizzazione personalizzata NewsFeed](../../../en/images/news-feeds/news-feed-custom-display.png "Visualizzazione personalizzata NewsFeed")

## Elencare i Feed di Notizie in una Categoria

La pagina *Joomla! RSS News Feeds* elenca otto feed di notizie separati. Potresti
creare un feed per alcuni o tutti e assegnarli a una Categoria, ad esempio *Joomla
News*. Poi puoi creare un elemento di menu con il *Tipo di Elemento di Menu* impostato su *Elenca i Feed di Notizie in una Categoria* e la Categoria impostata su *Joomla News*.

![Modulo del menu feed di notizie per categoria](../../../en/images/news-feeds/news-feed-menu-category-form.png "Modulo del menu feed di notizie per categoria")

Prova a vedere il risultato!

