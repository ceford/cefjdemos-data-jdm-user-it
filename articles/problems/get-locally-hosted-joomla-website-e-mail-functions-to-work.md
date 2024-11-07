<!-- Filename: Get_locally_hosted_Joomla!_website_e-mail_functions_to_work / Display title: Email Host Locale  -->

## Hosting Locale

La maggior parte degli ISP blocca la porta 25, quindi non puoi inviare email dal server SMTP del tuo computer. Questo per bloccare gli spammer. Se non intendi fare spam, puoi utilizzare il server di posta del tuo ISP.

Per utilizzare la funzione email dal server SMTP del tuo ISP anche se stai ospitando il tuo sito Joomla sul tuo computer, effettua l'accesso al tuo sito Joomla come Super Utente e vai alla scheda **Server** della pagina **Configurazione Globale**. Nella sezione **Mail** i tuoi dati dovrebbero essere simili ai seguenti:

    Email di provenienza: someone@example.com (di solito tu)
    Nome di provenienza: NomeQualsiasi

    Mailer: SMTP
    Host SMTP: smtp.charter.net (Qualunque cosa il tuo ISP ti dica di usare per i loro server SMTP)
    Percorso Sendmail: /usr/sbin/sendmail
    Porta SMTP: 25
    Sicurezza SMTP: STARTTLS
    Autenticazione SMTP: Sì (o No)
    Nome utente SMTP: johndoe (nome utente di un tuo account email presso il tuo ISP)
    Password SMTP: trr33459 (password di un tuo account email presso il tuo ISP)
Invia un messaggio di prova per verificare che funzioni.

Il Nome utente SMTP, la Password e l'Host sono gli stessi campi che inserisci quando aggiungi un account di Outlook Express, o Eudora, o qualsiasi client email che puoi utilizzare sul tuo computer.

Potresti incontrare problemi con le estensioni che cambiano l'indirizzo *From* nelle email inviate. Ad esempio, l'estensione ProjectFork a volte invia email come se provenissero dalla persona che gestisce il progetto. Questo può causare un problema poiché alcuni server SMTP degli ISP non permettono un indirizzo "from" che non corrisponde al nome utente (ad esempio, Rogers in Canada). Riceverai un messaggio del tipo: "PHPMAILER_FROM_FAILEDname@whatever.com." Una soluzione alternativa è assicurarsi di utilizzare sempre un indirizzo email valido del tuo ISP per i tuoi utenti.

*Tradotto da openai.com*

