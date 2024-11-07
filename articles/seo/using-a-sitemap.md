<!-- Filename: Using_A_Sitemap / Display title: Utilizzo di una Sitemap  -->

## Usare una Sitemap

Sebbene i motori di ricerca possano solitamente trovare le tue pagine tramite i collegamenti da altri luoghi su internet, è una buona pratica creare una Sitemap che fornisca ai 'bot' dei motori di ricerca un elenco delle pagine del tuo sito web - pensalo come una mappa per trovare tutto il contenuto del tuo sito. Le Sitemaps non sono importanti solo per i motori di ricerca, sono anche molto utili per le persone con disabilità che potrebbero avere bisogno di un'interfaccia semplice per visualizzare la struttura del tuo sito e navigare nel sito senza usare le tue strutture di menu. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html" rel="nofollow noreferrer noopener">Nota del Gruppo di Lavoro del W3C sulle Sitemaps</a>

Una sitemap serve a diversi scopi:

- Fornisce un elenco strutturato che mostra una panoramica di tutti i contenuti sul tuo sito web
- Permette a un visitatore di ottenere rapidamente una panoramica della struttura del tuo sito
- Fornisce un modo alternativo di navigare il tuo sito web, senza la necessità di strutture di menu complesse
- Fornisce ai motori di ricerca un mezzo per trovare contenuti che potrebbero non essere disponibili attraverso le strutture di menu (es. pagine di destinazione)

### Tipi di Sitemap

È possibile fornire sitemap per tipi specifici di informazioni, inclusi:

- Video <a href="https://support.google.com/webmasters/answer/80471" rel="nofollow noreferrer noopener">guida di Google sulle sitemap video</a>
- Immagini <a href="https://support.google.com/webmasters/answer/answer.py?answer=178636" rel="nofollow noreferrer noopener">guida di Google sulle sitemap delle immagini</a>
- Notizie <a href="https://support.google.com/news/publisher/answer/75717" rel="nofollow noreferrer noopener">guida di Google sulle sitemap delle Notizie</a>
- Internazionale <a href="https://support.google.com/webmasters/answer/2620865?hl=en&amp;ref_topic=2370587" rel="nofollow noreferrer noopener">guida di Google sulle sitemap internazionali</a>

Queste sitemaps specializzate ti permettono di fornire informazioni relative al tipo di media specifico - per esempio, con una sitemap video puoi fornire informazioni sulla durata, la categoria e lo stato di idoneità; con le sitemaps delle immagini puoi specificare il soggetto dell'immagine, la licenza d'uso e il tipo di immagine.

### Creare una sitemap

Su un sito statico, creare una sitemap è semplicemente una questione di creare manualmente un file XML utilizzando gli standard appropriati e salvarlo come un file XML. Su un sito dinamico, dove il contenuto cambia regolarmente, questo non è veramente un'opzione - dovresti aggiornare manualmente il file sitemap ogni volta che aggiungi nuovi contenuti!

Per questo motivo ci sono diverse estensioni disponibili nella Joomla Extensions Directory (<a href="https://extensions.joomla.org/category/structure-a-navigation/site-map" rel="noreferrer noopener">categoria Sitemap nella Joomla Extensions Directory</a>) che ti permettono di costruire dinamicamente una sitemap che rispetta gli standard delle sitemap attesi dai motori di ricerca. <a href="https://www.sitemaps.org/" rel="nofollow noreferrer noopener">Protocollo Sitemaps</a>

La maggior parte di queste estensioni funzionano scegliendo le voci di menu che desideri includere in una sitemap e specificando quanto spesso cambiano (vedi Frequenza di Aggiornamento). È anche possibile includere sottopagine da quelle voci di menu (per esempio, una voce di menu potrebbe portare a una pagina blog di categoria, ma tu vuoi mostrare tutti gli articoli che sono mostrati su questa pagina come elementi individuali - un altro esempio potrebbe essere una voce di menu che punta a una pagina di categoria del negozio, e nella sitemap vorresti elencare la categoria e poi ciascun prodotto al suo interno come un link separato).

### Frequenza di Aggiornamento

Sebbene tu possa specificare manualmente nella tua Sitemap quanto frequentemente gli spider dei motori di ricerca dovrebbero visitare il tuo sito web, la maggior parte dei motori di ricerca ha sistemi integrati che regolano automaticamente la frequenza delle visite di ritorno in base a quanto spesso viene cambiata la pagina in questione.

Per esempio, se dici ai bot dei motori di ricerca di visitare la tua pagina su base giornaliera, ma quando visita la pagina nulla è cambiato per una settimana, potrebbe regolare di conseguenza la frequenza delle visite di ritorno e non tornare tanto spesso quanto hai detto. Puoi richiedere, tramite i vari portali dei webmaster, che la frequenza delle visite di ritorno sia modificata se necessario.

Questo suggerisce, quindi, che se hai contenuti che cambiano regolarmente, il tuo sito verrà 'spiderato' più frequentemente - portando a contenuti che vengono indicizzati più rapidamente rispetto ai siti web che non cambiano spesso.

È generalmente sensato specificare che le pagine statiche vengono esplorate meno frequentemente di quelle che cambiano regolarmente. Per esempio, un articolo di testo statico potrebbe essere impostato con una frequenza di aggiornamento di una volta al mese, mentre il tuo blog o la pagina delle notizie potrebbe essere impostato con una frequenza di aggiornamento di una volta al giorno o una volta a settimana, a seconda di quanto spesso aggiungi nuovi contenuti.

### Sitemaps HTML

Una sitemap HTML è essenzialmente un indice per il tuo sito che puoi rendere disponibile ai visitatori del tuo sito web. Questo serve a due scopi:

1. Fornisce un luogo in cui i visitatori possono andare per accedere facilmente a qualsiasi contenuto sul tuo sito, anche se non è necessariamente facile da accedere tramite altri strumenti di navigazione sul sito
2. Fornisce un deposito centralizzato di link ai contenuti del tuo sito che può essere facilmente indicizzato dai motori di ricerca
3. Permette agli utenti con disabilità di navigare rapidamente nel tuo sito con un semplice elenco di link, piuttosto che attraverso menu complessi

Al minimo, una sitemap dovrebbe collegarsi alle sezioni principali e alle pagine all'interno del tuo sito, ma più dettagliata riesci a farla, meglio è.

Sono disponibili estensioni menzionate in precedenza che creano automaticamente sitemaps basate sui contenuti di Joomla.

### Sitemaps XML

Le Sitemaps XML sono un modo facile per i webmaster di informare i motori di ricerca su nuove e vecchie pagine sui loro siti che sono disponibili per l'esplorazione. Nella sua forma più semplice, una Sitemap è un file XML che elenca gli URL di un sito insieme a metadati aggiuntivi su ciascun URL (quando è stato aggiornato l'ultima volta, quanto spesso cambia di solito e quanto è importante, rispetto ad altri URL nel sito) in modo che i motori di ricerca possano esplorare il sito in modo più intelligente.

Utilizzare il protocollo Sitemap non garantisce che le pagine web vengano incluse nei motori di ricerca, ma fornisce suggerimenti ai web crawler per fare un lavoro migliore nell'esplorare il tuo sito.

1. Una sitemap XML fornisce un elenco di link ai contenuti del tuo sito che può essere facilmente indicizzato dai motori di ricerca
2. È possibile creare sitemap XML specifiche per Notizie, URL Mobile, Immagini e Video

Sono disponibili estensioni che creano automaticamente sitemaps XML basate sui contenuti di Joomla.

*Tradotto da openai.com*

