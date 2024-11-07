<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Disabilita Elenco Directory  -->

## Contesto

Di default, su un server web Apache, una directory che non contiene un file di indice definito nella configurazione (index.html o index.php) visualizzerà un elenco di tutti i file e le sottodirectory presenti nella directory. Questo può essere utile su un server di test personale, ma rappresenta un grave rischio per la sicurezza su un server di produzione attivo.

In passato, era prassi comune includere un file index.html vuoto in tutte le directory di Joomla per prevenire questo problema su server configurati male. Questo non è più il caso. Ci si aspetta una corretta configurazione del server, sia nei file di configurazione del server che nei singoli file .htaccess. La prima opzione è preferibile in quanto viene applicata a tutti i siti web sul server.

Tuttavia, i siti in un ambiente di hosting condiviso possono aspettarsi che ciascun sito modifichi la configurazione del server utilizzando file .htaccess. Il server deve essere impostato su "AllowOverride Options" o "AllowOverride All" per abilitare le sovrascritture nei file .htaccess.

## Utilizzo di .htaccess

Il file htaccess.txt fornito con Joomla può essere utilizzato su server Apache
rinominandolo o copiandolo in .htaccess. Contiene molte impostazioni per contrastare
gli attacchi degli hacker ai siti Joomla. Tra le altre, vedrai le seguenti
impostazioni per prevenire la visualizzazione dei contenuti delle directory:

```
Options -Indexes

## Nessun elenco di directory
<IfModule mod_autoindex.c>
	IndexIgnore *
</IfModule>
```

## Testa il tuo sito

Un modo per testare il tuo sito è inserire l'URL della cartella delle tue immagini nella barra degli URL del browser: `https://yourdomain.com/images/`. Poiché la cartella delle immagini normalmente non contiene un file index.html o index.php, dovresti vedere una pagina completamente vuota. Se vedi un elenco di tutti i file e le cartelle, allora non stai impedendo la scansione delle directory in nessuna parte del tuo sito. Correggi!

*Tradotto da openai.com*

