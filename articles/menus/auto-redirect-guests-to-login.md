<!-- Filename: Auto_redirect_guests_to_login / Display title: Reindirizza automaticamente gli ospiti al login  -->

## Funzionalità Desiderata

Supponiamo che tu abbia alcune opzioni di menu che richiedono che un utente sia loggato, come *Invia un Articolo*. Vorresti che tutti gli utenti potessero vedere la voce di menu riservata, indipendentemente dal fatto che siano loggati o meno. Il comportamento desiderato è il seguente.

* Se l'utente è loggato, viene indirizzato direttamente alla voce di menu riservata.
* Se l'utente non è loggato, gli viene presentato il modulo di accesso e, dopo un accesso riuscito, viene reindirizzato alla pagina riservata.
* Se l'utente non è registrato, ha l'opzione di registrarsi o di navigare verso un'altra pagina.

## Soluzione

Ecco come fare questo in Joomla!.

1. Crea un nuovo menu dall'elenco dei **Menu**, chiamato ad esempio **Menu Nascosto**.
2. Aggiungi gli elementi di menu che saranno accessibili solo agli utenti registrati (ad esempio, *Invia un Articolo*). Imposta i livelli di accesso richiesti di questi elementi di menu su **Registrato**.
3. NON creare un modulo per il *Menu Nascosto*. Non sarà visualizzato su nessuna pagina, quindi non ha bisogno di un modulo.
4. Crea il tuo menu *reale*, chiamato ad esempio **Menu del Sito**, e l'elemento di menu che sarà visualizzato per tutti gli utenti, ad esempio *Invia un Articolo*.
   - L'elemento di menu avrà un tipo di voce di menu di **Alias Voce di Menu** che si trova nel tipo di voce di menu **Collegamenti di Sistema**.
   - Il parametro *Voce di Menu* sarà l'elemento di menu *Invia un Articolo* del *Menu Nascosto*. 
   - Il livello di accesso per questo elemento di menu sarà **Pubblico**, poiché tutti devono essere in grado di vederlo e usarlo.
5. Crea un modulo per il *Menu del Sito* proprio come fai per qualsiasi menu.
6. Se desideri sottomenu, assicurati di aver aggiunto gli elementi di sottomenu nel **Menu del Sito** e non nel **Menu Nascosto**.

Ora, quando un ospite (utente non registrato) accede alla scelta del menu *Invia un Articolo*, viene reindirizzato alla pagina di accesso. Se l'accesso ha esito positivo, l'utente viene reindirizzato alla pagina limitata **Invia un Articolo**. Se è già loggato, il reindirizzamento è immediato.

## Esempio

Per i seguenti elementi del menu:

1. Home
2. Blog
3. Wiki
4. Directory
5. Annunci
6. FAQS
7. Negozio
8. Contattaci

Tutti gli elementi del menu dovrebbero essere visibili a tutti nel front-end, ma gli elementi 3, 4, 5, 6 e 7 dovrebbero essere accessibili solo agli utenti **Registrati**.

In questo caso, gli elementi del menu dal 3 al 7 sono situati nel menu *nascosto* con il loro parametro **Accesso** impostato su **Registrato**. Gli elementi dal 3 al 7 hanno elementi di menu *Alias* nel menu *reale* con i loro parametri **Accesso** impostati su **Pubblico**.

