<!-- Filename: Setting_up_Apache,_PHP_and_MySQL_manually / Display title: Configurare manualmente Apache, PHP e MySQL -->

## Panoramica

Ecco una breve panoramica dei passaggi per configurare Apache, PHP e MySQL in un ambiente Windows e fare riferimento a vari strumenti correlati per mantenere e lavorare con la maggior parte delle attività relative a Joomla!.

Per rendere la guida chiara e concisa, supporremo che ovunque non forniamo istruzioni esplicite, si lasceranno applicare i percorsi di installazione predefiniti senza modifiche.

### Avvertimento

Se hai già installato sul tuo computer qualsiasi pacchetto AMP preconfezionato:

- Sarà difficile tornare al tuo stack AMP. Le varie installazioni che effettueremo di seguito sovrascriveranno i valori del registro e apporteranno modifiche all'ambiente generale. (Questo si applica almeno all'ambiente PC/Windows.)
- Se hai bisogno di mantenere qualsiasi configurazione (Apache, MySQL o PHP) o dati (i tuoi siti web esistenti e database correlati), prima di tentare di seguire queste istruzioni, effettua i backup appropriati.

(necesita di essere ampliato con consigli specifici su come ottenere quanto sopra...)

## Configurazione di MySQL

1.  Scarica il <a href="https://dev.mysql.com/downloads/mysql/" rel="nofollow noreferrer noopener">programma di installazione di MySQL</a> appropriato per la tua piattaforma.
2.  Avvia l'installazione e scegli un percorso di installazione personalizzato.
3.  Procedi con l'intero processo di installazione e fai clic su Fine.
4.  Ti verrà ora presentato il *MySQL Server Instance Configuration Wizard*.
    1.  Assicurati che la *Configurazione Standard* sia selezionata e vai su Avanti.
    2.  Se hai già installato MySQL potresti ricevere il messaggio *Esiste già un servizio Windows con il nome MySQL. Disinstalla questo servizio correttamente o scegli un nome diverso per il nuovo servizio.* In tal caso, scegli un nome di servizio alternativo.
    3.  Nella finestra successiva controlla l'opzione *Includi la directory Bin nel PATH di Windows*. Facendo ciò potrai accedere alle varie utilità di MySQL dalla riga di comando.
    4.  Nella finestra successiva potrai creare una password per il tuo utente root di MySQL, l'utente con il livello di accesso più alto sul tuo server.
    5.  Nella finestra finale tutte le modifiche che hai configurato finora verranno salvate quando premi il pulsante *Esegui* e il servizio windows per questa istanza verrà avviato.

### Note

1.  Per rendere l'istruzione il più accessibile possibile, abbiamo omesso diversi scenari di configurazione della tua istanza MySQL, come la possibilità di spostare i tuoi file di database.
2.  MySQL si installa di default con una modalità STRICT che potrebbe causare alcuni errori quando si utilizzano estensioni o applicazioni che non l'hanno considerata.

### Risorse MySQL

- <a href="https://www.heidisql.com/" class="external text" rel="nofollow noreferrer noopener">HeidiSQL</a> Un sostituto completo e facile da usare per phpMyAdmin sotto costante sviluppo.
- <a href="https://dev.mysql.com/downloads/workbench/" class="external text" rel="nofollow noreferrer noopener">MySQL Workbench</a> Vari strumenti tra cui apprezzerai l'Administrator, che ti aiuta a configurare la tua istanza di MySQL. Richiede il <a href="https://dotnet.microsoft.com/en-us/" class="external text" rel="nofollow noreferrer noopener">framework .Net</a>.
- <a href="https://www.phpmyadmin.net/" class="external text" rel="nofollow noreferrer noopener">phpMyAdmin</a> Un potente client web per MySQL per amministrare tutto ciò che riguarda MySQL.
- <a href="https://dev.mysql.com/doc/" class="external text" rel="nofollow noreferrer noopener">Documentazione MySQL</a>

## Configurazione di Apache

1.  <a href="https://httpd.apache.org/download.cgi" class="external text"
     rel="nofollow noreferrer noopener">Scarica il
    programma di installazione</a> di tua preferenza.
2.  Esegui la procedura guidata di installazione e clicca attraverso ogni step fino a raggiungere
    la finestra di Informazioni del Server. Inserisci le opzioni seguenti rispettivamente
    e nell'ordine dato in ciascuno dei campi, a meno che tu non abbia particolari requisiti su come configurare il tuo server web:
    1.  localhost,
    2.  localhost e
    3.  admin@localhost
3.  Prosegui con la procedura guidata che installerà e avvierà il server web Apache
    come servizio di Windows.
4.  Nella barra di stato di Windows vedrai ora una piuma color rosa
    con un pulsante di riproduzione verde che indica che Apache è attivo e
    funzionante. Punta il tuo browser su
    <a href="http://localhost/"
    rel="nofollow noreferrer noopener">http://localhost/</a> e dovresti
    vedere una pagina che indica il suo funzionamento.
5.  Andiamo ora nella posizione in cui Apache è installato che
    comunemente si trova in *C:\Program Files\Apache Software
    Foundation\Apache2.2* ed esploriamo le varie directory
    1.  *bin* - contiene i vari file binari alcuni dei quali sono
        elencati di seguito. Per accedere a queste applicazioni, la maggior parte delle quali basate su comando, dobbiamo aggiungere il percorso alla directory *bin* nella nostra variabile globale PATH. Per farlo, fai clic destro su Il mio computer \> Proprietà \> Avanzate \> Variabili d'ambiente e nell'elenco delle Variabili di Sistema trova e seleziona la
        Variabile PATH e fai clic su Modifica e aggiungi un punto e virgola finale,
        se non è già presente, seguito dal percorso assoluto della tua directory bin. Esci dalla finestra Proprietà di sistema accettando.
        1.  *httpd.exe* che è il server web Apache stesso, che si divide in diversi processi figli mentre gestisce tutte le simultanee richieste dei clienti in entrata come richiesto dalla direttiva MaxClients;
        2.  *ab.exe* è uno strumento di benchmarking che viene fornito con Apache
            permettendoti di vedere quanto bene la tua applicazione può performare
            per unità di tempo
    2.  *conf* - cartella in cui si trovano vari file di configurazione di
        cui i seguenti sono di maggiore interesse nel nostro caso
        1.  *httpd.conf* - la maggior parte delle direttive del server si trova in
            questo file e per un facile accesso dovresti associare il
            tipo di file *.conf* con un editor user-friendly, ossia qualsiasi cosa
            diversa dal Blocco Note predefinito.
        2.  *extra\httpd-vhosts.conf* - contiene direttive che permetterebbero
            di utilizzare il tuo server locale come host virtuale, ossia capace
            di gestire diversi server sul tuo PC. Uno scenario d'uso è quello
            che durante una fase di sviluppo se vuoi mappare l'effettivo dominio
            per cui stai lavorando sulla tua copia locale, potresti farlo con
            leggere modifiche in questo file. Ne discuteremo in maggiore dettaglio di seguito.
    3.  *htdocs* - la radice predefinita del server web, qui è dove
        <a href="http://localhost/"
        rel="nofollow noreferrer noopener">http://localhost/</a> è
        mappato, ossia se non lo riconfiguri in *httpd.conf* sopra.
    4.  *logs* - registri di accesso e di errore, quando si cerca di risolvere vari
        problemi relativi al tuo server o persino alla tua applicazione

### Risorse di Apache

- La
  <a href="https://httpd.apache.org/docs/current/" class="external text"
   rel="nofollow noreferrer noopener">documentazione di riferimento di Apache</a>

## Configurazione di PHP

1.  <a href="https://windows.php.net/download/" class="external text"
     rel="nofollow noreferrer noopener">Scarica PHP</a>
    e scegli comunemente VC6 x86 Thread Safe in formato Zip. Le varie
    opzioni riguardano il modo in cui il codice base di PHP è stato compilato in binario
    e probabilmente non è qualcosa di cui dovresti preoccuparti per ora.
2.  Crea una cartella sotto C:\Program Files\\ (o ovunque si trovi la tua
    directory dei programmi) e chiamala PHP.
3.  Trova il file Zip scaricato e spostalo nella cartella appena creata
    e scompattalo direttamente nella cartella.
4.  Aggiungiamo ora il percorso di PHP al nostro PATH globale seguendo
    le istruzioni sopra.

### Configurare PHP

La configurazione consiste nell'editare il file *php.ini*. Un file di esempio
per diversi scenari è già presente nella tua cartella PHP. Rinominiamo
*php.ini-development* in *php.ini* e apriamolo nel tuo editor di testo preferito. I valori comuni da modificare sono i seguenti e tutte queste
variabili sono ben documentate nel file *php.ini*. (Nota che si tratta di
una impostazione a livello di server che si applica a tutti i tuoi progetti):

- *max_execution_time* - quando hai script che girano troppo a lungo
  e il server restituisce vari risultati inaspettati che pensi sia
  dovuto a non poter completare l'intero processo
- *memory_limit*
- *error_reporting*
- *display_errors*
- *log_errors* - una variabile di cui dovresti prendere nota negli scenari di produzione
- *upload_tmp_dir*
- *upload_max_filesize*
- *extension_dir* - per evitare complicazioni, indicheremo la directory in cui si trovano le seguenti estensioni
  commentando questa variabile e assegnando la posizione assoluta della
  cartella. La linea completa dovrebbe essere la seguente:
    extension_dir = "C:\Program Files\PHP\ext"

- La sezione delle estensioni dinamiche contiene vari moduli aggiuntivi che
  vuoi caricare con, e quelli commentati sono quelli che vengono
  preconfezionati con PHP e si trovano nella directory *ext* nella tua
  cartella PHP. Se vuoi attivarne qualcuno, basta rimuovere il commento
  come devi fare con le seguenti estensioni:
  - php_curl.dll
  - php_gd2.dll
  - php_mbstring.dll
  - php_mysql.dll
  - php_mysqli.dll
  - php_pdo.dll
  - php_pdo_mysql.dll
  - php_xsl.dll
- session.save_path

### Configurare Apache per funzionare con PHP

Ora che abbiamo configurato PHP per funzionare come vogliamo, passiamo ad
Apache e facciamo lo stesso.

- Apri *httpd.conf* e nella sezione "Dynamic Shared Object (DSO) Support"
  aggiungi le seguenti direttive. (Se hai posizionato la tua cartella PHP
  diversamente, fai le modifiche corrispondenti per php5apache2_2.dll
  qui sotto.):
    LoadModule php5_module "C:/Program Files/PHP/php5apache2_2.dll"
    AddType application/x-httpd-php .php

- Nella DirectoryIndex aggiungi *index.php* e *index.htm* come possibili
  file da servire quando viene richiesta la directory come segue:
    DirectoryIndex index.html index.htm index.php

- Alla fine del file aggiungi la seguente linea che indicherà dove si trova
  il file *php.ini*:
    PHPIniDir "C:/Program Files/PHP"

### Riavviare e testare PHP

Appena fai qualsiasi modifica a *php.ini*, *httpd.conf* o a qualsiasi altro
file di configurazione, devi riavviare Apache per vedere l'effetto delle
modifiche. Quindi ora riavviamo Apache utilizzando lo strumento Apache Monitor
che puoi trovare nella barra di stato di Windows. Si spera che non ti vengano
mostrate finestre di dialogo e che Apache Monitor continui a funzionare
verde.

Adesso testeremo che PHP stia funzionando. Vai alla root del documento del tuo web server (nel caso predefinito *C:\Program Files\Apache Software
Foundation\Apache2.2\htdocs*) e aggiungi un file chiamato *phpinfo.php* con
il seguente contenuto:


Questo renderà una pagina contenente informazioni sulla tua configurazione PHP
e sui vari moduli/estensioni attualmente caricati. Punta il tuo browser su
<a href="http://localhost/phpinfo.php"

rel="nofollow noreferrer noopener">http://localhost/phpinfo.php</a>.

### Installare e configurare *xdebug*

1.  Punta il tuo browser su
    <a href="https://xdebug.org/wizard" class="external text"
     rel="nofollow noreferrer noopener">Wizard di Installazione Xdebug</a>.
    Questa pagina ti assisterà a trovare una versione adatta di Xdebug.
2.  Copia l'intera pagina della pagina *phpinfo* che abbiamo eseguito sopra e incollala
    nell'area di testo e segui le istruzioni fornite per l'installazione.

### Risorse XDebug

- Il <a href="https://www.php.net/docs.php" class="external text"
   rel="nofollow noreferrer noopener">Manuale PHP</a>
  Ottima documentazione aggiornata con commenti aggiuntivi preziosi dagli utenti.
  Sono disponibili versioni scaricabili.
- La
  <a href="https://xdebug.org/docs/" class="external text"
  rel="nofollow noreferrer noopener">Documentazione Xdebug 3</a>

