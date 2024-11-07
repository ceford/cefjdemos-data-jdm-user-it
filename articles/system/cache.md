<!-- Filename: Cache / Display title: Cache  -->

## Per Amministratori

Come amministratore, Joomla ti offre la possibilità di memorizzare nella cache parti del tuo sito. Puoi scegliere di memorizzare nella cache intere pagine web o solo parti di quelle pagine. Questa guida spiega come fare.

Su una pagina web di un sito Joomla ci sono 3 elementi che possono essere memorizzati nella cache:

1. L'intera pagina stessa – la cache della Pagina
2. L'output del componente Joomla per quella pagina web – noto come cache della Vista
3. L'output dei moduli mostrati su quella pagina – noto come cache del Modulo

Hai a disposizione diverse impostazioni di cache che ti consentono di controllare cosa viene memorizzato nella cache:

1. Il plugin di sistema "Sistema – Cache della Pagina"
2. La Configurazione Globale, scheda Sistema, Impostazioni della Cache. Qui l'opzione Cache di Sistema può essere impostata su
   - OFF – Cache disabilitata
   - ON – Cache conservativa
   - ON – Cache progressiva
3. Molti moduli nelle loro opzioni hanno una scheda Avanzate in cui la Cache può essere impostata su *Usa globale* o *Nessuna cache*

Come descritto di seguito, ci sono anche regole per la memorizzazione nella cache che sono implementate all'interno del codice di Joomla e sulle quali non hai controllo.

Puoi svuotare la cache attraverso la selezione del menu Amministratore → Sistema → Svuota Cache. In generale, puoi considerare Joomla come avente 3 livelli di cache, che aumentano in aggressività:

1. Cache conservativa
2. Cache progressiva
3. Cache della Pagina

Inoltre, gli sviluppatori di Joomla possono utilizzare le funzionalità di cache per memorizzare il risultato delle query al database, ad esempio, per aumentare la reattività del sito, ma questo è al di fuori dell'ambito delle capacità degli Amministratori.  

## Memorizzazione nella Cache delle Pagine

Per attivare questa funzione, vai su Amministratore → Estensioni → Plugin. Trova quindi il plugin Sistema – Cache Pagina e abilitalo. Ciò significa che le pagine del sito ora saranno memorizzate nella cache e, ogni volta che vengono richieste di nuovo, verrà servita la pagina memorizzata nella cache anziché essere generata da Joomla a partire dalle informazioni nel database. La pagina memorizzata nella cache continuerà a essere servita fino alla sua scadenza, come definito dal parametro *Tempo di Cache* nella scheda Amministratore → Configurazione Globale → Sistema → Impostazioni Cache.

Se stai leggendo questa pagina come un tutorial e vuoi testare la memorizzazione nella cache delle pagine, è meglio impostare le opzioni di cache della Configurazione Globale su:

- Gestore della Cache – File
- Percorso della Cartella Cache – lascia vuoto
- Tempo di Cache – 15 (il valore predefinito di 15 minuti)
- Caching Specifico della Piattaforma - No
- Cache del Sistema – OFF – Caching disabilitato

Per verificare che la memorizzazione nella cache delle pagine stia funzionando, vai su una pagina del sito web che mostra un articolo. Dopo aver visualizzato quella pagina, dovresti trovare nel file system una directory `cache/page` con un file al suo interno con un nome file simile a `xxx-cache-page-yyy.php`, dove xxx e yyy sono lunghe stringhe hash. Joomla deve memorizzare nella cache pagine separate per URL separati, quindi la seconda stringa di cifre esadecimali è un hash dell'URL della pagina web del sito, per rendere univoco il nome di quel file.

Utilizza quindi la funzionalità Amministratore per modificare il testo di quell'articolo e ridisplaya la pagina web del sito. Dovresti trovare la versione memorizzata nella cache, non il tuo testo modificato.

Modificare un articolo (o un altro elemento Joomla) non cancella la cache della pagina per la/e pagina/e web in cui quell'articolo è visualizzato. Per cancellare la cache della pagina, vai su Amministratore → Sistema → Cancella Cache. Fai clic sulla casella di controllo accanto al *Gruppo di Cache* chiamato "page" e premi il pulsante Elimina. Quando visualizzerai di nuovo la tua pagina web, dovrebbe ora mostrare il tuo testo modificato.

Se il tuo sito ha una funzione come un carrello della spesa, applicare la memorizzazione nella cache delle pagine causerà problemi, poiché le pagine devono mostrare ciò che il cliente ha già selezionato, piuttosto che visualizzare una pagina memorizzata nella cache che è comune a tutti. Tuttavia, puoi configurare il plugin Sistema - Cache Pagina per escludere dalla cache voci di menu specificate o URL e intervalli di URL specificati (nella scheda Avanzate), in modo che solo le pagine veramente statiche siano memorizzate nella cache.

## Caching Conservativo

Con il Caching Conservativo puoi memorizzare nella cache l'output delle viste dai componenti e l'output dei moduli che consentono il caching. Tuttavia, tieni presente che questo funzionerà solo sulle pagine che non sono memorizzate nella cache usando la Cache di Pagina. Per quelle pagine, l'intera pagina web è memorizzata nella cache e il Caching Conservativo non è nemmeno considerato.

Per attivare il Caching Conservativo:

1. Vai su Amministratore → Sistema → Configurazione Globale → Scheda Sistema e, all'interno delle Impostazioni della Cache, imposta la Cache di Sistema su ON – Caching conservativo.
2. Vai su Amministratore → Estensioni → Moduli e seleziona i moduli che desideri memorizzare nella cache. Se quel modulo consente il caching, allora nella scheda Avanzato dovresti poter impostare la Cache su:

- Usa Globale – questo modulo sarà memorizzato nella cache (con l'opzione Globale ora impostata su caching Conservativo)
- Nessun caching – questo modulo non sarà memorizzato nella cache.

(Nota che il Tempo di Cache nella Configurazione Globale è in minuti, ma il Tempo di Cache nelle impostazioni del Modulo è in secondi.)

Per verificare che funzioni, vai sul tuo sito, **assicura di essere disconnesso**, e naviga verso una pagina web che visualizza un articolo. Controlla il tuo file system e dovresti trovare una cartella `cache/com_content` contenente un file di cache.

Troverai anche altre directory come `cache/com_languages` (poiché la visualizzazione della pagina comporta il caricamento della lingua corrente, che sarà memorizzata anche nella cache) e anche directory relative alla cache dei moduli, ad esempio `cache/com_modules`. Questi sono il risultato dell'uso della cache che gli sviluppatori hanno codificato all'interno dell'applicazione Joomla.

Se modifichi e salvi quell'articolo, quindi aggiorni la pagina del sito, scoprirai che il sito visualizza il testo aggiornato. Ciò è dovuto al fatto che ogni volta che l'editazione viene salvata, Joomla cancella la cache per quell'articolo.

Tuttavia, puoi dimostrare che la cache funziona se modifichi il file di cache nella directory `cache/com_content` utilizzando un editor di testo di base. Utilizzando l'editor, cambia una lettera nel testo dell'articolo nel file di cache e salva il file. Poi, quando aggiorni la pagina web, dovresti vedere la modifica che hai apportato al file di cache.

Come puoi selezionare quali viste dei componenti vengano memorizzate nella cache e in quali circostanze? Ahimè, non puoi farlo. Questo è determinato dagli sviluppatori del componente core di Joomla e codificato nel codice PHP del componente. I criteri sono diversi per ogni componente. Tuttavia, puoi facilmente scoprire quali criteri sono utilizzati perché per ciascuno dei componenti del sito sono codificati nel file `DisplayController.php` del sito. Ad esempio, nel momento di questa revisione (Joomla versione 5) per il componente Contatti troviamo in `components/com_contact/src/Controller/DisplayController.php`

```php
    public function display($cachable = false, $urlparams = [])
    {
        if ($this->app->getUserState('com_contact.contact.data') === null) {
            $cachable = true;
        }
```

Questo significa che le viste associate con i contatti saranno memorizzabili a meno che non ci siano dati di sessione indicizzati da com_contact.contact.data – che sarà il caso se nella sessione utente l'utente ha visualizzato un modulo di contatto (ad esempio su una pagina a cui punta un elemento di menu di tipo Contatti → Contatto Singolo).

Il file equivalente per articoli `components/com_content/src/Controller/DisplayController.php` contiene:

```php
    public function display($cachable = false, $urlparams = false)
    {
        $cachable = true;

        /**
         * Imposta il nome della vista predefinita e il formato dalla Richiesta.
         * Nota che stiamo usando a_id per evitare collisioni con il router e la pagina di ritorno.
         * Il frontend è un po' più complesso rispetto al backend.
         */
        $id    = $this->input->getInt('a_id');
        $vName = $this->input->getCmd('view', 'categories');
        $this->input->set('view', $vName);

        $user = $this->app->getIdentity();

        if (
            $user->get('id')
            || ($this->input->getMethod() === 'POST'
            && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive'))
        ) {
            $cachable = false;
        }
```

L'espressione `$user->get('id')` è vera se si tratta di un utente registrato. Ciò significa che gli articoli non vengono mai memorizzati nella cache per gli utenti connessi. Le espressioni successive si riferiscono ad altre condizioni in cui il caching non viene effettuato, anche se l'utente non è connesso.

In questo modo puoi scoprire le circostanze in cui viene eseguito il caching, ma cambiarle non è consigliabile. Puoi anche dimostrare che i moduli vengono memorizzati nella cache utilizzando il modulo Joomla Breadcrumbs, assicurandoti che sia visualizzato in una posizione di modulo sulla pagina web, impostando la sua opzione Caching e modificando manualmente il file di cache in `cache/mod_breadcrumbs`.

## Cache Progressiva

Come la Cache Conservativa, anche la Cache Progressiva memorizza nella cache l'output delle viste dei componenti e dei moduli. La differenza funzionale tra le due è che con la Cache Progressiva **per gli utenti disconnessi tutti i moduli sono sempre memorizzati nella cache**. In questo caso, impostare l'opzione *Nessuna Cache* per un modulo non ha effetto. Se l'opzione di archiviazione della cache è impostata su *File*, puoi trovare il file di cache dei moduli (l'output di tutti i moduli è memorizzato all'interno dello stesso file) nella directory `cache/com_modules`.

Per attivare la Cache Progressiva, vai su Amministratore → Sistema → Configurazione Globale → scheda Sistema e all'interno delle *Impostazioni Cache* imposta *Cache di Sistema* su *ON – Cache progressiva*.

Per quanto riguarda le condizioni per la memorizzazione nella cache delle viste dei componenti core di Joomla, **non c'è differenza tra cache conservativa e progressiva**. Nonostante quello che potresti leggere su alcuni siti web e nelle risposte alle domande di Stack Overflow, non è vero che la Cache Conservativa si riferisce a quando l'utente non è connesso e la Cache Progressiva a quando l'utente è connesso.

## Riassunto

Di seguito è riportato un riassunto dei tipi di caching.

### Caching dell'intera pagina

- **Configurazione**: Plugin integrato (Amministratore → Estensioni →
  Gestore Plugin → Sistema - Cache della pagina)
- **Cache**: ogni intera pagina del tuo sito
- **Basato su**: URL
- **Maggiori informazioni**:
  - Caching opzionale del browser: memorizza anche nella cache il browser/computer dei tuoi visitatori
  - Memorizza nella cache solo le pagine per i visitatori ospiti (non per i visitatori connessi).
    Presta attenzione all'uso di questo plugin se hai un sito interattivo in cui vuoi servire contenuti basati su informazioni di sessione/cookie piuttosto che solo sull'URL semplice. Funzionalità come un carrello della spesa non funzioneranno.

### Caching delle viste

- **Configurazione**: Configurazione Globale → Cache
- **Cache**: ogni vista di un componente
- **Basato su**: URL, vista, parametri, ...
- **Maggiori informazioni**: Gli sviluppatori di componenti devono includere questo nel loro codice per farlo funzionare. Nella maggior parte dei casi ciò non viene fatto. Il componente principale dei contenuti di Joomla lo utilizza, ma solo per i visitatori ospiti del tuo sito, anche se non è obbligatorio per ogni componente.

### Caching dei moduli

- **Configurazione**: Configurazione Globale → Cache
- **Cache**: ogni modulo (personalizzato singolarmente tramite i Parametri Avanzati di ciascun modulo)
- **Basato su**: l'ID del modulo, i livelli di visualizzazione dell'utente e il parametro *Itemid* nella richiesta HTTP
- **Maggiori informazioni**: È necessario disabilitarlo su alcuni moduli per evitare problemi

### Ulteriore Caching

Se desideri esplorare altri sistemi di cache e possibilità, potresti voler consultare le estensioni di terze parti relative al caching.

### Motori di caching o archiviazione

- **Configurazione**: Configurazione Globale → Cache

Qui puoi scegliere quale sistema vuoi che il tuo sito utilizzi per tutte
le memorie cache. Alcune opzioni sono: APC, Eaccelorator, File, Memcache, Redis, XCache.

APC, ad esempio, memorizza anche nella cache il tuo opcode PHP.

## Per Sviluppatori

<div class="alert alert-warning">
Questa sezione necessita di una revisione per Joomla! 4/5.
</div>

La classe **JCache** permette molti tipi e livelli diversi di
caching. Le seguenti sottoclassi sono realizzate specificamente, ma puoi
aggiungerne altre tue, o utilizzare quella principale in molti modi
diversi.

Non dimenticare che il primo livello di cache incontrato sovrascriverà
qualsiasi caching più profondo. Suppongo che troppi livelli siano anche
controproducenti (*da verificare comunque*).

- **JCacheView** memorizza nella cache e restituisce l'output di una
  vista specifica (in MVC). Un id cache viene generato automaticamente
  dall'URI, vista specifica e dal suo metodo specifico, oppure puoi
  dare il tuo.

Questo può essere fatto automaticamente tramite la funzione display del
controller di base. Per esempio nel controller del tuo componente:

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true chiede caching.
        }
    }

Ci sono anche alcuni urlparams da considerare. Controlla questo
[Joomla StackExchange](http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000 "")

Inoltre, sii consapevole che eventuali aggiornamenti (come hit o conteggi di visite)
NON saranno aggiornati (a meno che non aggiungi questo al di fuori di
questo metodo e quindi in qualsiasi parte più profonda dell'MVC.)

- **JCachePage** memorizza nella cache e restituisce il corpo della
  pagina.
- **JCacheCallback** memorizza nella cache e restituisce l'output e i
  risultati di funzioni o metodi.

Se desideri memorizzare nella cache le query, questa è una buona classe
per farlo, come illustrato qui: Utilizzare la cache per velocizzare il
codice

- **JCacheOutput** memorizza nella cache e restituisce l'output.

Questo è piuttosto destinato alla memorizzazione nella cache di una
parte specifica del codice PHP. Agisce come un buffer di output, ma
memorizzato nella cache.

*Tradotto da openai.com*

