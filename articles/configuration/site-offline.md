<!-- Filename: J4.x:Site_Offline / Display title: Sito Offline -->

## Solo Utenti del Sito

Ci possono essere occasioni in cui è necessario rendere il tuo sito Joomla! 
non disponibile ai visitatori per un breve periodo. Esiste un semplice interruttore di configurazione **Sito Non Disponibile** per questo scopo, che può essere cambiato da **No** a **Sì** secondo necessità. Quando è impostato su *Sì*, tutti i visitatori del sito vedono una pagina di messaggio offline con un modulo di login. Il modulo predefinito Offline può essere personalizzato con un'immagine:

![Schermata sito non disponibile](../../../en/images/configuration/site-offline.png)

L'interruttore Sito Non Disponibile non si applica all'interfaccia amministrativa e gli utenti che possono accedere al backend possono continuare a fare login anche al frontend. L'accesso al frontend è negato solo agli utenti nei gruppi di utenti Registrato, Autore, Editore e Pubblicatore.

## Per Attivare Offline

- Seleziona **Home Dashboard → Configurazione Globale** dal menu Amministratore.
- Nella scheda **Sito** imposta l'interruttore **Sito Offline** su **Sì**.
- Puoi quindi scegliere di utilizzare
  - **Usa Messaggio Personalizzato**, che è il testo nella casella Messaggio Personalizzato. Oppure...
  - **Il Messaggio Predefinito della Lingua del Sito**, che è **Questo sito è in manutenzione. Si prega di riprovare più tardi.** in inglese o l'equivalente nella lingua selezionata del Sito. Questo permette anche di selezionare un'immagine. Oppure...
  - **Nascondi** per non mostrare alcun messaggio.
- Seleziona **Salva e Chiudi** dalla Barra degli Strumenti.
- Esegui tutta la manutenzione necessaria.
- Torna al modulo di Configurazione Globale.
- Imposta l'interruttore Sito Offline su **No**.
- Seleziona **Salva e Chiudi** dalla Barra degli Strumenti.

## Tutti gli utenti

Puoi limitare l'accesso al tuo sito web proteggendo con password la directory di Joomla. Solo gli utenti che conoscono il nome utente e la password per l'accesso alla directory potranno accedere al sito. Puoi configurare più di un utente. Con il Pannello di Controllo di Hosting cPanel:

- Accedi al tuo account cPanel.
- Nella sezione File, seleziona **Privacy delle Directory**.
- Se la root del tuo sito si trova in una sottodirectory di public_html
  - Seleziona la directory public_html
- Seleziona il pulsante Modifica per la directory che contiene il tuo sito
  (public_html se il tuo sito si trova nella root web).
- Seleziona la casella di controllo **Proteggi con password questa directory.**
- Inserisci un nome per la directory protetta: il predefinito potrebbe essere sufficiente.
- Seleziona il pulsante **Salva**.
- Verrà mostrata una pagina con un messaggio di successo e un link Torna Indietro, selezionalo.
- Crea un utente per l'accesso alla directory protetta.
- Inserisci un nome utente
- Inserisci una password e ripetila (ricordala o segnala).
- Seleziona il pulsante **Salva**.

Ora, verifica che la directory richieda una password per l'accesso via web. Quando visiti il tuo sito, ti verrà richiesto di inserire il nome utente e la password di accesso alla directory. Questi potrebbero essere completamente diversi dal nome utente e dalla password di Joomla.

Per rimuovere la protezione con password della directory:

- Accedi al tuo account cPanel.
- Nella sezione File, seleziona **Privacy delle Directory**.
- Se la root del tuo sito si trova in una sottodirectory di public_html
  - Seleziona la directory public_html
- Seleziona il pulsante **Modifica** per la directory che contiene il tuo sito
  (public_html se il tuo sito si trova nella root web). Ora mostrerà un simbolo di lucchetto e Sì sotto l'intestazione Privata.
- **Deseleziona** la casella di controllo **Proteggi con password questa directory.**
- Seleziona il pulsante **Salva**.

Per verificare che la protezione con password sia stata rimossa, utilizza un browser diverso per accedere al tuo sito o chiudi e riapri il browser esistente e poi accedi nuovamente al tuo sito.

