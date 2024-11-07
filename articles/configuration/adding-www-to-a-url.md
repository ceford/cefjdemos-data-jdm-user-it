<!-- Filename: Adding_www_to_a_url / Display title: Aggiungere www a un URL  -->

## Espressioni Regolari di Apache .htaccess

Per una soluzione semplice, aggiungi quanto segue al tuo file `.htaccess`:

```bash
    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$ [NC]
    RewriteRule (.*) https://www.example.com/$1 [R=301,L]
```

In questo caso, un URL della forma `https://example.com/index.php?item=1` sarà
reindirizzato a `https://www.example.com/index.php?item=1`.

Nell'esempio sopra:

* `RewriteCond` definisce una condizione di test.
* `%{HTTP_HOST}` utilizza la variabile host dalla richiesta (example.com).
* `!` significa NON e `^` significa INIZIO - quindi, non inizia con www.example.com
* `(` e `)` catturano qualsiasi cosa sia tra parentesi per un uso successivo.
* `\` trasforma il carattere successivo da carattere di controllo a carattere effettivo.
* `.` di solito significa qualsiasi carattere ma preceduto da \ significa un punto fermo.
* `?` rende l'abbinamento facoltativo.
* `$` significa FINE (dell'abbinamento facoltativo).
* `[NC]` sta per No Case cioè non fa distinzione tra maiuscole e minuscole.
* `RewriteRule` è valido se l'url non inizia con www.
* `(.*)` è un modello, in questo caso un singolo carattere ripetuto 0 o più
    volte, significando la parte del percorso dell'URL. Viene catturato come $1.
* `https://www.example.com/` è il sostituto per la parte host dell'URL.
* `$1` è il percorso catturato.
* `[]` contiene flag - istruzioni su cosa fare.
* `R=301` è un'istruzione per inviare un'intestazione Moved Permanently.
* `L` significa Ultimo nel set - poiché è stato trovato un abbinamento, ignora qualsiasi regola successiva.

Una soluzione più completa che risolve diversi altri problemi di canonizzazione allo stesso tempo:

```bash
    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]
```

Se desideri capire cosa significa tutto questo potresti leggere questi articoli:

* [Introduzione a Apache mod_rewrite](https://httpd.apache.org/docs/2.4/rewrite/intro.html)
* [Introduzione ai Reindirizzamenti .htaccess](https://www.danielmorell.com/guides/htaccess-seo/redirects/introduction-to-redirects)

*Tradotto da openai.com*

