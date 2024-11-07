<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-feeds.md / Display title: Feed di notizie  -->

## Introduzione ai Feed di Notizie

C'era una volta in cui era pratica comune per un sito web visualizzare notizie provenienti da siti remoti in una pagina o pannello. I browser avevano persino lettori di notizie integrati per fare proprio questo. I tempi cambiano e i browser principali non offrono più questa opzione. E ci sono nuovi metodi per condividere i contenuti dei siti, specialmente con i siti di social media.

Il metodo per condividere le notizie è il *Really Simple Syndication*, solitamente abbreviato in **RSS**, e questo ha ancora un posto nella promozione dei siti web. Lo screenshot seguente mostra *NetNewsWire*, un lettore RSS gratuito e open source per Mac. Altri lettori RSS sono disponibili per altre piattaforme. L'illustrazione mostra il feed RSS degli **Annunci di Joomla!** selezionato. Dieci annunci sono elencati con Titolo e breve descrizione. L'annuncio selezionato è mostrato per intero nella colonna di destra.

![Feed RSS degli Annunci di Joomla](../../../en/images/news-feeds/news-netnewswire-display.png "Annunci di Joomla")

Immagina cosa uno o più feed RSS potrebbero fare per il tuo sito web!

## Configurare un Feed di Notizie

Il tuo sito web ha i feed di notizie configurati di default. Un sito web Joomla 5 appena installato ha queste due righe vicino alla parte superiore del codice sorgente della pagina Home:

```
<link href="/j51/index.php?format=feed&amp;type=rss" rel="alternate" type="application/rss+xml" title="Home">
<link href="/j51/index.php?format=feed&amp;type=atom" rel="alternate" type="application/atom+xml" title="Home">
```
Queste righe permettono ai sistemi automatizzati di utilizzare sia i feed RSS che Atom. Atom è una specifica di syndication delle notizie più recente e leggermente diversa. Le righe saranno presenti in tutte le pagine **In Primo Piano** e nelle pagine **Blog di Categoria** ma non nella maggior parte degli altri tipi di pagina. È possibile disabilitare l'inclusione di questi feed RSS se lo si desidera.

## Attiva/Disattiva il Link RSS Feed

L'impostazione globale del link RSS Feed si trova nella scheda **Integrazione** della pagina Opzioni Articoli. Imposta su *Mostra* o *Nascondi* secondo le tue preferenze. L'impostazione predefinita è **Mostra**.

L'impostazione globale può essere modificata in un elemento di menu del blog di una categoria. Ancora una volta, seleziona la scheda *Integrazione* e imposta il *Link RSS Feed* su *Mostra* o *Nascondi*.

Il Feed RSS non può essere nascosto in una pagina principale degli articoli in evidenza (bug?)!

## Il Modulo dei Feed di Syndication

C'è un modulo core che puoi posizionare sulle pagine Blog in Primo Piano o di Categoria per fornire un link di Syndication. Compila i campi nella scheda Modulo. La maggior parte ha valori predefiniti adatti. Se il campo Etichetta viene lasciato vuoto, l'etichetta predefinita in inglese è *Feed Entries*. Nella scheda *Assegnazione Menu* seleziona **Su tutte le pagine**. Il modulo apparirà solo nelle pagine Blog in Primo Piano e di Categoria.

![Inserimento dati dei feed di syndication](../../../en/images/news-feeds/news-syndication-feeds-form.png "Inserimento dati dei feed di syndication")

Ricorda di assegnare il modulo a una *Posizione* e di renderlo *Pubblicato*.

Nella vista della pagina del sito, il modulo visualizza un link. Non è inteso per il clic a meno che tu non abbia configurato un Lettore di Notizie locale. Il link deve essere copiato per l'uso in un Lettore di Notizie su un altro sito o applicazione Lettore di Notizie.

![Visualizzazione dei feed di syndication](../../../en/images/news-feeds/news-syndication-feeds-display.png "Visualizzazione dei feed di syndication")

Nota che il link è per gli elementi di quella pagina. Quindi, se il tuo sito ha diverse pagine blog di categoria, avrai diversi feed RSS.

