<!-- Filename: Preconfigured_htaccess / Display title: Il file htaccess.txt  -->

## Introduzione

Un server web Apache utilizza un file .htaccess per la configurazione specifica del sito. Un file htaccess preconfigurato (`htaccess.txt`) viene fornito con Joomla. Si trova nella directory principale di Joomla e contiene istruzioni per evitare comuni exploit degli hacker e implementare URL SEF. Se Joomla è installato in una sottodirectory, potrebbe esserci un ulteriore file `.htaccess` nella directory padre. Apache li elabora uno dopo l'altro.

La pratica normale è rinominare il file `htaccess.txt` fornito da Joomla in `.htaccess` in concomitanza con la selezione delle impostazioni SEO nel pannello di Configurazione Globale. Il tuo servizio di hosting potrebbe aggiungere ulteriori impostazioni a .htaccess, quindi potrebbe essere meglio unire il tuo file .htaccess con qualsiasi file .htaccess fornito dal sistema esistente.

### Configurazione della piattaforma

Il file attivo è impostato in uno dei file httpd.conf con:
```
    AccessFileName .htaccess
```
Il valore predefinito è .htaccess (che lo rende nascosto su file system simili a Unix). Non è necessario cambiarlo.

Sulla piattaforma Windows potresti cambiarlo in:

    AccessFileName htaccess.ini

in modo da poterlo modificare più facilmente.

Non apportare modifiche a `htaccess.txt` perché potrebbe essere sovrascritto da un aggiornamento di Joomla e eventuali modifiche andrebbero perse.

## Aggiornamenti di Joomla

Il file htaccess.txt può cambiare da una versione di Joomla all'altra. In caso di dubbi o problemi strani che si verificano dopo l'aggiornamento, assicurati che il tuo file .htaccess sia aggiornato. Questo è il contenuto del file `htaccess.txt` incluso con Joomla 5.1:

```bash
##
# @package    Joomla
# @copyright  (C) 2005 Open Source Matters, Inc. <https://www.joomla.org>
# @license    GNU General Public License version 2 o successiva; vedi LICENSE.txt
##

##
# LEGGI QUESTO COMPLETAMENTE SE SCEGLI DI USARE QUESTO FILE!
#
# La riga 'Options +FollowSymLinks' può causare problemi con alcune configurazioni del server.
# È richiesta per l'uso di Apache mod_rewrite, ma potrebbe essere già stata impostata dal
# tuo amministratore del server in modo da non consentire modifiche in questo file .htaccess.
# Se il suo utilizzo causa un errore sul tuo sito, commentalo (aggiungi # all'inizio della
# riga), ricarica il tuo sito nel browser e testa i tuoi URL sef. Se funzionano, significa
# che è stato impostato dal tuo amministratore del server e non è necessario impostarlo qui.
##

## ERRORI DI MANCANZA DI CSS O JAVASCRIPT
#
# Se il tuo sito appare strano dopo aver abilitato questo file, il tuo server sta probabilmente già
# comprimendo (gzip) i file css e js e dovresti commentare la sezione GZIP di questo file.
##

## OPENLITESPEED
#
# Se stai utilizzando un server web OpenLiteSpeed, qualsiasi modifica apportata a questo file non avrà effetto fino a quando non avrai riavviato il server web.
##

## Può essere commentato se causa errori, vedi le note sopra.
Options +FollowSymlinks
Options -Indexes

## Nessuna lista delle directory
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>

## Sopprimere il rilevamento del tipo mime nei browser per tipi sconosciuti
<IfModule mod_headers.c>
    Header always set X-Content-Type-Options "nosniff"
</IfModule>

## Proteggere da determinate richieste cross-origin. Maggiori informazioni possono essere trovate qui:

Sure, I can help translate the text, but it seems like you only provided a link rather than any Markdown text that requires translation. Could you please provide the specific Markdown text you need translated?

## https://web.dev/why-coop-coep/
#<IfModule mod_headers.c>
#    Header always set Cross-Origin-Resource-Policy "same-origin"
#    Header always set Cross-Origin-Embedder-Policy "require-corp"
#</IfModule>

## Disabilita JavaScript inline quando apri direttamente file SVG o li embeddi con il tag object
<FilesMatch "\.svg$">
  <IfModule mod_headers.c>
    Header always set Content-Security-Policy "script-src 'none'"
  </IfModule>
</FilesMatch>

## Queste direttive sono abilitate solo se il modulo mod_rewrite di Apache è abilitato
<IfModule mod_rewrite.c>
    RewriteEngine On

    ## Inizio - Regole di riscrittura per bloccare alcuni exploit comuni.
    # Se si verificano problemi sul tuo sito, commenta le operazioni elencate
    # di seguito aggiungendo un # all'inizio della riga.
    # Questo tenta di bloccare il tipo più comune di `attempts` di exploit su Joomla!
    #
    # Blocca qualsiasi script che tenta di base64_encode i dati all'interno dell'URL.
    RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
    # Blocca qualsiasi script che include un tag <script> nell'URL.
    RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
    # Blocca qualsiasi script che tenta di impostare una variabile PHP GLOBALS tramite URL.
    RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
    # Blocca qualsiasi script che tenta di modificare una variabile _REQUEST tramite URL.
    RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
    # Restituisce l'intestazione 403 Forbidden e mostra il contenuto della home page del root
    RewriteRule .* index.php [F]
    #
    ## Fine - Regole di riscrittura per bloccare alcuni exploit comuni.

    ## Inizio - Reindirizzamenti personalizzati
    #
    # Se hai bisogno di reindirizzare alcune pagine, o impostare un reindirizzamento canonico non-www verso
    # www (o viceversa), inserisci quel codice qui. Assicurati che quei
    # reindirizzamenti utilizzino la sintassi corretta di RewriteRule e le flag [R=301,L].
    #
    ## Fine - Reindirizzamenti personalizzati

    ##
    # Decommenta la riga seguente se l'URL del tuo server web
    # non è direttamente correlato ai percorsi fisici dei file.
    # Aggiorna la tua directory di Joomla! (soltanto / per la root).
    ##

    # RewriteBase /

    ## Inizio - Sezione SEF principale di Joomla!.
    #
    # Correzione PHP FastCGI per l'autorizzazione HTTP, richiesta per l'applicazione API
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
    # -- URL SEF per l'applicazione API
    # Se il percorso richiesto inizia con /api, il file non è /api/index.php
    # e la richiesta non è già stata riscritta internamente verso lo script
    # api/index.php
    RewriteCond %{REQUEST_URI} ^/api/
    RewriteCond %{REQUEST_URI} !^/api/index\.php
    # e il percorso richiesto e il file non corrispondono direttamente a un file fisico
    RewriteCond %{REQUEST_FILENAME} !-f
    # e il percorso richiesto e il file non corrispondono direttamente a una cartella fisica
    RewriteCond %{REQUEST_FILENAME} !-d
    # riscrivi internamente la richiesta allo script /api/index.php
    RewriteRule .* api/index.php [L]
    # -- URL SEF per l'applicazione frontend pubblica
    # Se il percorso richiesto e il file non sono /index.php e la richiesta
    # non è già stata riscritta internamente verso lo script index.php
    RewriteCond %{REQUEST_URI} !^/index\.php
    # e il percorso richiesto e il file non corrispondono direttamente a un file fisico
    RewriteCond %{REQUEST_FILENAME} !-f
    # e il percorso richiesto e il file non corrispondono direttamente a una cartella fisica
    RewriteCond %{REQUEST_FILENAME} !-d
    # riscrivi internamente la richiesta allo script index.php
    RewriteRule .* index.php [L]
    #
    ## Fine - Sezione SEF principale di Joomla!.
</IfModule>

## Queste direttive sono abilitate solo se il modulo Apache mod_rewrite è disabilitato
<IfModule !mod_rewrite.c>
    <IfModule mod_alias.c>
        # Quando Apache mod_rewrite non è disponibile, istruiamo un reindirizzamento temporaneo
        # della pagina iniziale al front controller in modo esplicito affinché il sito web
        # e i link generati possano ancora essere usati.
        RedirectMatch 302 ^/$ /index.php/
        # RedirectTemp non può essere usato invece
    </IfModule>
</IfModule>

## GZIP & BROTLI
## Queste direttive sono attivate solo se il modulo mod_headers di Apache è attivato.
## Questa sezione verificherà se esiste un file .gz e, in tal caso, lo trasmetterà in streaming
## direttamente o come alternativa comprimere con gzip qualsiasi risorsa al volo
## Se il tuo sito inizia a sembrare strano dopo aver abilitato questo file, e vedi
## ERR_CONTENT_DECODING_FAILED nella scheda rete della console del tuo browser
## Se il tuo server sta già comprimendo i file CSS e JS usando gzip, non hai bisogno di questo.
## Blocco abilitato nel tuo .htaccess

<IfModule mod_headers.c>
    # Servi i file CSS compressi con gzip se esistono
    # e il client accetta gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.css" "$1\.css\.gz" [QSA]

    # Servi i file JS compressi con gzip se esistono
    # e il client accetta gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.js" "$1\.js\.gz" [QSA]

    # Fornisci i tipi di contenuto corretti e previeni la doppia compressione con mod_deflate.
    RewriteRule "\.css\.gz$" "-" [T=text/css,E=no-gzip:1,E=no-brotli:1]
    RewriteRule "\.js\.gz$" "-" [T=text/javascript,E=no-gzip:1,E=no-brotli:1]

    <FilesMatch "(\.js\.gz|\.css\.gz)$">
        # Fornisci il tipo di codifica corretto.
        Header set Content-Encoding gzip

        # Costringe i proxy a memorizzare nella cache separatamente i file css/js compressi e non compressi.
        Header append Vary Accept-Encoding
    </FilesMatch>
</IfModule>
```
