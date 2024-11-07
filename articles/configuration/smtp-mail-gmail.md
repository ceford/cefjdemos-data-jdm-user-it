<!-- Filename: How_to_debug_SMTP_mail_in_Joomla_4 / Display title: Posta SMTP e Gmail -->

## Introduzione

Nella pagina Configurazione Globale, nel pannello Server, c'è un'opzione per selezionare un agente di consegna della posta. L'impostazione predefinita è *PHP Mail*. Se questo non funziona, potrebbe essere consigliato di utilizzare SMTP. Utilizza lo stesso meccanismo della tua applicazione di posta elettronica. Ci sono diverse impostazioni che devi configurare correttamente. In breve:

Vai a **Configurazione Globale** e seleziona la scheda **Server**. Cerca il pannello *Posta* vicino al fondo del modulo.

- **Mailer** impostato su SMTP. Verranno visualizzati diversi altri campi.
- **Host SMTP** Questo è localhost per impostazione predefinita, ma è improbabile che funzioni. Deve essere impostato sull'host che gestisce la tua posta in uscita, ad esempio un account Gmail.
- **Porta SMTP** Il valore predefinito è 25. Verifica che sia il valore che il tuo Host SMTP si aspetta.
- **Sicurezza SMTP** Il valore predefinito è *Nessuna*, ma probabilmente è necessario STARTTLS.
- **Autenticazione SMTP** Questo potrebbe non essere richiesto se stai utilizzando una rete domestica che non richiede l'autenticazione per le email in uscita. Altrimenti:
- **Nome utente SMTP** e **Password SMTP** inserisci i valori che usi per accedere al tuo account di posta elettronica via internet.
- Seleziona il pulsante **Invia email di prova**.

## Utilizzare Gmail

Se disponi di un account Gmail attivo, puoi utilizzare Gmail come server di posta configurandolo nelle impostazioni globali.

Nella scheda server, imposta le seguenti opzioni:

- Mailer: SMTP
- Host SMTP: smtp.gmail.com
- Porta SMTP: 465
- Sicurezza SMTP: SSL/TLS
- Autenticazione SMTP: Sì
- Imposta le due righe successive con le tue informazioni. Devi utilizzare una password specifica per l'applicazione (ASP), descritta di seguito.
- Nome utente SMTP: il tuo nome utente Gmail
- Password SMTP: la password specifica per l'applicazione (ASP) che hai generato, descritta di seguito.

Sono anche supportate le seguenti combinazioni:

- Porta SMTP: 587
- Sicurezza SMTP: STARTTLS
- Porta SMTP: 25
- Sicurezza SMTP: STARTTLS

Non è necessario abilitare il modulo SSL in Apache.

È necessario abilitare l'estensione OpenSSL in PHP. I dettagli possono essere trovati alla [pagina di installazione di php.net](https://www.php.net/manual/en/openssl.installation.php).

Se utilizzi WAMP su Windows, il modulo openssl non è abilitato di default e hai bisogno di abilitarlo. Per fare ciò:

1.  Apri il file php.ini e decommenta la riga `extension=php_openssl.dll` rimuovendo il punto e virgola ; dall'inizio della riga.
2.  Salva il file php.ini e riavvia il servizio Apache.

Nota che se utilizzi la verifica in due passaggi su Gmail, devi aggiungere una nuova password in Impostazioni - Account - Modifica impostazioni account - Altre impostazioni account Google - Sicurezza - Verifica in due passaggi - Gestisci le password specifiche per l’applicazione.

Quando la nuova Password Specifica per l’Applicazione (ASP) è presentata in gruppi di quattro caratteri separati da spazi, assicurati di **NON inserire gli spazi** nella password SMTP nelle impostazioni del server di posta in Joomla.

- Password Specifiche per l’Applicazione (ASP): Consulta la pagina di supporto Google intitolata [Accedi con le Password per le app](https://support.google.com/accounts/answer/185833).
- Verifica a 2 Fattori: Consulta la pagina di supporto Google intitolata [Attiva la verifica in due passaggi](https://support.google.com/accounts/answer/185839).

## Debugging

Se la mail non viene inviata o non arriva mai:

- Seleziona **Plugin** dal **Pannello Home → Sito**. 
- Trova e attiva il plugin **System - Debug** e configurarlo:
  - Imposta **Gruppi Consentiti** su *Super Users* per limitare l'output di debug alla tua 
    sessione di accesso sia nel backend che nel frontend. Se non vuoi 
    accedere al frontend come Super Utente, crea un gruppo utente unico per le tue 
    attività di test e seleziona tale gruppo utente dall'elenco dei gruppi consentiti.
  - **Salva e Chiudi**
- Seleziona **Configurazione Globale** dal **Pannello Home → Sito**. 
- Nella scheda *Sistema* imposta **Debug Sistema** su *Sì*.
- Nella scheda *Server* imposta **Rapporti Errori** su *Massimo*.
- Nella scheda *Log* nota il contenuto di *Percorso alla Cartella di Log*, 
  di solito *\[qualcosa\]/administrator/logs*. 
- Imposta **Registra Quasi Tutto** su *Sì*.
- Nel pannello di *Registrazione Personalizzata* imposta il campo *Categorie di Log* su *mail* 
  (senza virgolette).
- **Salva** per salvare le impostazioni di debug.
- Nella scheda **Server** seleziona il pulsante *Invia Email di Test* in basso 
  alla pagina.

Se ci sono problemi nel codice durante il test, dovresti ottenere un *Stack Trace*
che ti aiuterà, o aiuterà altri, a diagnosticare il problema. Inoltre, cerca un file 
nella cartella dei log con un nome come *administrator/logs/everything.php* e aprilo
con un editor di testo. Potrebbe essere utile vedere cosa è stato registrato quando il messaggio è stato inviato.

*Tradotto da openai.com*

