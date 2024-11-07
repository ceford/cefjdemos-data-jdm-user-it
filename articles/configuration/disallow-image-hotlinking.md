<!-- Filename: How_do_you_block_direct_hot_linking_to_image_files_using_htaccess%3F / Display title: Vietare il collegamento diretto alle immagini -->

## Definizione

Il hotlinking è la pratica di collegare un'immagine presente su un sito web da un articolo su un altro sito web. Può essere una pratica molto utile. Questo sito utilizza molte immagini che in realtà sono situate sul sito docs.joomla.org. Ciò consente di risparmiare tempo ed energie necessarie per creare schermate e sulla larghezza di banda di questo sito. Tuttavia, possono sorgere problemi di copyright e potresti voler impedire che le tue immagini siano usate in questo modo.

Il metodo descritto qui utilizza un file *.htaccess*, che è una funzionalità del server Apache. Altri server web potrebbero fornire altri metodi per prevenire il hotlinking.  

## Indicazioni

Inserisci il seguente codice nel file *.htaccess* della directory principale.

```
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?iltuodominio.com [NC]
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?google.com [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

### Spiegazione

* La prima RewriteCond permette richieste dirette utilizzando un URL senza referrer.
* La seconda RewriteCond permette richieste dal tuo stesso dominio. Il flag
    *\[NC\]* significa *No Case*, ossia corrisponde sia ai caratteri maiuscoli che minuscoli.
* La terza RewriteCond permette richieste da Google, in modo che
    le tue immagini possano ancora apparire nei risultati di ricerca. Puoi aggiungere
    righe simili per qualsiasi altro sito che desideri permettere.
* La RewriteRule blocca le richieste per i file immagine da tutti i domini non
    precedentemente permessi. Il flag F ordina al browser di restituire un'intestazione
    Forbidden (403). L sta per ultima regola.

### Bloccare il Hot Linking da Domini Specifici

Per evitare il hotlinking solo da domini specifici, come *myspace.com*,
*blogspot.com* e *livejournal.com*, consentendo ad altri siti di hotlinkare
le tue immagini, usa il seguente codice:

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?myspace\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?blogspot\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?livejournal\.com/ [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```
Puoi aggiungere quanti diversi domini vuoi. Ogni riga *RewriteCond* tranne
l'ultima dovrebbe terminare con i flag *\[NC,OR\]*. *NC* significa ignorare
le maiuscole. *OR* significa "Oppure Successiva", nel senso corrisponde a
questa linea **o** alla successiva. L'ultima *RewriteCond* omette il flag *OR*
per interrompere la corrispondenza dopo l'ultima *RewriteCond*.

*Tradotto da openai.com*

