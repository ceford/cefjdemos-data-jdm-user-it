<!-- Filename: J5.x:Managing_Mail_Template_Layout / Display title: Modelli di Posta Elettronica -->

## Introduzione

I modelli di posta vengono utilizzati per inviare messaggi email di sistema in **testo semplice** o **HTML** o entrambi, selezionati nel modulo *Opzioni: Modelli di Posta*. Se è selezionato solo un metodo, l'alternativa non sarà presente nel modulo di modifica del messaggio.

Lo screenshot seguente mostra una selezione dei 26 modelli di posta standard disponibili. L'elenco è disponibile selezionando **Sistema -> Modelli di posta** dal menu Amministratore.

![mail templates list](../../../en/images/templates/mail-templates-list.png)

I messaggi di posta possono essere personalizzati per modificare il layout, l'aspetto e il testo in base alle esigenze del tuo sito. Ad esempio, potresti voler utilizzare il logo del sito e lo schema di colori in quelle email inviate ai clienti. La personalizzazione delle email inviate agli amministratori è meno importante.

Ci sono due metodi di personalizzazione: tramite *Mail Template: Options* per tutti i modelli di posta e tramite *Per Template Mail Settings*.

## Modello di posta: Opzioni

Seleziona il pulsante **Opzioni** nella barra degli strumenti della lista *Modelli di Posta* per accedere alle impostazioni generali del modello di posta. Seleziona il pulsante *Attiva/Disattiva Guida in Linea* per vedere se uno qualsiasi dei campi del modulo ha un aiuto extra.

![mail templates options](../../../en/images/templates/mail-templates-options.png)

### Formato Email

Sii consapevole che un destinatario potrebbe impostare un client di posta per utilizzare HTML semplice o Testo Normale per evitare il download delle immagini. Quindi potrebbe essere meglio impostare il *Formato della Mail* su *Testo Normale* o *Entrambi*.

### Impostazioni Modello Email Per

Se questa opzione è impostata su **Sì**, i moduli di modifica del modello di posta individuale disporranno di una scheda aggiuntiva *Opzioni* che ti consente di modificare le impostazioni di posta per quel modello e, facoltativamente, di inviare una copia (BCC) a un indirizzo email specifico, a condizione che il campo **Invia copia** qui sia impostato su **Abilitato**.

## Modulo di Modifica del Modello

Nell'elenco dei Modelli Email puoi selezionare qualsiasi modello da modificare. Il link del Titolo porta al modulo di modifica per il modello inglese predefinito. Ogni bandiera è un link allo stesso modello in quella lingua.

### La scheda Posta

![edit mail template form](../../../en/images/templates/mail-template-edit.png)

I contenuti delle aree Oggetto e Corpo sono inizialmente memorizzati in stringhe di lingua. Questo rende facile *Ripristinare l'Oggetto Predefinito* o il *Corpo*. Tuttavia, una volta che un modello di posta specifico è stato modificato, i suoi campi Oggetto e Corpo vengono memorizzati nella tabella `#__mail_templates`.

Gli elementi tra parentesi graffe sono tag segnaposto che vengono sostituiti con valori reali quando l'email viene inviata. Nell'esempio sopra `{SITENAME}` sarebbe qualunque nome tu abbia scelto per il tuo sito. `{Method}` sarebbe il metodo di trasporto della posta selezionato: `PHP Mail`, `Sendmail` o `SMTP`.

I valori segnaposto disponibili variano da una mail all'altra. Potresti aggiungere i tuoi valori segnaposto personalizzati, ma ciò richiede un plugin personalizzato, descritto in un [articolo della rivista](https://magazine.joomla.org/all-issues/february-2025/joomla-5-email-templates-how-to-add-variables-via-plugin) di febbraio 2025.

### La scheda Opzioni

Questa scheda è presente solo se *Impostazioni Email per Modello* è impostato su *Sì* in *Modelli di Email: Opzioni*. L'illustrazione seguente mostra uno screenshot con *Impostazioni Email* impostato su *No*. Se impostato su *Sì* compaiono più campi modulo che sostituiscono le opzioni di Mail impostate nella Configurazione Globale, scheda Server.

![edit mail template form](../../../en/images/templates/mail-template-edit-options.png)

Se desideri inviare una copia nascosta di un'email in uscita a un indirizzo email specifico, puoi inserirlo nel campo *Invia Copia a Email*.

## Sostituzioni Modello di Posta

Per creare un sostituto del modello di posta all'interno di un modello personalizzato:

1. Vai su Sistema -> Modelli del sito -> Apri il tuo modello (ad esempio, Cassiopeia).
2. Nella scheda Crea override, seleziona joomla -> mail.
3. Joomla copierà il file `mailtemplate.php` nella directory `/html/layouts/joomla/mail/` del tuo modello, dove potrai modificarlo secondo le necessità.

Una volta creato l'override, puoi modificare il layout e gli stili delle tue email senza influenzare il modello di base.

## Elenco dei Modelli di Posta

| Titolo | Estensione | Descrizione |
|-------|-----------|-------------|
| Registro Azioni Utenti: Mail di Notifica | Registro Azioni Utenti | Mail inviata agli amministratori riguardo nuove voci nel Registro Azioni Utenti. |
| Configurazione Globale: Mail di Test | Configurazione | Inviato quando si clicca sul pulsante "Invia Mail di Test" nella Configurazione Globale. Viene inviato all'indirizzo di invio impostato nelle impostazioni della mail. |
| Contatti: Mail Modulo di Contatto | Contatti | L'email del "Modulo di Contatto". |
| Contatti: Copia Mail Modulo di Contatto | Contatti | Inviata al mittente di una mail con il modulo di contatto se l'opzione "Invia Copia al Mittente" è abilitata e selezionata. |
| Messaggi: Nuovo messaggio | Messaggi | Email contenente un messaggio creato nel componente di messaggistica. |
| Privacy: Richiesta Esportazione Dati (Admin) | Privacy | Mail per informare l'utente che una richiesta di esportare i dati da questo sito è stata creata dall'amministratore |
| Privacy: Richiesta Rimozione Dati (Admin) | Privacy | Mail per informare l'utente che una richiesta di rimuovere i dati da questo sito è stata creata dall'amministratore |
| Privacy: Richiesta Esportazione Dati | Privacy | Mail per verificare che i dati di un utente debbano essere esportati dal sito |
| Privacy: Richiesta Rimozione Dati | Privacy | Mail per verificare che i dati di un utente debbano essere rimossi dal sito |
| Privacy: Esportazione Dati Utente | Privacy | Mail con esportazione dei dati utente |
| Utenti: Mailing di Massa Utenti | Utenti | L'email di "Mailing di Massa Utenti". |
| Utenti: Reset Password | Utenti | Inviata a un utente tramite il link "Hai dimenticato la password?" ad esempio in un modulo di accesso. |
| Utenti: Notifica nuovo account all'admin | Utenti | Notifica all'admin che un nuovo account attivato è stato creato. |
| Utenti: Richiesta all'admin di verificare il nuovo account | Utenti | Notifica agli admin per verificare un nuovo account verificato. |
| Utenti: Account attivato dall'admin | Utenti | Notifica inviata all'utente che il nuovo account è stato attivato da un amministratore. |
| Utenti: Nuovo account con attivazione dell'admin | Utenti | Notifica del nuovo account all'utente, che ora dovrà essere attivato da un admin. |
| Utenti: Nuovo account con attivazione dell'admin (con PW) | Utenti | Notifica del nuovo account all'utente, che ora dovrà essere attivato da un admin. La password in chiaro è inclusa nella mail. |
| Utenti: Nuovo account senza attivazione | Utenti | Notifica del nuovo account all'utente. L'account è già attivato. |
| Utenti: Nuovo account senza attivazione (con PW) | Utenti | Notifica del nuovo account all'utente. L'account è già attivato. La password in chiaro è inclusa nella mail. |
| Utenti: Nuovo account con auto-attivazione | Utenti | Notifica del nuovo account all'utente, che ora dovrà auto-attivare. |
| Utenti: Nuovo account con auto-attivazione (con PW) | Utenti | Notifica del nuovo account all'utente, che ora dovrà auto-attivare. La password in chiaro è inclusa nella mail. |
| Utenti: Promemoria Nome Utente | Utenti | Inviata a un utente tramite il link "Hai dimenticato il nome utente?" ad esempio in un modulo di accesso. |
| Codice inviato via email | Autenticazione Multi-fattore - Codice di Autenticazione via Email | Inviato agli utenti dalla pagina di Autenticazione Multi-fattore quando si utilizza l'opzione "Codice di Autenticazione via Email". |
| Attività - Consenso Privacy: Rinnovare il Consenso | Attività - Consensi Privacy | Promemoria di rinnovare il consenso alla privacy per questo sito. |
| Joomla: Notifica Aggiornamenti | Attività - Notifica Aggiornamenti Joomla! | Inviato agli amministratori del sito quando il plugin task "Notifica Aggiornamenti Joomla!" rileva un aggiornamento. |
| Utenti: Nuovo Utente | Utente - Joomla! | Inviato a un nuovo utente quando viene creato nel backend. |

*Tradotto da openai.com*

