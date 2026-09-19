<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Laragon per Windows",
    "description": " ",
    "author": ""
}
-->

## Configurazione di un ambiente Joomla locale usando Laragon

Laragon è uno strumento leggero per Windows che gestisce Apache, MySQL e
PHP con una semplice installazione. Nessun file di configurazione, nessuna
configurazione manuale: basta scaricare, eseguire e iniziare a creare/testare
Joomla. Leggi questo articolo sul Joomla Community Magazine: [Laragon: il
server AMP semplice e ad alte prestazioni per Windows](https://magazine.joomla.org/all-issues/october-2025/laragon-the-effortless,-high-performance-amp-server-for-windows).

Questa guida ti porta da zero a un sito Joomla locale funzionante e
illustra anche una piccola particolarità dell'interfaccia nell'ultima
versione, facile da risolvere una volta capito cosa sta succedendo.

### Download e installazione di Laragon

Per iniziare, visita la [pagina di download di Laragon](https://laragon.org/download) ufficiale. Scarica la versione Laragon Full (attualmente la v8.6.1), poiché include tutto ciò di cui hai bisogno (come Apache, MySQL e le versioni più recenti di PHP) già pronto all'uso.
In alternativa, puoi scaricare direttamente il [programma di installazione](https://github.com/leokhoa/laragon/releases/download/8.6.1/laragon-wamp.exe).

Una volta scaricato il file `.exe`, fai doppio clic su di esso per iniziare l'installazione.

**Nota su Windows Defender:** poiché Laragon è un potente strumento per sviluppatori, Windows Defender SmartScreen potrebbe impedirne l'avvio e mostrare una schermata di avviso blu. È normale: fai semplicemente clic su **Ulteriori informazioni**, quindi fai clic sul pulsante **Esegui comunque** visualizzato in fondo.

![avviso di protezione della configurazione di Laragon su Windows](../../../en/images/hosting-local/laragon-setup-windows/01-laragon-setup-windows-protected-warning.png)

Prosegui con la procedura guidata di configurazione. Le impostazioni predefinite vanno perfettamente bene,
ma presta attenzione a questi due dettagli importanti:

1.  **Percorso di destinazione:** lascia la cartella di installazione su
    `C:\laragon`. Installarlo in profondità all'interno di `Program Files` o
    `Documenti` può talvolta causare problemi di autorizzazioni in seguito.
2.  **Opzioni di configurazione:** assicurati che la casella **Host virtuali
    automatici** sia selezionata. Questa è la funzionalità che assegna al tuo
    sito Joomla locale un indirizzo intuitivo (come `http://myjoomla.test`)
    invece di un indirizzo IP grezzo.

![opzioni di configurazione di laragon](../../../en/images/hosting-local/laragon-setup-windows/02-laragon-setup-options.jpg)

Al termine dell'installazione, riavvia il computer. (la procedura guidata di
installazione ti chiederà di fare lo stesso)

### Avviare il server e configurare le autorizzazioni del firewall

Apri Laragon dal menu Start e fai clic sul pulsante **Avvia tutto**.

Poiché è la prima volta che esegui un server locale, Windows deve
verificare che sia sicuro. Verranno visualizzate finestre a comparsa di
Windows Defender Firewall che richiedono l'accesso alla rete per servizi
come **Apache HTTP Server**, **MySQL** e **Mailpit**.

- Fai semplicemente clic su **Consenti accesso** in ciascuna di queste finestre.

Una volta concesso l'accesso, Laragon avvierà il tuo ambiente locale. Capirai
che funziona quando vedrai comparire i numeri delle porte di Apache e MySQL
nella finestra di Laragon.

### Il problema di "Già in esecuzione" (e come risolverlo)

Quando hai finito di lavorare, potresti fare clic su "Arresta tutto" per
spegnere Apache e MySQL, quindi fare clic sulla "X" nell'angolo in alto a
destra per chiudere la finestra di Laragon.

Ecco il problema: fare clic sulla "X" non arresta completamente Laragon.
Continua a essere eseguito silenziosamente in background. Se provi ad aprire
nuovamente l'app Laragon dal menu Start o dal desktop, nell'angolo in basso a
destra dello schermo verrà visualizzato un avviso giallo con il messaggio:
**"Laragon è già in esecuzione!"**

![notifica di Laragon già in esecuzione durante la configurazione](../../../en/images/hosting-local/laragon-setup-windows/03-laragon-setup-already-running-notice.png)

**La trappola:** Se fai clic sulla "X" di quel piccolo avviso giallo per chiuderlo, anche la finestra principale di Laragon scomparirà, rendendoti completamente impossibile accedere al pannello di controllo. (Nota: occasionalmente potrebbe anche comparire un pop-up relativo alla licenza che fa bloccare l'interfaccia in modo simile).

**La soluzione:** Se l'interfaccia scompare o si blocca, devi semplicemente 恒一
forza la chiusura del processo in background e riparti da zero. È molto semplice:

1.  Premi `Ctrl + Shift + Esc` sulla tastiera per aprire **Gestione attività di
    Windows**.
2.  Cerca **Laragon** nell'elenco dei processi in esecuzione.
3.  Fai clic con il pulsante destro del mouse su di esso e seleziona
    **Termina attività**.

Tutto qui! Hai terminato in sicurezza il processo in background bloccato. Ora puoi
aprire Laragon dal menu Start e verrà caricato perfettamente, consentendoti di
fare clic su "Avvia tutto" senza errori.

### Gestione dei pop-up della licenza (le schermate di "sollecito")

Laragon è gratuito per lo sviluppo e i test non commerciali
senza acquistare una licenza. Tuttavia, dopo aver utilizzato l'app per un po'
di tempo, è probabile che venga visualizzato un messaggio "Chiave di licenza"
che invita a sostenere il progetto.

Poiché stai utilizzando la versione gratuita, puoi semplicemente chiudere
queste schermate, ma è prevista una sequenza specifica:

1.  La finestra principale **Chiave di licenza** apparirà sopra
    l'interfaccia di Laragon. Fai clic sul testo **Chiudi** o sulla "X".<br>
    ![finestra della chiave di licenza della configurazione di laragon](../../../en/images/hosting-local/laragon-setup-windows/04-laragon-setup-license-key-window.png)
2.  Subito dopo averla chiusa, apparirà un secondo pop-up di **Avviso**,
    che ti ricorderà che Laragon è in esecuzione senza licenza.
    Fai clic su **OK** o sulla "X".<br>
    ![avviso di assenza di licenza della configurazione di laragon](../../../en/images/hosting-local/laragon-setup-windows/05-laragon-setup-no-license-warning.png)
3.  Dopo aver chiuso il secondo avviso, Laragon potrebbe aprire automaticamente
    il tuo browser web e reindirizzarti a `https://laragon.org/key`. Puoi
    semplicemente chiudere quella scheda del browser.
4.  Quando torni all’interfaccia di Laragon e fai clic su **Start All** per
    riavviare il server, potrebbe essere necessario fare clic sugli stessi
    due popup esattamente un’altra volta.

Dopo averli chiusi questa seconda volta, i popup scompariranno e
sarai completamente libero di usare Laragon!

*(Nota: se in qualsiasi momento durante questi popup l’interfaccia di Laragon
si blocca e non risponde ai clic, ricorda semplicemente il trucco
`Ctrl + Shift + Esc` del Task Manager del passaggio precedente per terminare
il processo in background e ricominciare da capo)*

### Creazione di un database per Joomla

Prima di installare Joomla, è necessario disporre di un database vuoto in cui archiviare i relativi dati.
Laragon include un gestore di database integrato chiamato HeidiSQL, quindi
tutto ciò di cui hai bisogno è già disponibile.

1.  Assicurati che i servizi di Laragon siano in esecuzione (fai clic su **Start All**).
2.  Fai clic sul pulsante **Database** nell'interfaccia principale di Laragon.
3.  Si aprirà una finestra di gestione delle sessioni. Laragon compilerà automaticamente
    le credenziali locali predefinite (Utente: `root`, Password:
    *\[lascia vuoto\]*).
4.  Fai clic sul pulsante **Open** in basso.<br>    
    **Risoluzione dei problemi: errore "Access denied for user 'root'@'localhost'"
    : ** Se fai clic sul pulsante **Open** e ricevi immediatamente un errore di
    connessione non riuscita, non preoccuparti! Di solito significa che hai
    un altro programma MySQL (come XAMPP o MySQL Workbench) in esecuzione in
    background, che sta impedendo a Laragon di accedere alla porta del database
    (Porta 3306).<br>
    ![risoluzione dei problemi di accesso alla configurazione di Laragon](../../../en/images/hosting-local/laragon-setup-windows/06-laragon-setup-troubleshooting.jpg)
    **La soluzione:**
    1.  Premi il tasto Windows, digita **Servizi** e premi Invio.
    2.  Scorri l'elenco verso il basso per trovare **MySQL**, **MySQL80** o **MariaDB**.
    3.  Fai clic con il pulsante destro del mouse sul servizio in esecuzione e seleziona **Arresta**.
    4.  Torna a Laragon, fai clic su **Arresta tutto**, quindi su **Avvia tutto** e
        prova nuovamente a fare clic su **Apri** nel Gestore delle sessioni. Dovrebbe
        connettersi senza alcun errore.
5.  Dopo esserti connesso correttamente e aver effettuato l'accesso al gestore
    di database HeidiSQL, osserva la colonna a sinistra. Fai clic con il pulsante destro del mouse
    sul nome del server (di solito indicato come `Laragon.MySQL` o `127.0.0.1`).
6.  Passa il mouse su **Crea nuovo** e seleziona **Database**.
7.  Apparirà una piccola finestra. Inserisci un nome semplice per il database nel campo
    "Nome" (ad esempio: `joomla_dev`). Puoi lasciare il menu a discesa
    "Regole di confronto" sull'impostazione predefinita.
8.  Fai clic su **OK**.

Vedrai comparire il tuo nuovo database nell’elenco a sinistra. Tutto
qui! Ora puoi chiudere completamente la finestra del gestore database.

### Ottenere i file di Joomla

Ora che il server e il database sono pronti, è il momento di predisporre i
file di Joomla. Il modo in cui eseguire questa operazione dipende interamente
da ciò che si desidera ottenere con questa configurazione locale:

**Metodo 1: per creare un sito web standard** Se si desidera semplicemente creare
un sito web o testare le estensioni, è necessario utilizzare la versione stabile
standard.

- Visitare la [pagina ufficiale per il download di Joomla](https://downloads.joomla.org) 
  e scaricare il file `.zip` dell'ultimo **pacchetto completo**.

**Metodo 2: per testare le PR della community (test delle patch)** Se l'obiettivo è
aiutare la community testando patch e richieste pull, è necessario un pacchetto
precompilato che contenga il codice più aggiornato in assoluto.

- **La build notturna:** scaricare l'ultima `.zip` della build notturna dalla
  pagina [Nightly Builds](https://developer.joomla.org/nightly-builds.html).
  Queste build vengono generate ogni notte e sono perfette per l'uso con il
  componente Joomla Patch Tester.
- **Il pacchetto precompilato della PR:** In alternativa, se stai testando una
  PR specifica su GitHub, scorri fino in fondo alla pagina della PR, fai clic su
  **Show all checks** e cerca il link **Download Prebuilt packages**.
  ![link al pacchetto precompilato della configurazione di laragon](../../../en/images/hosting-local/laragon-setup-windows/07-laragon-setup-prebuilt-package-link.png)

**Metodo 3: Per contribuire al codice principale** Se prevedi di scrivere codice e
inviare le tue Pull Request, ti serve il codice sorgente non compilato.

- Clona direttamente il [repository GitHub di Joomla CMS](https://github.com/joomla/joomla-cms)
  nel tuo ambiente Laragon utilizzando Git.
- *Importante:* Un clone GitHub non elaborato non funzionerà immediatamente: devi
  aprire il Terminale di Laragon ed eseguire `composer install` e `npm ci` nella
  tua cartella per compilare le dipendenze PHP e gli asset CSS/JS. (Poiché hai
  installato la versione Full di Laragon, Composer e NPM sono
  già installati sul tuo sistema).

### **Posizionamento dei file in Laragon:**

Indipendentemente dal metodo scelto, per eseguire i file in Laragon
il processo è esattamente lo stesso:

1.  Apri l'interfaccia di Laragon e fai clic sul pulsante **Root**. Questo
    apre automaticamente la cartella `C:\laragon\www` sul computer.
2.  All'interno di questa cartella `www`, crea una nuova cartella per il progetto. Mantieni
    il nome della cartella semplice, in minuscolo e senza spazi (ad esempio:
    `joomla_dev` o `joomla_pr_test`).
3.  Inserisci i file di Joomla all'interno di questa nuova cartella. (Se hai scaricato un
    `.zip` nel Metodo 1 o 2, estrai direttamente tutto il contenuto in questa
    cartella. Se usi Git nel Metodo 3, clona il repository in questa cartella).
4.  Poiché durante l'installazione hai abilitato "Host virtuali automatici",
    Laragon utilizza automaticamente il nome della cartella per creare il tuo indirizzo web locale. Quindi, una cartella denominata
    `joomla_dev` sarà accessibile nel browser all'indirizzo `http://joomla_dev.test`.
    <br>
    **Suggerimento: mantieni puliti i tuoi ambienti:** è una buona idea creare
    cartelle diverse per versioni diverse di Joomla o per test PR specifici
    (ad esempio, una cartella denominata `joomla5_stable` e un'altra denominata
    `joomla4_dev`). Laragon le eseguirà tutte senza problemi
    fianco a fianco, con i propri URL `.test` puliti, impedendo che il codice
    e i database si mescolino!
    <br>
    ![cartelle del progetto per la configurazione di Laragon](../../../en/images/hosting-local/laragon-setup-windows/08-laragon-setup-project-folders.png)

## Esecuzione del programma di installazione di Joomla

Il database è pronto e i file di Joomla si trovano nella loro nuova
cartella (ad esempio, `C:\laragon\www\joomla_dev`). Ora è il momento di
installare effettivamente Joomla!

**Passaggio cruciale: ricarica Apache!** Se Laragon era già in esecuzione
mentre creavi la nuova cartella del progetto, Laragon non sa ancora che
la cartella esiste.

- Apri l'interfaccia di Laragon.
- Fai clic su **"Reload"** in alto a destra. *(In questo modo obblighi
  Laragon a eseguire la scansione della cartella `www` e a generare il
  nuovo indirizzo `http://joomla_dev.test`).*

**Completamento della configurazione:**

1. Apri il browser web e inserisci l'URL generato automaticamente per il
   progetto (ad es. `http://joomla_dev.test`).
2. Dovresti visualizzare immediatamente la pagina del programma di
   installazione web di Joomla.
3. Scegli la lingua e inserisci un nome per il sito Joomla.
4. Configura l'account del Super User (ricorda queste credenziali di
   accesso: ti serviranno per accedere al pannello di amministrazione di
   Joomla!).
5.  Nella schermata **Configurazione del database**, inserisci le credenziali del
    database Laragon creato in precedenza:
    - **Tipo di database:** `MySQLi` (predefinito)
    - **Nome host:** `localhost`
    - **Nome utente:** `root`
    - **Password:** *\[Lascia questo campo completamente vuoto\]*
    - **Nome del database:** Il nome esatto inserito in HeidiSQL in precedenza
      (ad es., `joomla_dev`).
    ![impostazioni del database dell'installer Joomla per la configurazione di Laragon](../../../en/images/hosting-local/laragon-setup-windows/09-laragon-setup-joomla-installer-database.png)
6.  Fai clic su **Installa Joomla.**

Al termine della barra di avanzamento, verrà visualizzato un messaggio di
successo: ora puoi fare clic su **Apri sito** per visualizzare il tuo sito web
locale attivo oppure su **Apri amministratore** per accedere al backend di Joomla.

È tutto: il tuo sito Joomla locale è attivo e pronto per essere utilizzato.

*Tradotto da openai.com*