<!-- Filename: J4.x:Installing_Joomla / Display title: Installazione di Joomla -->

## Introduzione

L'installazione di Joomla! per la prima volta è molto semplice. Dopo aver completato i passaggi preliminari, impostato un ambiente di hosting e creato un database, il programma di installazione web integrato di Joomla configurerà il tuo nuovo sito in pochi minuti. I passaggi precedenti:

### Configurazione dell'Hosting

Se non hai ancora configurato un ambiente di hosting, devi farlo ora, sia su un servizio di hosting che sul tuo computer locale.

Inoltre, ci sono alcune impostazioni PHP che devono essere adeguate affinché Joomla possa essere installato. Le impostazioni si trovano di solito in un file di configurazione *php.ini* o *user.ini* sul server. Se sei su un hosting condiviso, parla con il tuo servizio di hosting su come cambiare queste impostazioni, se possibile. Se lavori su un localhost, ad esempio con XAMPP, o un VPS o un host dedicato, non dovresti essere limitato da queste impostazioni e puoi impostarle tu stesso.

I valori minimi per il file *php.ini* sono mostrati di seguito:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

È possibile lavorare con valori più bassi di upload_max_filesize e post_max_size, ma le estensioni più grandi non riusciranno a caricarsi e causeranno problemi imprevedibili.

### Configurazione del Database

Se non hai ancora configurato un database, fallo ora. È trattato per un servizio di hosting cPanel nel tutorial [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting). C'è anche un tutorial *Creare un Database per Joomla!* che copre i metodi localhost e phpMyAdmin.

Dovrai annotare le informazioni di base sul database necessarie quando l'installazione effettiva di Joomla viene avviata.

- Posizione del database, solitamente *localhost* anche su un servizio di hosting. Può essere il server di un host specifico come *`dbserver1.yourhost.com`*.
- Il nome del database
- Il nome utente del database
- La password dell'utente del database

## Preparazione per l'Installazione

### Scaricamento e Caricamento dei File del Pacchetto Joomla!

Scarica l'attuale versione di Joomla! dal link sulla pagina [Download Joomla](https://downloads.joomla.org/)

Sposta il file zip del pacchetto di installazione di Joomla scaricato sul server.  
Per un servizio di hosting, puoi utilizzare la funzione di caricamento del File Manager di cPanel oppure un client FTP per trasferire il file zip di Joomla 5.x scaricato sul tuo server. Ci sono diversi client FTP disponibili.  
Ecco un dettagliato [Confronto dei software client FTP](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software).  
In caso di dubbio, usa FileZilla.

È meglio spostare il pacchetto zip scaricato sul tuo server e decomprimerlo lì piuttosto che decomprimerlo localmente e poi spostare l'albero dei file. Normalmente carichi i tuoi file web nella cartella radice del tuo servizio di hosting. Questa è tipicamente chiamata `public_html`, ma altre varianti includono `htdocs` e dipende da come il tuo host ha configurato il server. Per scopi Joomla, puoi caricare i file direttamente in *public_html* o in una sottocartella che hai creato al suo interno.

**Avviso:** Se decomprimi i file sul tuo computer, quindi li copi sul tuo server, assicurati di spostare solo le cartelle e i file contenuti **all'interno** del pacchetto Joomla. Se decomprimi le cartelle e i file in una cartella, ad esempio chiamata *`Joomla`* e poi carichi quella cartella, il tuo sito dovrà essere accessibile su *`iltuosito.com/Joomla`* invece di *`iltuosito.com`*. Puoi rinominare la sottodirectory da Joomla a qualcosa di più adatto al sito, come jblog, e potresti trovare ciò conveniente. **Nota:** i nomi delle directory dovrebbero essere in minuscolo, senza spazi e utilizzare segni meno anziché sottolineature per separare le parole.

I file del pacchetto zip possono essere estratti direttamente sull'host utilizzando vari strumenti da riga di comando (ad esempio, unzip), che devono essere installati sul server. Se il tuo servizio di hosting utilizza lo strumento di amministrazione cPanel, il pulsante Estrarre può essere premuto nel File Manager. Oltre a ciò, il gratuito strumento di terze parti Akeeba Kickstart può anche essere utilizzato per questo scopo. I file e le directory decompresse verranno posizionati nella cartella corrente. L'estrazione sul tuo computer locale dipende dal tuo sistema operativo. Prova a fare clic con il tasto destro del mouse e verifica se c'è un menu di estrazione. In questo caso, il tuo sistema operativo potrebbe inserire i file in una cartella con lo stesso nome del file zip. Dopo l'estrazione, puoi eliminare il file zip e rinominare la cartella di estrazione in qualcosa di breve e adatto all'uso in un URL.

## Inizia Installazione

Con i requisiti sopra indicati soddisfatti, un database creato e i file Joomla necessari in posizione, sei pronto per installare Joomla. Avvia l'installatore web di Joomla aprendo il tuo browser preferito e navigando al nome di dominio del sito. Su un'installazione di hosting utilizzerai *`https://www.yoursitename.com`*. Se stai installando Joomla localmente, utilizzerai *`http://localhost/`* e dovresti vedere la schermata di installazione.

![Joomla installer part 1, installation language and site name](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla cercherà di identificare automaticamente il campo *Seleziona lingua* dalla lingua del tuo browser. È possibile modificarlo se necessario.

Compila le seguenti informazioni.

- **Nome del sito** Il nome del tuo sito web — questo può essere modificato in qualsiasi momento nella pagina di Configurazione Globale del Sito.

Quando tutto sulla prima pagina è completato, seleziona il pulsante *Setup Login Data* per procedere.

## Dati di accesso

Dovresti ora vedere la schermata dei dati di accesso.

![Joomla installer part 2, login data](../../../en/images/getting-started/installing-joomla-installer-2.png)

Compila le seguenti informazioni.

- **Nome Reale** Il nome del Super User. Questo è il modo in cui Joomla ti darà il benvenuto quando effettui l'accesso.
- **Nome utente account Super User** Il nome utente per il *Super User*. Evita di usare *admin* come nome dell'Amministratore!
- **Password Admin** Ricorda che un Super User ha il massimo controllo delle interfacce del Sito e dell'Amministratore, quindi usa una password difficile. Utilizza **Il Mio Profilo** nell'interfaccia di *Amministrazione* per cambiarla in seguito.
- **Indirizzo Email Super User** L'indirizzo email del Super User. Inserisci un'email valida nel caso dimenticassi la password. Questo è l'indirizzo email dove riceverai un link per cambiare la password del Super User.

Quando tutto nella seconda pagina è completato, seleziona il pulsante *Configurazione Connessione al Database* per procedere.

## Configurazione del database

Inserisci le informazioni del database annotate quando hai creato il database per questa installazione.

![Joomla installer part 3, database configuration](../../../en/images/getting-started/installing-joomla-installer-3.png)

Per semplificazione, queste istruzioni sono un riferimento per l'installazione con un database MySQLi. Le istruzioni nella pagina di installazione sono autoesplicative, ma eccole di nuovo:

- **Tipo di Database** MySQLi è il database comune utilizzato
- **Nome Host** Dove si trova il tuo database. Comune è *localhost*, anche sui servizi di hosting. Tuttavia, alcuni host utilizzano un server di database specifico come *dbserver1.yourhost.com*.
- **Nome Utente** Il nome utente utilizzato per connettersi al database
- **Password** La password per l'utente del database (non la password dell'Amministratore)
- **Nome del Database** Il nome del database
- **Prefisso Tabella** Questo viene generato automaticamente come caratteristica di sicurezza. Puoi accettare il predefinito generato casualmente o cambiarlo. Basta non dimenticare di mettere il carattere di sottolineatura (`_`) alla fine del prefisso.
- **Crittografia della Connessione** specifica come la connessione al database deve essere crittografata. Se non lo sai - allora è meglio attenersi al predefinito. Tuttavia, questo consente alle aziende che utilizzano l'autenticazione a una o due vie per la connessione al database di fornirla.

Tutte queste scelte e altre ancora possono essere modificate nella pagina Configurazione Globale del Sito, sotto *Opzioni del Server* una volta completata l'installazione. Nota, comprometterai la tua installazione se modifichi queste impostazioni dopo l'installazione a meno che tu non abbia una copia completa del database attualmente utilizzato dall'installazione di Joomla. Utilizzi comuni potrebbero essere l'aggiornamento del nome utente e della password del database o il completamento di un trasferimento di un'installazione esistente a un nuovo host con parametri diversi.

Dopo aver selezionato il pulsante *Installa Joomla*, dovrebbe apparire la barra di avanzamento dell'installazione di Joomla.

![Joomla installer part 4, installation progress bar](../../../en/images/getting-started/installing-joomla-installer-4.png)

Una volta completata l'installazione, dovresti vedere la pagina di successo.

## Completamento

### Successo e Conclusione dell'Installazione

Congratulazioni! Il tuo sito Joomla è pronto.

![Joomla installer part 5, your joomla site is ready](../../../en/images/getting-started/installing-joomla-installer-5.png)

Lo screenshot sopra mostra un'installazione per sviluppatori. Un'installazione di produzione rimuove automaticamente la cartella di installazione.

Se vuoi iniziare a utilizzare Joomla immediatamente senza installare lingue aggiuntive, puoi selezionare *Apri Amministratore* per accedere al *Cruscotto Amministratore* oppure selezionare *Apri Sito* per andare alla pagina iniziale del sito. Potresti vedere una sezione con impostazioni PHP consigliate.

- **Impostazioni Consigliate** Queste impostazioni sono consigliate nella tua configurazione PHP, ma non impediranno l'installazione di Joomla!. Puoi fare riferimento alle istruzioni sopra su come possono essere modificate se c'è bisogno di farlo.

### Lingue extra

Come parte del processo di installazione di Joomla, ti viene data l'opportunità di installare lingue aggiuntive prima di completare l'installazione.

Per fare questo, selezionare il pulsante Installa lingue aggiuntive

Questo ti porterà a una pagina di installazione aggiuntiva che ti permetterà di selezionare le lingue di cui hai bisogno.

#### Installa Lingue Aggiuntive

Viene visualizzato un elenco di pacchetti linguistici.

![Joomla installer part 6, install additional languages](../../../en/images/getting-started/installing-joomla-installer-6.png)

Seleziona fino a 3 lingue che desideri installare. (Più di 3 alla volta possono causare problemi di timeout; puoi installarne altre in seguito.)

Ricorda quanto segue:

- I pacchetti lingua inclusi nelle distribuzioni personalizzate non saranno elencati in questa fase poiché sono già installati.
- Una versione dei pacchetti proposti corrisponderà alla versione principale di Joomla (5.0.x, 5.1.x, ecc.). La versione minore del pacchetto potrebbe non corrispondere, ad esempio stai installando la versione 5.0.3 e viene mostrato un pacchetto lingua 5.0.2.
- I pacchetti lingua non corrispondenti nell'esempio sopra potrebbero avere stringhe non tradotte.
- I pacchetti lingua non corrispondenti saranno offerti come aggiornamento quando i pacchetti saranno aggiornati dai team di traduzione registrati. L'aggiornamento disponibile sarà mostrato nel Pannello di controllo così come in **Estensioni → Aggiornamento**. Questo comportamento è simile a **Estensioni → Installa Lingue**.

Seleziona *Avanti* e verrà visualizzata una barra di avanzamento durante l'installazione del o dei pacchetti lingua.

#### Scegli la lingua predefinita

Quando l'installazione delle lingue è completata, ti verrà presentata una schermata simile a *Congratulazioni! Il tuo sito Joomla è pronto.* La differenza sarà un elenco delle lingue installate che ti permetterà di selezionare la lingua predefinita per il sito e l'interfaccia dell'Amministratore.

![Joomla installer part 7, choose default language](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Seleziona la lingua predefinita che desideri utilizzare.
- Quando hai selezionato la lingua predefinita, seleziona il pulsante *Imposta lingua predefinita* per confermare.
- Verrà visualizzato un messaggio di sistema che conferma che Joomla ha impostato la lingua predefinita dell'AMMINISTRATORE e del SITO. Quel messaggio può essere chiuso.

#### Finalizzare

Ora puoi navigare alla *Dashboard Amministratore*. Accedi selezionando *Apri Amministratore* oppure vai direttamente alla Home page del tuo sito selezionando *Apri Sito*.

*Tradotto da openai.com*

