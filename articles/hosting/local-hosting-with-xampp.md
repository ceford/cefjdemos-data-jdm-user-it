<!-- Filename: / Display title: Hosting Locale con XAMPP -->

## Introduzione

XAMPP è un pacchetto facile da installare che include il server web Apache, PHP, XDEBUG e il database MySQL. Questo ti consente di creare l'ambiente necessario per eseguire Joomla! sulla tua macchina locale. L'ultima versione di XAMPP è disponibile sul sito web di [Apache Friends](https://www.apachefriends.org/index.html). I download sono disponibili per Linux, Windows e Mac OS X. Scarica il pacchetto per la tua piattaforma.

*Nota Importante Riguardante XAMPP e Skype:* Apache e Skype utilizzano entrambi la porta 80 come alternativa per le connessioni in entrata. Se usi Skype, vai nel pannello Strumenti-Opzioni-Avanzate-Connessioni e deseleziona l'opzione *Usa 80 e 443 come alternative per le connessioni in entrata*. Se Apache viene avviato come servizio, prenderà la porta 80 prima che Skype si avvii e non vedrai un problema. Tuttavia, per sicurezza, disabilita l'opzione in Skype.

## Installazione

L'installazione su qualsiasi piattaforma è molto semplice - usa l'Installer. Non c'è un vero manuale o guida per XAMPP. La documentazione è sotto forma di FAQ collegate dalla pagina dei Download.

### Installazione su Windows

Per Windows, è consigliato installare XAMPP in "c:\xampp" (non in "c:\program files"). Se lo fai, il tuo Joomla! (e qualsiasi altra cartella di siti web locali) andrà nella cartella "c:\xampp\htdocs". (Per convenzione, tutto il contenuto web va sotto la cartella "htdocs".)

Se hai più server http (come IIS) puoi cambiare la porta di ascolto di xampp. In \apache\conf\httpd.conf, modifica la riga Listen 80 in Listen \[portnumber\] (es: "Listen 8080").

<div class="alert alert-info">
<h4>Tutorial della rivista della comunità Joomla<h4>
<p>Puoi trovare un tutorial dettagliato su come installare XAMPP su Windows, insieme alla Joomla 4 Beta, al tester di patch Joomla e a Git in questo <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git" rel="noreferrer noopener">articolo della rivista della comunità Joomla</a>.</p></div>

Per installare XDebug: [XAMPP - Configurazione di XDebug per PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Installazione su Linux

#### Installa XAMPP

La pagina di download scarica un installer xampp-linux-x64-8.2.12-0-installer.run dove 8.2.12 è l'ultima versione. Esegui il file dell'installer per installare Apache2, MySQL e PHP.

Dopo l'installazione usa i seguenti comandi per avviare e fermare i servizi:
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Testa il tuo server locale XAMPP

Apri il tuo Browser e puntalo su

    http://localhost

L'index.php re-indirizzerà a

    http://localhost/xampp

Qui troverai istruzioni su come cambiare username/password di default. Su un PC che non serve file a Internet o LAN, cambiare i default è una decisione personale.

#### Ottieni Joomla

* Scarica l'ultimo zip di installazione di Joomla
* Decomprimi sul tuo disco rigido
* Connetti a localhost con un client FTP Default
* Crea una cartella per il tuo Joomla sul server localhost
* Carica i file di installazione di Joomla non compressi nella nuova cartella Joomla.

##### Importante:

- L'installazione di xampp imposta la corretta proprietà dei file e permessi.
- Usando il **comando CHOWN** causerai **problemi di proprietà con xampp**.
- **Usare nautilus** per manipolare cartelle/file su localhost causerà **problemi di proprietà con xampp**.

#### Informazioni sul database

- Host: localhost
- Nome predefinito del Database: test
- Utente predefinito del Database: root
- Password predefinita: Non c'è **nessuna** Password predefinita.
- Password amministratore: tua scelta.

Installare dati di esempio è consigliato per l'utente principiante.

Dopo l'installazione cancella la directory di installazione e punta il tuo Browser su: `http://localhost/yournewjoomlafolder` o `http://localhost/yournewjoomlafolder/administrator`.

#### Creare un collegamento nel menu di Ubuntu

##### Per creare una GUI per xampp collegata al tuo menu di Ubuntu

Apri il Terminale e digita

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Poi copia quanto segue nell'editor nano e salva.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP Control Panel
    Comment=Avvia e Ferma XAMPP
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Se il pannello di controllo non si avvia, prova a eseguire direttamente il comando Exec nel terminale:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Se ricevi l'errore:

    Error importing pygtk2 and pygtk2-libglade

Installa le librerie mancanti:

    sudo apt-get install python-glade2

#### Debugger PHP di XDebug

Il pacchetto XAMPP per Linux non include il debugger PHP XDebug.
Per installare XDebug su Debian o Ubuntu:

- Installa il pacchetto *build-essential*:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Scarica il [pacchetto di sviluppo](http://www.apachefriends.org/en/xampp-linux.html) per la tua versione di XAMPP ed estrailo sopra la tua installazione esistente:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Compila XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

Dopo aver fatto questo, sul tuo terminale avrai il seguente output…

    Configuring for:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Poi l'output sarà questo.. per favore controlla la directory specificata.

    Installing shared extensions:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Crea una cartella nella tua cartella temporanea che contenga il file di dati generato da XDebug:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Installazioni alternative:

Installa utilizzando la libreria di estensioni PHP (PECL) inclusa in xampp:

    sudo /opt/lampp/bin/pecl install xdebug

Su Ubuntu/Debian puoi installare utilizzando:

    apt-get install php5-xdebug

(avvertimento: questo installerà anche Apache e PHP dai repository apt).

##### Avvertimento per utenti a 64 bit

Quando compili XDebug o installi tramite apt-get, riceverai un messaggio di errore quando (ri)avvii xampp:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

Questo perché xampp gira a 32 bit ma XDebug è a 64 bit. Per superare questo problema, puoi creare xdebug.so su una macchina a 32 bit o scaricarlo da:

    http://code.activestate.com/komodo/remotedebugging/

Scarica il file: "PHP Remote Debugging Client" per "Linux (x86)".
Estrai il contenuto del file sul tuo computer, questo file compresso contiene diverse cartelle con numeri di versione es: 4.4, 5.0, 5.1 ... 5.3 e così via, entra nella cartella con il numero di versione più alto o in quella che funziona per te, poi copia manualmente il file "xdebug.so" nella seguente posizione, sovrascrivi se necessario

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Ricorda che questa posizione potrebbe essere diversa sul tuo computer.

### Installazione su Mac OS X

Mac OS X include di default un server Apache, ma la maggior parte degli sviluppatori preferirà usare gli strumenti integrati e la configurabilità forniti da XAMPP.

Come la maggior parte dei programmi su Mac, l'installazione è un gioco da ragazzi. Visita il sito web [Apache Friends](https://www.apachefriends.org/) e scarica l'installer (xampp-osx-8.2.4-0-installer.dmg). Fai doppio clic sull'installer scaricato per avviare il processo di installazione.

Per avviare il server, apri "XAMPP Control.app" e premi il pulsante start accanto a Apache.

#### Un po' di risoluzione dei problemi

Molti utenti Mac hanno un po' di difficoltà in questa fase quando provano a impostare un'altra istanza di Apache sulla loro macchina. Se non riesci ad avviare l'Apache di XAMPP, hai due opzioni:
**Puoi cambiare la porta di ascolto di XAMPP.** In \Applications\XAMPP\xamppfiles\etc\httpd.conf, modifica la riga che dice, "Listen 80" in Listen \[portNumber\]. Esempio:

    Listen 8080

**Puoi cambiare la porta di ascolto del server Apache pre-installato.** In finder, vai su "/etc" (CMD+SHIFT+G); da qui potrai navigare attraverso i file Apache normalmente nascosti. Trova la cartella etichettata Apache2, e modifica il file "http.conf". Modifica la riga che dice, "Listen 80" in Listen \[portNumber\]. Esempio:

    Listen 8080

*Nota: Se scegli di cambiare la porta del server Apache pre-installato, potresti dover riavviare il tuo computer affinché le modifiche abbiano effetto. Dovrai anche autenticarti come amministratore per cambiare questi file.*

### Test dell'installazione di XAMPP

Una volta che XAMPP è installato e hai avviato il servizio Apache con lo strumento Pannello di Controllo di XAMPP, puoi testarlo aprendo il tuo browser e navigando a `http://localhost`. Dovresti vedere la schermata di benvenuto di XAMPP simile a quella qui sotto.

![La pagina di avvio di xampp](../../../en/images/hosting/local-hosting-xampp.png)

Seleziona il link chiamato `phpinfo()` nel menu in alto. Questo mostrerà una lunga schermata di informazioni sulla configurazione PHP, come mostrato qui sotto.

![La pagina di informazioni sulla versione php di xampp](../../../en/images/hosting/local-hosting-xampp-php.png)

A questo punto, XAMPP è installato correttamente. Nota il *File di Configurazione Caricato*. Modificheremo questo file nella sezione successiva per configurare XDebug.

*Tradotto da openai.com*

