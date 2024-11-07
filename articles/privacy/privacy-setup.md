<!-- Filename: J4.x:Privacy_Setup / Display title: Configurazione della Privacy  -->

## Componente Privacy

Il Componente Privacy è utilizzato per gestire le informazioni sulla privacy e per raccogliere richieste di informazioni o richieste di eliminazione delle informazioni. Si basa su indirizzi email, quindi si applica principalmente agli utenti registrati che devono fornire un indirizzo email durante la registrazione. Si applica anche ai dati degli utenti non registrati i cui indirizzi email sono stati forniti tramite il componente Contatti. Non implementa il permesso di utilizzare cookie o tracciamenti richiesti dal GDPR.

Quando vengono raccolte informazioni personali identificabili, dovresti assicurarti che:

- L'utente sia informato sul motivo per cui richiedi queste informazioni in un linguaggio chiaro e facile da comprendere.
- L'utente sappia quali dati raccogli su di lui.
- L'utente sappia per cosa utilizzerai i dati.
- L'utente abbia fornito il suo consenso attivo all'uso dei dati.

In genere, queste informazioni sono descritte in un articolo sulla Politica della Privacy.

## Dashboard della Privacy

Il dashboard della privacy fornisce un riepilogo delle **Richieste di Privacy** e dello **Stato della Privacy** del sito. Per accedere:

- Seleziona **Utenti → Privacy** dal menu Amministratore.

![dashboard della privacy](../../../en/images/privacy/privacy-dashboard.png)

Ci sono due moduli visualizzati per default nel Dashboard della Privacy:

### Richieste di Privacy

Questo modulo fornisce un riepilogo delle richieste di informazioni correnti.

### Stato della Privacy

Questo modulo mostra lo stato delle opzioni a cui i proprietari del sito dovrebbero prestare attenzione:

- **Informativa sulla privacy pubblicata**: imposta un articolo sulla Privacy nell'extension **Sistema - Consenso alla Privacy**.
- **Elemento di menu del modulo richiesta pubblicato**: imposta un elemento di menu per consentire agli utenti autenticati di inviare richieste.
- **Richieste urgenti in sospeso**: controlla le richieste confermate più vecchie dell'età specificata nei parametri del componente (default 14 giorni) e avvisa il proprietario del sito di eventuali richieste che richiedono attenzione urgente.
- **Invio email abilitato**: il sito deve essere in grado di inviare email per elaborare le richieste di informazioni.
- **Crittografia del database**: questo è rilevante quando viene utilizzato un database remoto.

## Plugin: System - Consenso alla Privacy

Se questo plugin è disabilitato, il pannello di Stato Privacy della Dashboard mostrerà
che la Politica sulla Privacy è **Non Disponibile** e fornirà un link al
modulo di modifica del plugin. Quando abilitato, il plugin richiede a qualsiasi nuovo utente
che si registra sul tuo sito di acconsentire alla Politica sulla Privacy. Tutti gli utenti esistenti
saranno reindirizzati al loro Profilo Utente affinché possano dare il consenso.

Per impostare i consensi:

- Seleziona **Dashboard di Home **→** Plugin** dal menu dell'Amministratore.
- Trova il plugin **System - Consenso alla Privacy** (da non confondere con
  il plugin Privacy - Consensi).
- Seleziona per aprire il modulo di inserimento dati del plugin.

![plugin sistema consenso alla privacy](../../../en/images/privacy/plugin-system-privacy-consent.png)

- Imposta lo **Stato** su **Abilitato**.
- Facoltativo: Seleziona o Crea un articolo da collegare dal modulo di Registrazione.
  Oppure imposta il Tipo di Privacy su Voce di Menu e Seleziona o Crea una voce
  di menu.
- Seleziona la scheda **Scadenza** e **Attiva Guida Inlinea** per una
  spiegazione di ciascun campo. Abilita e regola i parametri **se** desideri
  che i consensi scadano dopo un numero selezionato di giorni.

### Note sul Consenso alla Privacy per siti Multilingua:

**Breve Politica sulla Privacy e Messaggio di Reindirizzamento** Se utilizzi il
testo predefinito, verrà visualizzato nella lingua dell'utente. Non è
possibile tradurre il testo personalizzato. Se desideri personalizzare il testo
e visualizzarlo in più lingue, dovresti lasciare questo campo vuoto e utilizzare
la funzione di override della lingua di Joomla per personalizzare le stringhe di lingua
`PLG_SYSTEM_PRIVACYCONSENT_NOTE_FIELD_DEFAULT` e
`PLG_SYSTEM_PRIVACYCONSENT_REDIRECT_MESSAGE_DEFAULT` per ogni lingua installata.

**Articolo di Privacy** e **Voce di Menu di Privacy** Se associ questo
articolo o voce di menu con alternative in altre lingue, allora la
politica sulla privacy verrà visualizzata nella lingua corretta per l'utente.

## Plugin: Utente - Termini e Condizioni

Quando abilitato, questo plugin richiede a qualsiasi nuovo utente che si registra sul tuo sito di acconsentire ai Termini e Condizioni per utilizzare il tuo sito. Tutti gli utenti esistenti saranno reindirizzati al loro Profilo Utente in modo che possano dare il consenso.

Questo plugin non è abilitato per impostazione predefinita. Per abilitare:

- Seleziona **Dashboard Home → Plugin** dal menu Amministratore.
- Trova il plugin **Utente - Termini e Condizioni**.
- Seleziona per aprire il modulo di inserimento dati del plugin.
- Imposta lo **Stato** su **Abilitato**.
- Opzionale: Seleziona o crea un articolo a cui collegarti dal modulo di Registrazione.

### Note sui Termini e Condizioni Utente per siti multilingue

**Termini e Condizioni Brevi** Se usi il testo predefinito, sarà visualizzato nella lingua dell'utente. Non è possibile tradurre il testo personalizzato. Se desideri personalizzare il testo e visualizzarlo in più lingue, dovresti lasciare questo campo vuoto e utilizzare il sistema di sovrascrittura della lingua di Joomla per personalizzare le stringhe linguistiche `PLG_USER_TERMS_NOTE_FIELD_DEFAULT` per ogni lingua installata.

**Articolo Termini & Condizioni** Se associ questo articolo a delle alternative in altre lingue, la politica sulla privacy sarà visualizzata nella lingua corretta per l'utente.

## Visualizzazione del Consenso alla Registrazione Utente

Insieme, i due plugin appaiono sul modulo di Registrazione Utente come nel seguente screenshot:

![visualizzazione consensi alla privacy](../../../en/images/privacy/privacy-consents-site.png)

## Voce di Menu: Richiesta di Informazioni sulla Privacy

Gli utenti registrati possono richiedere un riepilogo delle informazioni o la rimozione tramite una voce di menu. Configura come segue:

- Seleziona **Menu** → **Menu Inferiore** dal menu dell'Amministratore (utilizza quello più conveniente).
- Inserisci un **Titolo** appropriato, ad esempio: **Richiesta di Informazioni sulla Privacy**.
- Utilizza il pulsante **Seleziona** per aprire il popup del tipo di voce di menu.
- Nella sezione **Privacy** seleziona l'elemento **Crea Richiesta**.
- Imposta il campo **Accesso** su **Registrato**.
- **Salva & Chiudi**.

Vai alla visualizzazione del tuo sito e verifica che la voce di menu non venga visualizzata quando non sei connesso e che venga visualizzata dopo aver effettuato l'accesso. Usa il link e prova l'opzione **Esporta**. Puoi provare l'opzione **Rimuovi** più tardi utilizzando un account fittizio. Se c'è una richiesta in sospeso vedrai un messaggio di errore:

“La tua richiesta di informazioni non può essere creata. C'è già una richiesta di informazioni attiva per questo indirizzo email e tipo di richiesta. Si prega di contattare il proprietario del sito per aggiornamenti su questa richiesta.”

## Voce di Menu: Conferma Richiesta Privacy

Per motivi SEF, è possibile creare una voce di menu nascosta per consentire all'utente di confermare la richiesta. Questo sarà presente nel link inviato via email.

- Seleziona **Menu** → **Menu Nascosto** dal menu dell'Amministratore (crea un Menu Nascosto senza una posizione di modulo assegnata, oppure vedi sotto).
- Inserisci un **Titolo** appropriato, ad esempio: **Conferma Richiesta Privacy**.
- Usa il pulsante **Seleziona** per aprire il dialogo popup del Tipo di Voce di Menu.
- Nella sezione **Privacy**, seleziona l'elemento **Conferma Richiesta**.
- Se non hai un Menu Nascosto, utilizza il tuo menu principale e nella scheda Tipo di Link imposta **Visualizza nel Menu** su **No**.
- **Salva & Chiudi**.

## Voci del Menu dell'Amministratore

Dai un'occhiata alle altre voci del menu del Componente Privacy.

### Richieste di Privacy dell'Amministratore

Questa schermata è il punto centrale per elaborare e gestire le richieste di informazioni degli utenti. Si prega di consultare l'articolo correlato sul Workflow della Privacy per indicazioni sull'elaborazione delle richieste.

![richieste di informazioni sulla privacy](../../../en/images/privacy/privacy-information-requests.png)

### Capacità delle Estensioni

Questa schermata raccoglie e visualizza le informazioni sulle capacità relative alla privacy segnalate dalle singole estensioni. È intesa ad assistere nella preparazione di documentazione come un articolo sulla politica sulla privacy o un articolo sui termini di servizio.

![richieste di informazioni sulla privacy](../../../en/images/privacy/privacy-extension-capabilities.png)

I contenuti della pagina provengono da stringhe di lingua nel core, nel componente privacy e nei plugin che implementano l'evento onPrivacyCollectAdminCapabilities. Questo include:

- Autenticazione
- Captcha
- Installatore
- Privacy
- Sistema
- Utente

Le informazioni saranno visualizzate nella lingua selezionata per l'accesso dell'Amministratore.

### Consensi

Questa schermata visualizza un elenco di consensi, dal più recente. Sarà nella lingua utilizzata nel modulo di consenso, tipicamente durante la registrazione. Puoi cercare un utente specifico per nome. Si noti che il consenso all'accettazione dei Termini e Condizioni del sito non è registrato qui. Questo è solo nel Registro delle Azioni dell'Utente.

![consensi sulla privacy](../../../en/images/privacy/privacy-consents.png)

*Tradotto da openai.com*

