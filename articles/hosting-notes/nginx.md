<!-- Filename: Nginx / Display title: Nginx -->

<a href="http://nginx.org/"
rel="nofollow noreferrer noopener">Nginx</a> è un server Web leggero
che alimenta
<a href="https://en.wikipedia.org/wiki/Nginx"
rel="nofollow noreferrer noopener">circa il 33%</a> dei server Web
attraverso tutti i domini. A meno che tu non abbia requisiti specifici
che richiedono un server Web pesante come Apache, è molto meglio usare
Nginx.

Di seguito sono riportate le istruzioni per eseguire Joomla! con l'<a
href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/"
rel="nofollow noreferrer noopener">esempio di PHP FastCGI</a>.
## Installare Nginx

Per Ubuntu, esegui *aptitude install Nginx*. Per altre distribuzioni, esegui il gestore dei pacchetti corrispondente o consulta la <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">pagina di installazione di Nginx</a>.

## Installare PHP FastCGI

Per Ubuntu, leggi l'<a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">Esempio PHP FastCGI</a>.

Per Gentoo, PHP verrà eseguito come un servizio FastCGI (FPM), quindi il server Nginx eseguirà PHP come un processo separato:

```shell
# echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
# emerge php
```

Le impostazioni predefinite di PHP-FPM sono adatte alla maggior parte dei server. Per configurazioni speciali, visita il <a href="http://php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">sito di PHP FPM</a>.

## Configurare Nginx

I file di configurazione di Nginx si trovano in:

- `/etc/nginx/sites-available/` su Ubuntu (per i siti che operano su
  quell'istanza di Nginx)
- `/etc/nginx/nginx.conf` su Gentoo e Raspbian (Debian ottimizzato per
  Raspberry Pi)

Ecco un esempio di file di configurazione Nginx, *joomla.conf*, che puoi
riutilizzare su tutti i tuoi siti con Nginx abilitato.

    server {
      listen 80;
        server_name TUO_DOMINIO;
        server_name_in_redirect off;

        access_log /var/log/nginx/localhost.access_log;
        error_log /var/log/nginx/localhost.error_log info;

        root PERCORSO_SUL_SERVER;
        index index.php index.html index.htm default.html default.htm;
        # Supporto per URL puliti (chiamati anche Search Engine Friendly)
        location / {
            try_files $uri $uri/ /index.php?$args;
        }

        # aggiungi intestazione globale x-content-type-options
        add_header X-Content-Type-Options nosniff;

        # nega l'esecuzione di script all'interno di directory scrivibili
        location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
            return 403;
            error_page 403 /403_error.html;
        }

        location ~ \.php$ {
          fastcgi_pass  127.0.0.1:9000;
          fastcgi_index index.php;
          include fastcgi_params;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include /etc/nginx/fastcgi.conf;
        }

        # caching dei file
        location ~* \.(ico|pdf|flv)$ {
            expires 1y;
        }

        location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
            expires 14d;
        }

    }

Presta attenzione a poche cose:

1.  Il parametro *fastcgi_pass* è impostato su *127.0.0.1:9000*,
    corrispondente alla porta su cui è configurato FPM per ascoltare.
    Questo significa che puoi eseguire i processi PHP su server separati.
    Su Gentoo, puoi trovare questa configurazione nel file
    */etc/php/fpm-php5.3/php-fpm.conf/*. 
2.  Non dimenticare di sostituire TUO_DOMINIO e PERCORSO_SUL_SERVER sopra
    a seconda del tuo dominio e del percorso di Joomla sul tuo server.

## Supporto GZip

Se hai bisogno del supporto per la compressione GZip, aggiungi la seguente sezione alla sezione *http* del file di configurazione principale di Nginx:

    gzip on;
    gzip_http_version 1.1;
    gzip_comp_level 6;
    gzip_min_length 1100;
    gzip_buffers 4 8k;
    gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
    gzip_proxied any;
    gzip_disable "MSIE [1-6]\.";

## Fonti

- <a href="https://wiki.gentoo.org/wiki/Nginx" rel="nofollow noreferrer noopener">Nginx in Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/" rel="nofollow noreferrer noopener">Nginx per Windows</a>
- <a href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview" rel="nofollow noreferrer noopener">Nginx in Ubuntu</a>
- <a href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html" rel="nofollow noreferrer noopener">Nginx in Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">Installazione e configurazione di PHP-FPM</a>
- <a href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/" rel="nofollow noreferrer noopener">Compressione e decompressione</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/" rel="nofollow noreferrer noopener">Creare regole di riscrittura NGINX</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html" rel="nofollow noreferrer noopener">Come Nginx elabora una richiesta</a>

*Tradotto da openai.com*

