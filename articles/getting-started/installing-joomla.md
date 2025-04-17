<!-- Filename: J4.x:Installing_Joomla / Display title: # Installare Joomla -->

## Introduzione

Installare Joomla! per la prima volta è molto semplice. Dopo aver completato i passaggi preliminari, impostato un ambiente di hosting e creato un database, l'installatore web integrato di Joomla imposterà il tuo nuovo sito in pochi minuti. I passaggi precedenti:

### Configurazione dell'Hosting

Se non hai ancora impostato un ambiente di hosting, devi farlo ora, sia su un servizio di hosting che sul tuo computer locale.

Inoltre, ci sono alcune impostazioni PHP che devono essere sufficienti per installare Joomla. Le impostazioni si trovano solitamente in un file di configurazione *php.ini* o *user.ini* sul server. Se sei su un hosting condiviso, parla con il tuo servizio di hosting su come modificare queste impostazioni, se è possibile farlo. Se lavori su un localhost, ad esempio con XAMPP, o su un VPS o host dedicato, non dovresti avere restrizioni da queste impostazioni e puoi impostarle da solo.

I valori minimi per il file *php.ini* sono mostrati di seguito:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

È possibile lavorare con valori più bassi di upload_max_filesize e post_max_size, ma estensioni più grandi non riusciranno a caricarsi e causeranno problemi imprevedibili.

### Configurazione del Database

Se non hai ancora impostato un database, fallo ora. È trattato per un servizio di hosting cPanel nel tutorial [Hosting cPanel](jdocmanual?article=user/hosting/cpanel-hosting). C'è anche un tutorial *Creare un Database per Joomla!* che copre i metodi localhost e phpMyAdmin.

Dovrai annotare le informazioni di base sul database necessarie quando viene avviata l’installazione effettiva di Joomla.

- Posizione del database, di solito *localhost* anche su un servizio di hosting. Può essere il server di un host specifico come *`dbserver1.yourhost.com`*.
- Il nome del database
- Il nome utente del database
- La password dell'utente del database

## Preparazione per l'installazione

### Scaricare e caricare i file del pacchetto Joomla!

Scarica l'ultima release di Joomla! dal link nella
[Pagina di download di Joomla](https://downloads.joomla.org/).

Sposta il file zip del pacchetto di installazione di Joomla scaricato sul server.
Per un servizio di hosting, puoi utilizzare la funzione di Upload del File Manager di cPanel
oppure un client FTP per trasferire il file zip di Joomla 5.x scaricato sul tuo server. Sono disponibili diversi client FTP.
Ecco un [Confronto dettagliato tra software client FTP](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software).
In caso di dubbi, usa FileZilla.

La *cartella root* del tuo server

È meglio spostare il pacchetto zip scaricato sul tuo server e
decomprimerlo lì piuttosto che decomprimerlo localmente e poi spostare l'albero dei file.
Normalmente carichi i tuoi file web nella cartella root del tuo servizio di hosting.
Questa è tipicamente denominata `public_html`, ma altre variazioni
includono `htdocs` e ciò dipende da come il tuo host ha configurato il
server. Per scopi Joomla, puoi caricare i file direttamente in
*public_html* o in una sottocartella che hai creato all'interno.

**Avvertenza:** Se decomprimi i file sul tuo computer, quindi li copi sul
tuo server, assicurati di spostare solo le cartelle e i file contenuti **all'interno**
del pacchetto Joomla. Se decomprimi le cartelle e i file in una cartella,
ad esempio chiamata *`Joomla`* e poi carichi quella cartella, il tuo sito
dovrà essere accessibile su *`nomesito.com/Joomla`* invece di
*`nomesito.com`*. Puoi rinominare la sottodirectory da Joomla in
qualcosa di più appropriato per il sito, come jblog, e potresti trovare che
sia conveniente. **Nota:** i nomi delle directory dovrebbero essere in minuscolo, senza
spazi e utilizzare trattini anziché underscore per separare le parole.

I file del pacchetto zip possono essere estratti direttamente sull'host utilizzando
vari strumenti a riga di comando (ad es. unzip), che devono essere installati sul
server. Se il tuo servizio di hosting utilizza lo strumento amministrativo cPanel, si può
premere il pulsante Extract nel File Manager. Inoltre,
anche lo strumento gratuito di terze parti Akeeba Kickstart
può essere utilizzato a questo scopo. I file e le directory decompressi
saranno posizionati nella cartella corrente. L'estrazione sul tuo computer dipende
dal tuo sistema operativo. Prova a fare clic con il tasto destro e verifica se c’è un menu di estrazione. In questo caso
il tuo sistema operativo potrebbe inserire i file in una cartella con lo stesso nome del file zip.
Dopo l'estrazione, puoi eliminare il file zip e rinominare la
cartella di estrazione con qualcosa di breve e adatto per l'uso in un URL.

## Inizio Installazione

Con i requisiti sopra indicati soddisfatti, un database creato e i file richiesti di Joomla pronti, sei pronto per installare Joomla. Avvia l'installazione web di Joomla aprendo il tuo browser preferito e navigando al nome di dominio del sito. Su un'installazione in hosting utilizzerai *`https://www.yoursitename.com`*. Se stai installando Joomla localmente, utilizzerai *`http://localhost/`* e dovresti vedere la schermata di installazione.

![Installatore Joomla parte 1, lingua di installazione e nome del sito](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla cercherà di identificare automaticamente il campo *Seleziona Lingua* dalla lingua del tuo browser. Puoi cambiarlo se necessario.

Inserisci le seguenti informazioni.

- **Nome del Sito** Il nome del tuo sito web — può essere cambiato in qualsiasi momento più tardi nella pagina Configurazione Globale del Sito.

Quando tutto nella prima pagina è completato, clicca sul pulsante *Configura Dati di Accesso* per procedere.

## Dati di Accesso

Ora dovresti vedere la schermata dei dati di accesso.

![Installatore di Joomla parte 2, dati di accesso](../../../en/images/getting-started/installing-joomla-installer-2.png)

Compila le seguenti informazioni.

- **Nome Reale** Il nome del Super Utente. Questo è come Joomla ti
  accoglierà quando effettuerai l'accesso.
- **Nome utente dell'account Super Utente** Il nome utente per il *Super Utente*.
  Evita di usare *admin* come nome dell'Amministratore!
- **Password amministratore** Ricorda che un Super Utente ha il massimo controllo
  delle interfacce del Sito e dell'Amministratore, quindi usa una password difficile.
  Usa **Il Mio Profilo** nell'interfaccia di *Amministrazione* per cambiarla in seguito.
- **Indirizzo email del Super Utente** L'indirizzo email del Super Utente. Inserisci un
  email valida nel caso in cui dimenticassi la tua password. Questo è l'indirizzo email
  dove riceverai un link per cambiare la password del Super Utente.

Quando tutto nella seconda pagina è completato, fai clic sul pulsante *Imposta Connessione al Database*
per procedere.

## Configurazione del Database

Inserisci le informazioni sul database annotate quando hai creato il database per questa installazione.

![Installatore Joomla parte 3, configurazione del database](../../../en/images/getting-started/installing-joomla-installer-3.png)

Per semplificare, queste istruzioni sono un riferimento all'installazione con un database MySQLi. Le istruzioni sulla pagina di installazione sono autoesplicative, ma eccole di nuovo:

- **Tipo di Database** MySQLi è il database comune utilizzato
- **Hostname** Dove si trova il tuo database. Comune è *localhost*, 
  anche nei servizi di hosting. Tuttavia, alcuni host utilizzano un server di database specifico come *dbserver1.yourhost.com*.
- **Nome Utente** Il nome utente utilizzato per connettersi al database
- **Password** La password per l'utente del database (non la password dell'Amministratore)
- **Nome del Database** Il nome del database
- **Prefisso della Tabella** Questo viene generato automaticamente come misura di sicurezza. Puoi accettare il valore predefinito generato casualmente o cambiarlo. Basta non dimenticare di mettere il carattere underscore (`_`) alla fine del prefisso.
- **Crittografia della Connessione** specifica come la connessione al database dovrebbe essere crittografata. Se non lo sai - è meglio attenersi al valore predefinito. Tuttavia, ciò consente alle aziende che utilizzano un'autenticazione a uno o due fattori per la connessione al database di fornirla.

Tutte queste scelte e altre ancora possono essere modificate nella pagina di Configurazione Globale del Sito, sotto *Opzioni del Server* dopo aver completato l'installazione. Nota, interromperai la tua installazione se modifichi queste impostazioni dopo l'installazione a meno che tu non abbia una copia completa dell'attuale database utilizzato dall'installazione di Joomla. Usi comuni sarebbero aggiornare il nome utente e la password del database o completare lo spostamento di un'installazione esistente a un nuovo host con parametri diversi.

Dopo che premi il pulsante *Installa Joomla*, dovresti vedere la barra di progresso dell'installazione di Joomla.

![Installatore Joomla parte 4, barra di progresso dell'installazione](../../../en/images/getting-started/installing-joomla-installer-4.png)

Una volta completata l'installazione, dovresti vedere la pagina di successo.

## Completamento

### Successo e completamento dell'installazione

Congratulazioni! Il tuo sito Joomla è pronto.

![Joomla installer parte 5, il tuo sito Joomla è pronto](../../../en/images/getting-started/installing-joomla-installer-5.png)

Lo screenshot sopra mostra un'installazione per sviluppatori. Un'installazione di produzione rimuove automaticamente la cartella di installazione.

Se vuoi iniziare a usare Joomla subito senza installare lingue aggiuntive, puoi selezionare *Apri Amministratore* per andare al *Cruscotto dell'Amministratore* o selezionare *Apri Sito* per andare alla Home page del Sito. Potresti vedere una sezione con le impostazioni PHP consigliate.

- **Impostazioni Consigliate** Queste impostazioni sono consigliate nella tua configurazione PHP, ma non impediranno l'installazione di Joomla. Puoi fare riferimento alle istruzioni sopra su come possono essere modificate se c'è bisogno di farlo.

### Lingue Aggiuntive

Come parte del processo di installazione di Joomla, hai l'opportunità di installare lingue aggiuntive prima di completare l'installazione.

Per fare ciò, seleziona il pulsante Installa Lingue Aggiuntive

Questo ti porterà a una pagina di installazione extra che ti permetterà di selezionare le lingue che desideri.

#### Installare Lingue Aggiuntive

Viene visualizzato un elenco di pacchetti lingua.

![Joomla installer parte 6, installare lingue aggiuntive](../../../en/images/getting-started/installing-joomla-installer-6.png)

Seleziona fino a 3 lingue che desideri installare. (Più di 3 in una volta può causare problemi di timeout; puoi installarne di più in seguito.)

Ricorda quanto segue:

- I pacchetti lingua inclusi nelle distribuzioni personalizzate non saranno elencati in questa fase in quanto sono già installati.
- Una versione dei pacchetti proposti corrisponderà alla versione principale di Joomla (5.0.x, 5.1.x, ecc.). La versione minore del pacchetto potrebbe non corrispondere, ad esempio, stai installando la versione 5.0.3 e viene mostrato un pacchetto lingua 5.0.2.
- I pacchetti lingua non corrispondenti nell'esempio sopra potrebbero avere stringhe non tradotte.
- I pacchetti lingua non corrispondenti saranno offerti come aggiornamento quando i pacchetti vengono aggiornati dai team di Traduzione registrati. L'aggiornamento disponibile sarà mostrato nel Pannello di controllo così come in **Estensioni → Aggiorna**. Questo comportamento è simile a **Estensioni → Installa Lingue**.

*Avanti* e una barra di progresso saranno visualizzati mentre il pacchetto o i pacchetti lingua sono installati.

#### Scegli la Lingua Predefinita

Quando l'installazione delle lingue è completa, ti verrà presentata una schermata simile a *Congratulazioni! Il tuo sito Joomla è pronto.* La differenza sarà una lista delle lingue installate che ti permetterà di selezionare la lingua predefinita per il Sito e l'interfaccia Amministratore.

![Joomla installer parte 7, scegli la lingua predefinita](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Seleziona la lingua predefinita che desideri usare.
- Quando hai selezionato la lingua predefinita, premi il pulsante *Imposta lingua predefinita* per confermare.
- Verrà visualizzato un messaggio di sistema che conferma che Joomla ha impostato la lingua predefinita per AMMINISTRATORE e SITO. Quel messaggio può essere chiuso.

#### Finalizzare

Ora puoi navigare al *Cruscotto dell'Amministratore*. Accedi selezionando *Apri Amministratore* o vai direttamente alla Home page del tuo sito selezionando *Apri Sito*.

