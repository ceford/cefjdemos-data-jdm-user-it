<!-- Filename: No_original_yet / Display title: Hosting Locale su Linux -->

## Introduzione

Questo articolo tratta dell'hosting di Joomla su un computer personale basato su Linux per scopi di test e sviluppo. Le versioni di Linux trattate appartengono alla famiglia Debian-Ubuntu, e specificamente a Linux Mint. Altre distribuzioni sono simili ma hanno una sintassi dei comandi e posizioni dei file differenti.

È necessario installare un insieme di pacchetti software comunemente noto come stack LAMP. Le lettere si riferiscono a Linux, Apache, MySQL e PHP. Puoi installare il software utilizzando l'interfaccia grafica utente (GUI) oppure la riga di comando in una finestra del Terminale. Sono modi differenti di utilizzare il Gestore di Pacchetti Synaptic.

## Installare Apache con l'interfaccia grafica

Dal menu di sistema, contrassegnato con il logo LM, seleziona Amministrazione / Gestore Pacchetti Synaptic. Ti verrà chiesta la password. Inserisci la tua password di accesso per aprire l'interfaccia grafica. In alto a destra si trova un pulsante `Cerca`. Selezionalo, inserisci **apache** e scegli `Cerca`. Seleziona la casella di controllo `apache2` e, nella finestra popup, seleziona `Segna per l'installazione`. Un'altra finestra popup mostrerà un elenco di pacchetti aggiuntivi necessari per supportare apache. Seleziona `Segna`:

![gestore pacchetti synaptic](../../../en/images/hosting/synaptic-package-manager-gui.png "Interfaccia Grafica Gestore Pacchetti Synaptic")

Seleziona il pulsante `Applica` nella barra degli strumenti in alto e il pulsante `Applica` nella finestra di dialogo di riepilogo. Apache sarà installato e configurato, concludendo il processo con una **finestra di dialogo Cambiamenti Applicati**. Seleziona `Chiudi`.

Puoi confermare che Apache è installato e funzionante aprendo il tuo browser, Firefox è predefinito in una nuova installazione di Linux Mint, e inserendo **localhost** nella barra degli URL. Dovresti vedere la pagina predefinita di Ubuntu Apache2:

![pagina predefinita di apache](../../../en/images/hosting/apache-default-page.png "Pagina Predefinita di Apache")

La pagina contiene alcune informazioni utili sui percorsi dei file che potrebbero non essere facilmente disponibili in seguito, quindi potresti voler stampare questa pagina su carta o in un file pdf.

## Installare PHP con il CLI

È probabilmente meglio installare PHP utilizzando la riga di comando. Una ragione per questo è che, al momento della stesura, il Gestore di Pacchetti Synaptic offre solo PHP8.1, sebbene PHP8.2 sia disponibile da tempo e possa essere installato da un repository di terze parti. C'è una buona descrizione della procedura in questo tutorial con sezioni di Avvio rapido e Dettagliata.

Per prima cosa, chiudi la GUI del Gestore di Pacchetti Synaptic e poi apri una finestra del Terminale e inserisci i seguenti comandi uno alla volta:

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl}
sudo apt install php8.2-fpm
sudo a2enconf php8.2-fpm
sudo systemctl reload apache2
```
Nel tuo browser, verifica che la pagina predefinita di localhost funzioni ancora.

## Installare MySQL o MariaDB

Puoi cercare sul web informazioni su ciascuno di questi pacchetti di database. MySQL è la scelta tradizionale, ma è stato acquisito da Oracle ed è ora meno popolare. MariaDB è un sostituto Open Source che offre funzionalità aggiuntive. Entrambi funzionano con Joomla! 5, ma non è facile passare dall'uno all'altro. Le tabelle devono essere esportate e importate. Joomla! 5 richiede versioni minime specifiche che Linux Mint offre tramite il Gestore Pacchetti Synaptic.

Apri l'interfaccia grafica del Gestore Pacchetti Synaptic e cerca mysql-server o mariadb-server. Seleziona la casella di controllo per l'elemento che termina con -server. Seleziona `Marca per l'installazione` e poi `Applica` nella Barra degli strumenti in alto. Puoi aprire il pannello Dettagli per vedere cosa sta accadendo durante l'installazione. Seleziona `Chiudi` quando hai finito.

Puoi testare se il tuo database funziona inserendo `mysql` nella riga di comando. Questo è lo stesso sia per MySQL che per MariaDB. Dovresti vedere un messaggio di errore `Accesso negato`, il che va bene poiché indica che l'installazione del tuo database funziona effettivamente.

## Installare phpMyAdmin

phpMyAdmin è uno strumento GUI per la gestione dei database di cui avrai bisogno per creare e gestire i tuoi database. Nel gestore dei pacchetti Synaptic, cerca **phpmyadmin**. Seleziona la casella di controllo e `Contrassegna per l'installazione`. Dopo il download, ci sarà un prompt per selezionare il `Webserver da riconfigurare automaticamente`. Seleziona la casella di controllo per `apache2` e poi il pulsante `Avanti`. Nella schermata di configurazione successiva lascia la casella di controllo `Configura database...` selezionata e premi `Avanti`.

Scegli una password applicativa per l'utente phpmyadmin. Test: nel tuo browser inserisci localhost/phpmyadmin nella barra degli URL. Dovresti vedere la schermata di login di phpMyAdmin. Con il nome utente phpmyadmin e la password che hai inserito durante l'installazione sarai in grado di effettuare il login. Ma non sarai in grado di creare alcun database! Per risolvere il problema, devi modificare il file di configurazione come root nella finestra Terminale:

```bash
sudo nano /etc/phpmyadmin/config.inc.php
```
Trova le due righe contenenti // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; e rimuovi le barre antecedenti per decommentarle. Entrambe!

Quindi accedi a mysql dalla riga di comando e crea un nuovo utente assegnando a quell'utente tutti i privilegi:
```bash
sudo mysql
CREATE USER 'admin'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
exit
```
Quindi torna a phpMyAdmin e prova a effettuare il login con il nome utente **admin** e senza password. Dovresti vedere tutti i database e poter creare nuovi database.

## Priorità del file Index

La posizione predefinita per le pagine web su Ubuntu/Linux Mint è /var/www/html. Se elenchi il contenuto di quella directory, vedrai che contiene index.html con il contenuto della pagina predefinita di Ubuntu Apache2. Crea un file chiamato index.php in quella directory con il seguente contenuto:

```php
<?php echo phpinfo();
```

Ricarica localhost. Non c'è nessun cambiamento! Inserisci **localhost/index.php** nella barra degli URL e vedrai una pagina contenente le informazioni sulla versione di PHP. Questo comportamento è controllato dalla configurazione predefinita di Apache che può essere modificata abilitando il modulo `dir` di Apache e modificando la sua configurazione:

```bash
sudo a2enmod dir
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Sposta index.php all'inizio dell'elenco. Poi riavvia Apache:

```bash
sudo systemctl restart apache2
```

Questa volta usando solo **localhost** nella barra degli URL dovresti vedere il contenuto del file index.php, una pagina di informazioni PHP.

## Host Virtuali

In un'installazione Linux di default, i file di sistema si trovano nella cartella root (/)
e i file dati degli utenti sono nella cartella home (/home/ilmiousername). Questo è un
potenziale problema perché l'utente Apache di default, www-data, potrebbe non avere i permessi
appropriati per creare file nello spazio dei file utente. La soluzione migliore è creare
Host Virtuali.

Prima di tutto, è necessario un modulo che permetta ad Apache di cambiare il suo utente e gruppo per
adattarsi a ciascun utente:

```bash
sudo apt-get install libapache2-mpm-itk
sudo a2enmod mpm_itk
```

Successivamente, fai una copia del file di configurazione del sito predefinito ed editala:

```bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf username.localhost.conf
sudo nano username.localhost.conf
```

Il file di configurazione del sito predefinito contiene commenti per spiegare il suo
contenuto. Sono omessi nell'illustrazione sotto. Decommenta la riga ServerName e modifica tutte le istanze di `username` con il tuo
nome utente.

```xml
<VirtualHost *:80>
        ServerName username.localhost
        ServerAdmin webmaster@localhost
        DocumentRoot /home/username/public_html
        <IfModule mpm_itk_module>
                AssignUserId username username
        </IfModule>
        <Directory /home/username/public_html/ >
                Options Indexes FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Abilita il nuovo sito e riavvia Apache:

```bash
sudo a2ensite username.localhost
sudo systemctl reload apache
```

Inserisci un'entrata nel file /etc/hosts per aggiungere un'entrata per il nuovo host virtuale.
Altrimenti, il tuo browser lo cercherà su internet.

```bash
sudo nano /etc/hosts
```

Quando terminato, dovrebbe apparire qualcosa di simile a questo:

```bash
127.0.0.1       localhost
127.0.0.1       username.localhost
127.0.1.1       nomehost

# Le seguenti righe sono desiderabili per host compatibili con IPv6
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

**Nomehost:** Questo è il nome che hai dato al tuo computer quando hai installato
Linux. Ti servirà a breve. Puoi cambiarlo se lo desideri, ma è meglio informarsi a riguardo e farlo prima.

Se tutto funziona correttamente, con un URL del tipo username.localhost vedrai un elenco delle directory del tuo 
direttorio public_html. La visualizzazione pubblica degli elenchi delle directory è considerata una cattiva pratica, un rischio per
la sicurezza, ed è solitamente disabilitata da un'altra impostazione di configurazione di Apache. Tuttavia, per un sito personale su un
personal computer utilizzato per lo sviluppo e il testing è molto utile. Molti siti diversi possono essere impostati in sottodirectory differenti. Ad esempio,
siti Joomla 4 e Joomla 5, Bacheche, Wiki e così via. Quando hai
molti siti di prova è difficile ricordare tutti i nomi delle sottodirectory!

## Accesso alla Rete Domestica

Se hai un altro computer nella tua rete domestica, probabilmente vorrai accedere al tuo sito Linux anche da lì. Per farlo funzionare è necessario un altro host virtuale. Copia e modifica quello appena creato:

```bash
cd /etc/apache2/sites-available
sudo cp username.localhost.conf username.conf
sudo nano username.conf
```
Cambia il ServerName da username.localhost a username.hostname e poi abilita il nuovo sito virtuale e riavvia Apache.

```bash
sudo a2ensite username
sudo apachectl restart
```
Vai sull'altro computer nella rete domestica e modifica il suo file hosts personale. Ad esempio, su un Mac modifica /private/etc/hosts e aggiungi la seguente riga in fondo:

```bash
192.168.178.20 username.hostname www.username.hostname
```
Dove 192.168.178.20 è l'indirizzo IP del tuo computer Linux.

Ora sul tuo secondo computer dovresti essere in grado di accedere al server web sul tuo computer Linux inserendo username.hostname nella barra URL del tuo browser.

## Note sulle Partizioni

Il software installato utilizzando il Synaptic Package Manager si trova solitamente nella directory root di Linux (/). I dati utente si trovano nella directory home (/home). In un'installazione semplice, queste directory si trovano nella stessa partizione del disco fisico.

In un'installazione più complessa, magari con l'opzione di avviare diversi sistemi operativi (Windows o Linux) o versioni diverse dello stesso sistema operativo, la root e i dati utente si trovano spesso in partizioni separate. Questo permette l'accesso agli stessi dati utente da ciascun sistema operativo.

C'è un problema: un sito Joomla situato in una directory /home/username necessita di dati di database che si trovano solitamente nella directory root, specificamente in /var/lib/mysql. Puoi spostare la directory dei dati di MySQL/MariaDB in una posizione accessibile da entrambi i sistemi operativi, sia nella partizione /home che in una partizione separata. Questo tutorial descrive come cambiare la directory dei dati di MySQL in Ubuntu e Debian Linux. Questo deve essere fatto per ciascun sistema operativo, ma non è trattato qui.

