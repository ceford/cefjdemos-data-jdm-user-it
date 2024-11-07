<!-- Filename: jdocmanual?manual=user&heading=help&filename=administrator-help.md / Display title: Guida per l'Amministratore   -->

## Introduzione

Quasi tutte le pagine dell'amministratore di Joomla hanno una barra degli strumenti contenente un pulsante **Aiuto** vicino alla parte superiore destra della pagina. Solo i cruscotti non hanno una barra degli strumenti e quindi un pulsante Aiuto.

Molte pagine hanno anche un pulsante etichettato **Toggle Inline Help**.
Questo visualizza o nasconde semplicemente una descrizione del campo, se disponibile. Il suo scopo è ridurre il disordine ma fornire un meccanismo di promemoria dove questo sarebbe utile. Non viene ulteriormente trattato qui.

Il pulsante **Aiuto** attiva l'apertura di una nuova finestra usando un URL incorporato nel pulsante. Un esempio:
```
data-url="https://help.joomla.org/proxy/index.php?keyref=Help51:Articles&lang=en"
```
In questo caso, il contenuto della pagina di aiuto proviene da una fonte esterna.

## La Fonte di Aiuto - un sito MediaWiki

MediaWiki è il software utilizzato da WikiPedia. È un pacchetto di software libero e open source (FOSS) che utilizza PHP e MySQL, proprio come Joomla. Puoi scaricarlo e installarlo da solo. In teoria, potresti creare il tuo server di aiuto e usarlo al posto del server di aiuto comune di Joomla. In pratica, devi sapere che le pagine di MediaWiki necessitano di un po' di elaborazione per renderle adatte alla visualizzazione come pagine di aiuto.

Qui entra in gioco il **proxy**. Recupera la pagina richiesta dall'installazione di MediaWiki e la prepara per essere visualizzata come pagina di aiuto. Puoi vedere una pagina originale di MediaWiki in questo esempio su https://docs.joomla.org/Help5.x:Articles e puoi modificarla se vedi qualcosa di sbagliato.

## L'URL di Aiuto Globale

Il file **configuration.php** nella radice di un'installazione Joomla contiene una variabile `$helpurl`:

```
$helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}&lang={langcode}';
```

Quando viene selezionato un pulsante di Aiuto, ciascuno degli elementi tra parentesi graffe viene sostituito. I valori {major} e {minor} sono le impostazioni di versione per la tua installazione. Il {langcode} è il codice della lingua attualmente selezionata per l'Amministratore, che potrebbe essere en, de o fr.

La variabile {keyref} è il nome del file di una pagina sul server di Aiuto, meno il suo namespace. Quindi, per la pagina Articoli, il nome del file rilevante è *Articles*.

**Nota:** `https://docs.joomla.org/` è il sito per modificare le pagine di Aiuto. Ma `https://help.joomla.org/proxy` è il sito per recuperare le pagine di Aiuto.

Non è prevista alcuna opzione per modificare l'URL del server di Aiuto predefinito all'interno dei moduli di Configurazione Globale dell'Amministratore, ma puoi cambiarlo con un editor di testo.

L'elenco completo dei codici di sostituzione disponibili è:

| Codice        | Verrà sostituito da                                                           |
|---------------|--------------------------------------------------------------------------------|
| {app}         | Nome dell'applicazione (ad esempio "Administrator" nel back-end di Joomla CMS) |
| {component}   | Nome del componente (ad esempio "com_content" nel Gestore Articoli)            |
| {keyref}      | Riferimento chiave dello schermo di aiuto (dopo il passaggio attraverso il sistema di traduzione) |
| {major}       | Numero di revisione principale di Joomla (ad esempio "5" in Joomla 5.6)         |
| {minor}       | Numero di revisione minore di Joomla (ad esempio "1" in Joomla 5.1)             |
| {maintenance} | Numero di revisione di manutenzione di Joomla (ad esempio "3" in Joomla 5.1.1)  |
| {language}    | Codice completo della lingua (ad esempio "en-GB")                               |
| {langcode}    | Parte del tag della lingua del codice lingua (ad esempio "en" se il codice completo è "en-GB") |
| {langregion}  | Parte del tag della regione del codice lingua (ad esempio "GB" se il codice completo è "en-GB") |

## Aiuto Globale nel Futuro

L'uso di un sito MediaWiki per la fornitura delle pagine di aiuto è in qualche modo un
peso per coloro che mantengono la documentazione e la procedura potrebbe cambiare in
futuro. Se ci sarà un cambiamento, è probabile che la fonte consisterà in
file HTML precompilati accessibili con una semplice modifica del dominio sorgente $helpurl.

## Assistenza Locale per Componenti Personalizzati

Se hai un componente personalizzato e ti senti a tuo agio con la modifica del codice sorgente PHP e la creazione di contenuti, puoi creare le tue pagine di aiuto individuali. Prendi il componente Jdocmanual come esempio. Come componente personalizzato, non ci sono pagine di aiuto sul sito MediaWiki di docs.joomla.org. I componenti di terze parti non sono autorizzati a fornire pagine di aiuto da lì.

Dai un'occhiata a questo frammento di codice da administrator/components/com_jdocmanual/src/View/Manual/ViewHtml.php:
```
        $tmpl = $app->input->getCmd('tmpl');
        if ($tmpl !== 'component') {
            ToolbarHelper::help('jdocmanual', true);
        }
```
La specifica della chiamata ToolbarHelper::help è la seguente:
```
@param $ref: Il nome del file di destinazione (escludendo l'estensione del file).
@param $useComponent: Utilizza il file di aiuto nella directory del componente.
@param $url: Utilizza questo URL invece di qualsiasi altro.
@param $component: Nome del componente per ottenere Aiuto (null per il componente corrente)
function Toolbar::help(
    string $ref,
    bool $useComponent = false,
    string $url = null,
    string $component = null
): HelpButton
Scrive un pulsante di aiuto per un'opzione data (apre una finestra popup).
```
In questo esempio **$ref** è un nome di file da utilizzare, in questo caso `'jdocmanual'` (deve corrispondere al maiuscolo/minuscolo del file di destinazione) e **$useComponent** è `true`, il che significa che la pagina di aiuto da utilizzare sarà situata all'interno dei file del componente in administrator/component/com_jdocmanual/help/en-GB/jdocmanual.html

Utilizzare un file di aiuto all'interno del componente dovrebbe significare che l'aiuto non manca mai e forse è sempre aggiornato.

## Aiuto da Remoto per Componente Personalizzato

Nel creare il pulsante di Aiuto, puoi impostare $useComponent = false e impostare
l'URL per puntare a una posizione specifica sul tuo sito o su un sito remoto.

```
    ToolbarHelper::help('jdocmanual', false, 'http://example.com/help/it-IT/jdocmanual.html');
```

Quindi, tutto ciò che serve è una pagina HTML con il nome corretto nel posto giusto.

*Tradotto da openai.com*  

