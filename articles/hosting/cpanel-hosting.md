<!-- Filename: J4.x:Hosting_Setup / Display title: Hosting cPanel  -->

## Introduzione

## Hosting cPanel

Quando accedi al tuo servizio di hosting cPanel, questo è ciò che dovresti aspettarti di vedere:

![pannello di controllo hosting cpanel](../../../en/images/hosting/cpanel-hosting.png)

### Configurazione del Database

Il pannello Database viene utilizzato per creare un database e un utente del database per Joomla.

Seleziona l'elemento MySQL Databases e inserisci un nome per il database nel modulo. La prima parte del modulo è predefinita. Il resto dipende da te. Dovrebbe essere breve e forse non ovvio - *jblog* ad esempio.

Nello stesso modulo, scendi alla sezione *Aggiungi Nuovo Utente*. Inserisci un nome utente. Può essere qualsiasi cosa tu voglia. Sarà utilizzato nel tuo file di configurazione di Joomla quindi non è qualcosa che devi ricordare. Usa il generatore di password per creare una password difficile da ricordare e copiala in un editor di testo - ne avrai bisogno durante l'installazione di Joomla.

Nello stesso modulo, scendi a *Aggiungi Utente al Database*. Seleziona l'utente che hai creato e il database che hai creato dai menu a tendina e poi clicca sul pulsante Aggiungi. Si apre un modulo per Gestire i Privilegi. Seleziona la casella di controllo *Tutti i Privilegi* e poi clicca sul pulsante *Applica Modifiche*.

Questo è tutto - ora hai un database pronto per un'installazione di Joomla.

### Caricare il Codice Sorgente di Joomla

A un certo punto avrai scaricato il file zip del codice sorgente di Joomla sul tuo laptop o desktop. Ora devi decidere come strutturare il tuo sito. La radice del documento per il tuo sito è la cartella *public_html*. Potresti mettere Joomla lì. Tuttavia, ciò ti impedisce di utilizzare un'altra applicazione sullo stesso sito. Ad esempio, potresti avere due installazioni Joomla completamente separate, una per la produzione (visualizzazione pubblica) e una per il test (visualizzazione privata). Quindi potresti creare una cartella all'interno di *public_html*, chiamata *j4* ad esempio, e caricare Joomla lì. Potresti avere un'altra cartella chiamata *j4test* e mettere un'altra copia di Joomla lì. L'illustrazione sottostante mostra tale impostazione con due siti web Joomla.

![gestore file hosting cpanel](../../../en/images/hosting/cpanel-file-manager.png)

Quando hai deciso la tua struttura, seleziona la cartella Joomla scelta in File Manager e clicca sul pulsante Carica. Nel modulo di caricamento, seleziona il file zip del codice sorgente di Joomla sul tuo computer locale per caricarlo nella cartella selezionata. Dopo il caricamento, torna a File Manager, seleziona il file *zip* e clicca sul pulsante Estrai. Dopo l'estrazione, puoi selezionare ed eliminare il file *zip*.

Ecco fatto! Sei pronto per installare Joomla.

