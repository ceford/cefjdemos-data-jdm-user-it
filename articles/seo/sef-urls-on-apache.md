<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: URL SEF su Apache -->

## Verifica che .htaccess sia abilitato

Verifica che il tuo file di configurazione di Apache permetta gli override di .htaccess. Devi assicurarti che gli override siano abilitati altrimenti il file .htaccess nella tua directory radice di Joomla! verrà ignorato o causerà un errore. Nella sezione del file di configurazione del tuo host virtuale o nel file di configurazione principale (`httpd.conf`) devi avere qualcosa di simile all'esempio sotto che abilita gli override:

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[un'opzione],[un'opzione],...
</Directory>
```

Ci sono altri modi per testare se `.htaccess` è abilitato se non hai accesso ai file di configurazione del tuo sito. Ti preghiamo di fare riferimento al [tutorial su .htaccess](http://httpd.apache.org/docs/current/howto/htaccess.html) che si trova sul sito della *The Apache Software Foundation* per ulteriori informazioni.

## Passo per Passo

Queste sono istruzioni passo dopo passo. Si prega di seguirle nell'ordine in cui sono presentate qui. Se un passaggio fallisce, **non** continuare fino a quando non hai risolto il problema.

1. Rinomina il file `htaccess.txt` nella cartella di base di Joomla! in `.htaccess`.
2. *Questo passaggio potrebbe non essere necessario.* Apri `.htaccess` in un editor di testo. Togli il commento a `RewriteBase /` (rimuovi il primo carattere, \#). Se Joomla è installato in una sua cartella, inserisci il nome della cartella di Joomla dopo la barra. ad es. `RewriteBase /yourjoomlafolder`.
3. Accedi al tuo Back-end e apri la Configurazione Globale.
4. Abilita l'opzione **Usa riscrittura URL/mod_rewrite di Apache** e *Salva*. Questa opzione utilizza la funzione *mod_rewrite* di Apache per eliminare la parte "index.php" dell'URL.

    Verifica se il tuo sito funziona correttamente. I tuoi URL dovrebbero ora apparire come:

        `http://www.example.com/the-news/1-latest-news/1-welcome-to-joomla`

    Se questa opzione causa errori, consulta 
    [Come verificare se mod rewrite è abilitato sul tuo server](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server).

    - Se non è abilitato e hai accesso al file
      `apache/conf/httpd.conf`, apri quel file e controlla se la linea
      `LoadModule rewrite_module modules/mod_rewrite.so` è senza commento.
      Se necessario, togli il commento alla linea e riavvia il server web Apache.
    - Se *mod_rewrite* non può essere abilitato, lascia disattivata questa opzione. Non importa se lasci il file `.htaccess` rinominato.
5. *Se pensi che sia necessario*, abilita **Aggiungi suffisso agli URL** e *Salva*. Questa opzione aggiunge `.html` alla fine degli URL. Ci sono opinioni diverse sul fatto che ciò sia necessario o utile. I motori di ricerca non sembrano preoccuparsi se i tuoi URL finiscono con `.html` o meno.
6. Apri il Plugin Manager e abilita il plugin **Sistema - SEF**. Questo plugin aggiunge il supporto SEF ai link negli articoli di Joomla. Opera direttamente sull'HTML e non richiede un tag speciale.

*Tradotto da openai.com*

