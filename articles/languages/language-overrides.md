<!-- Filename: J4.x:Language_Overrides / Display title: Sostituzioni di Lingua  -->

## Posizioni dei File di Lingua

La maggior parte dei file di lingua di Joomla! sono situati in cartelle di lingua, una nella radice del sito e un'altra nella cartella dell'amministratore. Ogni lingua ha la sua sottocartella basata sui codici lingua standard RFC3066. Ogni estensione memorizza le sue traduzioni con un nome derivato dal nome dell'estensione. Alcuni esempi:

    siteroot/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.sys.ini

I file contengono righe costituite da una chiave e dalla sua traduzione:

    COM_CONTENT="Articoli"
    COM_CONTENT_ADD_NEW_MENU_ITEM="Nuovo elemento di menu"
    COM_CONTENT_ARTICLE_CONTENT="Contenuto"
    COM_CONTENT_ARTICLES_TABLE_CAPTION="Tabella degli Articoli"
    COM_CONTENT_ARTICLES_TITLE="Articoli"

Il codice PHP di Joomla utilizza la chiave. Quest'ultima viene sostituita dalla traduzione del testo in fase di esecuzione. Il file .ini contiene traduzioni utilizzate dall'estensione. I file sys.ini contengono traduzioni utilizzate da Joomla per gestire l'estensione. Un file di lingua può contenere centinaia di righe.

Si consiglia alle estensioni di terze parti di memorizzare i loro file di lingua nelle cartelle di lingua all'interno dell'estensione. In questo modo sono al sicuro dall'eliminazione nel caso in cui un amministratore decida di disinstallare una lingua. Esempio:

    siteroot/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.sys.ini

**Non modificare mai nessun file di lingua core di Joomla! o di terze parti! Qualsiasi modifica apportata verrà persa al prossimo aggiornamento. Se desideri cambiare la formulazione di un qualsiasi elemento di lingua, utilizza il componente formale Override della Lingua.**

Gli overload di lingua sono le tue sostituzioni per le traduzioni delle chiavi di lingua core o dell'estensione. Queste sono traduzioni individuali, una o due, non un intero file! Gli override di lingua per una determinata lingua vengono tutti memorizzati in un unico file:

    siteroot/language/overrides/en-GB.override.ini
    siteroot/language/overrides/fr-FR.override.ini
    siteroot/language/overrides/de-DE.override.ini

    siteroot/administrator/language/overrides/en-GB.override.ini
    siteroot/administrator/language/overrides/fr-FR.override.ini
    siteroot/administrator/language/overrides/de-DE.override.ini

### Ordine di Caricamento della Lingua

Ad ogni caricamento di pagina, le traduzioni della lingua en-GB vengono caricate per prime. Questo assicura che nessuna chiave venga visualizzata dagli utenti del sito. Se è in uso un'altra lingua, le traduzioni per quella lingua vengono caricate successivamente, sostituendo le traduzioni en-GB. Altre lingue tendono a essere più lente nella creazione delle traduzioni rispetto all'en-GB, quindi gli utenti potrebbero occasionalmente vedere parole o frasi in inglese tra quelle della loro lingua.

Infine, le traduzioni vengono caricate dal file override della lingua. Questo permette al sito di utilizzare parole o frasi alternative per adattarsi alle circostanze locali.

## Sostituzioni di Lingua

Occasionalmente, potresti voler sostituire un singolo elemento di lingua tradotta con qualcosa di più adatto alle circostanze locali. Un caso comune è quando crei un override di un template o un layout e desideri aggiungere del contenuto che utilizza una nuova chiave di lingua. Il seguente esempio illustra un caso in cui del testo è stato aggiunto al layout del logout del modulo di login, descritto nell'articolo sui Layout di Template. Il layout alternativo ha questo codice:

```html
<p class="text-center">
La tua sessione scadrà alle <br><?php echo $endTime; ?>
</p>
```

Per un sito multilingue che utilizza inglese, francese e tedesco, il codice deve cambiare:

```html
<p class="text-center">
<?php echo Text::_('TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT')?><br><?php echo $endTime; ?>
</p>
```

Nota: se hai seguito il tutorial sui Layout di Template potresti già avere una chiave TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES che si traduce come Scade. Ma quella viene utilizzata in siteroot/administrator/language/overrides.

Ora la nuova chiave può essere tradotta in ogni lingua. Le traduzioni saranno salvate in siteroot/language/overrides.

- Seleziona **Sistema **→** Pannello di Gestione **→** Sostituzioni di Lingua**
- Seleziona la tua lingua e la posizione del sito.
- Seleziona il pulsante **Nuovo** e compila il modulo. In questo esempio la chiave di lingua è **TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT** e il testo potrebbe essere **La tua sessione scadrà alle**
- Salva & Chiudi il modulo.
- Ripeti il processo di traduzione per ogni lingua.

![form modifica sostituzioni lingue](../../../en/images/languages/language-overrides-edit.png)

Infine, verifica che la traduzione sia stata implementata.

![Risultato Sostituzione nel modulo di login del sito](../../../en/images/languages/language-overrides-custom-logout.png)

*Tradotto da openai.com*

