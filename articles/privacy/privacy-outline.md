<!-- Filename: Help4.x:Components_Privacy_Outline / Display title: Schema della Privacy -->

## Contenuto

La Suite Strumenti per la Privacy di Joomla è composta dalle seguenti parti:

- **Componente Amministratore** Gestisce le richieste di riservatezza delle informazioni utente.
- **Modulo - Pannello Privacy** Posiziona un pannello Privacy sulla Dashboard Home.
- **Modulo - Richieste di Privacy** Posiziona un pannello delle Richieste di Privacy sulla Dashboard Privacy.
- **Modulo - Stato della Privacy** Posiziona un pannello dello Stato della Privacy sulla Dashboard Privacy.
- **Voce di Menu - Crea Richiesta** Mostra un modulo per visualizzare una Richiesta di Informazioni. Da creare.
- **Plugin - Sistema - Consenso Privacy** Aggiunge campi di consenso ai moduli di informazioni personali come la Registrazione. Da abilitare.
- **Plugin - Utente - Termini e Condizioni** Richiede il consenso dell'utente ai termini e condizioni del sito. Da abilitare.
- **Plugin - Contenuto - Conferma Consenso** Aggiunge una casella di controllo obbligatoria a un modulo, ad esempio il modulo di contatto principale. Da abilitare.
- **Plugin - Privacy - Vari** Altri plugin, abilitati per impostazione predefinita, senza parametri significativi da impostare.

All'installazione la Suite Strumenti per la Privacy è pronta per l'uso da parte dell'Amministratore senza abilitare plugin o creare una voce di menu.

## Flusso di lavoro

Questa è una tipica sequenza di eventi:

- Arriva una richiesta di informazioni. Deve includere un indirizzo email valido per un Soggetto dei dati. Il Soggetto non deve necessariamente essere un utente registrato. Ad esempio, il Soggetto potrebbe essere un contatto aggiunto da un Amministratore.
- Se il messaggio non è inviato dal Soggetto tramite un modulo di Informazioni Personali del sito:
  - L'Amministratore va su **Utenti → Privacy → Richieste → Nuova** per creare una nuova richiesta di informazioni. Viene inviato un messaggio all'indirizzo email fornito invitando il Soggetto a confermare che si tratta di una richiesta genuina.
- Se il messaggio è inviato tramite un modulo di Informazioni Personali del sito, viene inviato automaticamente al Soggetto un messaggio di richiesta di conferma.
- Il Soggetto seleziona il link nel messaggio email per aprire il modulo di conferma. Al momento dell'invio, il Soggetto vede un messaggio di conferma.
- L'Amministratore vede che nei Messaggi Privati nella Barra del Titolo ci sono messaggi in attesa. Ci sarà anche un messaggio email del sistema.
- L'Amministratore va su **Utenti → Privacy → Richieste** e vede che lo stato della richiesta è cambiato in **Confermato**.
- Per una richiesta di Esportazione dati ci sono i pulsanti adiacenti Esporta e Email.
  - L'Amministratore seleziona il pulsante Esporta per dare un'occhiata ai dati da esportare. Questi sono in formato XML ma vengono visualizzati correttamente in Firefox.
  - L'Amministratore seleziona il pulsante Email per inviare i dati esportati al Soggetto.
- Per una richiesta di Rimozione dati c'è un pulsante Elimina adiacente.
  - L'Amministratore seleziona il pulsante elimina per anonimizzare i dati per l'utente. L'utente non potrà più effettuare il login.
- Seleziona l'indirizzo email del Soggetto dei dati per aprire il modulo di Revisione della Richiesta di Informazioni.
- Seleziona il pulsante Completa nella Barra degli Strumenti.
- L'elenco delle Richieste di Informazioni mostra lo Stato come Completato e i pulsanti Azione sono scomparsi.

Nota che questa suite non visualizza un modulo di autorizzazioni per i Cookie.

