<!-- Filename: J4.x:Assorted_Issues / Display title: Problemi Varie  -->

## Problema di Reindirizzamento Dopo l'Aggiornamento alla Versione 4.0.6

Si tratta di un bug! Linea 243 di *plugins/system/redirect/redirect.php*:

       $db->updateObject('#__redirect_links', $redirect, 'id');

dovrebbe essere

       $this->db->updateObject('#__redirect_links', $redirect, 'id');

## Una Pagina Visualizzata Senza Stile

Possibile causa: Una sezione gzip nel file *.htaccess* sta comprimendo
i file CSS e JavaScript già compressi.

Guarda questa sezione del file *.htaccess*:

    ## Queste direttive sono abilitate solo se il modulo mod_headers di Apache è attivato.
    ## Questa sezione controllerà se esiste un file .gz e, in tal caso, lo trasmetterà
    ##     direttamente o comprimerà al volo qualsiasi risorsa con gzip
    ## Se il tuo sito inizia a sembrare strano dopo aver abilitato questo, e vedi
    ##     ERR_CONTENT_DECODING_FAILED nella scheda di rete della console del tuo browser,
    ##     allora il tuo server sta già comprimendo i file css e js con gzip e non hai bisogno
    ##     che questo blocco sia abilitato nel tuo .htaccess

    ...

Se presente, commenta o rimuovi.  

## L'elenco dei moduli del sito è vuoto

Possibile causa: La dimensione del buffer di ordinamento di MySQL potrebbe essere troppo piccola.

Usando phpMyAdmin, vai a **Home**→**Variabili**→**Dimensione buffer di ordinamento**.

Dovrebbe essere almeno 256K e preferibilmente 512K. Su alcuni servizi di hosting condiviso, potrebbe essere impostato a 128K. Chiedi al servizio di hosting di aumentarla.

## L'aggiornamento non riesce dopo l'aggiornamento alla versione 4.0.4

Causa: una modifica essenziale alla procedura di aggiornamento che riguarda un numero ristretto di utenti.

Cerca in *.htaccess* questa riga:

    RewriteRule ^administrator/components/com_joomlaupdate/restore\.php$ - [L]

Modificala in:

    RewriteRule ^administrator\/components\/com_joomlaupdate\/extract\.php$ - [L]

Per ulteriori informazioni, vedere:

<a href="https://www.joomla.org/announcements/release-news/5850-changes-to-update-process-that-you-need-to-be-aware-of.html" rel="noreferrer noopener">Cambiamenti nel processo di aggiornamento di cui devi essere a conoscenza</a>

## Articoli Visibili nel Database e nel Frontend ma Non Visibili nel Backend

Questo accade quando gli articoli sono importati direttamente nel database, una pratica che funzionava bene in Joomla 3 ma non in Joomla 4. La soluzione proposta da un utente è la seguente:

    Ho importato articoli direttamente nel database nella tabella #__content come facevo spesso in Joomla 3.
    Tuttavia, in Joomla 4 non erano visibili.

    In Contenuti > Categorie, i contatori degli articoli importati venivano conteggiati dagli oggetti di categoria.
    Ma non erano visibili in Contenuti > Articoli.

    Ho risolto creando i riferimenti necessari nella tabella #__workflow_associations per ogni articolo importato:
    item_id = ID dell'articolo, stage_id = 1 ed extension = com_content.article.

Un altro utente ha suggerito quanto segue:

Questa query dovrebbe risolvere il problema per voi. Sostituite \#\_\_ con il vostro prefisso di database.

Questa query impedisce duplicati nella tabella delle associazioni del workflow:

    INSERT INTO #__workflow_associations (item_id, stage_id, extension)
    SELECT c.id as item_id, '1', 'com_content.article' FROM #__content AS c
    WHERE NOT EXISTS (SELECT wa.item_id FROM #__workflow_associations AS wa WHERE wa.item_id = c.id);

*Tradotto da openai.com*

