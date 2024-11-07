<!-- Filename: J4.x:Privacy_Workflow / Display title: Flusso di lavoro sulla privacy  -->

## Creazione di una Richiesta

Elaborare le richieste per informazioni personali è lo scopo principale del componente di privacy. Gli utenti possono chiedere un riepilogo dei loro dati personali o richiedere che tutti i loro dati personali vengano rimossi. Una richiesta può essere creata sia da un utente autenticato attraverso il modulo di richiesta sia da un super utente.

In questo contesto, un utente si riferisce a qualsiasi individuo o organizzazione che ha fatto una richiesta, indipendentemente dal fatto che ci sia un account utente registrato. Ad esempio, le richieste possono pervenire all'amministratore del sito da individui o organizzazioni aggiunti al sito come contatti.

I dati personali si basano sugli indirizzi email e l'elaborazione automatizzata è limitata alle estensioni che riportano le capacità di privacy.

*IMPORTANTE* Per creare ed elaborare richieste di informazioni, il tuo sito web DEVE essere in grado di inviare email a causa del requisito per il proprietario dell'informazione di confermare la richiesta.

### Richiesta da Utente Autenticato

Gli utenti registrati possono inviare una richiesta d'informazioni tramite un link di menu *Richiesta di Informazioni sulla Privacy* disponibile solo dopo il login. Un buon posto per tale link è nello stesso menu dove si trova il collegamento alla **Privacy Policy** del sito. Un menu in fondo alla pagina nel piè di pagina del sito è spesso una posizione preferita. Quando si invia una richiesta di informazioni, l'utente deve fornire:

- Il tipo di richiesta: Esporta o Rimuovi selezionato dalla lista a discesa.

![flusso di lavoro privacy richiesta utente](../../../en/images/privacy/privacy-workflow-user-request.png)

Al momento dell'invio, un messaggio indica che la richiesta è stata accettata e una email di verifica è in arrivo:

![flusso di lavoro privacy richiesta utente accettata](../../../en/images/privacy/privacy-workflow-user-request-accepted.png)

oppure che *La tua richiesta di informazioni non può essere creata. C'è già una richiesta di informazioni attiva per questo indirizzo email e tipo di richiesta. Si prega di contattare il proprietario del sito per aggiornamenti su questa richiesta.*

### Creazione da Super Utente

Attraverso la pagina **Privacy: Richieste di Informazioni**, qualsiasi super utente può creare una nuova richiesta di informazioni. Questo è l'unico modo per creare richieste di informazioni per utenti che NON hanno account sul sito. Per creare una richiesta:

- Seleziona **Utenti → Privacy → Richieste** dal menu Amministratore.
- Seleziona il pulsante **Nuovo** dalla Toolbar.
- Nel campo **Email** inserisci l'indirizzo email dell'utente.
- Nel campo **Tipo di Richiesta** seleziona Esporta o Rimuovi dalla lista a discesa.
- **Salva e Chiudi**.

Una volta creata, la richiesta non può essere modificata. Può solo essere Invalidata o Elaborata.

## Conferma di una Richiesta

Una volta creata una richiesta, indipendentemente da come viene creata, l'utente riceverà un'email contenente un link a un modulo di conferma.

![flusso di lavoro sulla privacy conferma richiesta utente](../../../en/images/privacy/privacy-workflow-user-request-confirm.png)

L'utente deve inserire il token fornito nell'email e inviare il modulo. Il token è valido per 24 ore. Se una richiesta non viene confermata entro tale intervallo di tempo, verrà contrassegnata come **Non valida** nell'elenco delle Richieste di Privacy e dovrà essere presentata una nuova richiesta.

Una volta che l'utente conferma la richiesta, un'email verrà inviata ai Super Utenti per indicare che è necessaria un'azione.

- Selezionare **Utenti → Privacy → Richieste** dal menu Amministratore.
- Le richieste che richiedono azione verranno contrassegnate come **Confermate**.

![flusso di lavoro sulla privacy elenco richieste di informazioni](../../../en/images/privacy/privacy-workflow-information-requests-list.png)

## Elaborazione di una Richiesta di Esportazione

Una volta che una richiesta di esportazione è stata confermata, ci sono due azioni disponibili per gli utenti avanzati.

- Esporta Dati: Questa operazione raccoglierà tutti i dati relativi al soggetto della richiesta di informazioni e creerà un file XML che sarà scaricato sul tuo computer. Questo è utile per permettere ai proprietari del sito di rivedere i dati dell'esportazione prima di inviarli all'utente.
- Invia Email con Dati di Esportazione: Questa operazione raccoglierà tutti i dati relativi al soggetto della richiesta di informazioni, creerà un file XML (lo stesso generato dall'azione Esporta Dati), e invierà un'email all'utente con il file dei dati esportati allegato.

**Importante:** L'azione di esportazione può raccogliere dati solo dalle estensioni che supportano la privacy. Pertanto, l'utente avanzato che sta agendo sulla richiesta dovrebbe rivedere l'esportazione e, se necessario, includere i dati contenuti in estensioni che memorizzano dati personali ma che non hanno supporto per la privacy.

## Elaborazione di una Richiesta di Rimozione

Una volta confermata una richiesta di rimozione, c'è solo un'azione disponibile per i super utenti.

- Elimina Dati: Questo processo renderà anonimi e/o rimuoverà i dati relativi al soggetto dell'informazione. Per le richieste in cui il proprietario delle informazioni possiede anche un account utente registrato, questo processo renderà anonimi il nome dell'account, il nome utente e l'indirizzo email, oltre a bloccare l'accesso all'account e terminare la sessione sul sito se l'utente è connesso al momento dell'elaborazione della richiesta.

**Importante:** L'azione di eliminazione può raccogliere dati solo da estensioni che supportano la privacy. Pertanto, il super utente che esegue la richiesta dovrebbe rivedere l'esportazione e, se necessario, rendere anonimi o rimuovere manualmente i dati contenuti nelle estensioni che conservano dati personali ma non supportano la privacy.

Alla selezione del pulsante **Elimina Dati**, compare un messaggio di conferma **Dati Rimossi** ma l'elenco delle Richieste di Informazioni sulla Privacy rimane invariato. I dati utente vengono rimossi o anonimizzati, ma non i dati nelle tabelle \#\_\_action_logs, \#\_\_messages e \#\_\_privacy_requests (vedi sotto).

## Completare una Richiesta

Dopo che la richiesta è stata elaborata, dovrebbe essere contrassegnata come completata. Questo indicherà che la richiesta è stata soddisfatta e non sono necessarie ulteriori azioni.

- Nella lista **Privacy: Richieste di Informazioni**, seleziona l'indirizzo email della richiesta in fase di elaborazione.
- Nel modulo **Privacy: Revisione Richiesta di Informazioni**:
  - Esamina i dati.
  - Seleziona il pulsante appropriato **Esporta**, **Email** o **Elimina** dalla Barra degli Strumenti se non è già stato fatto dalla vista elenco.
- Seleziona il pulsante **Completa** dalla Barra degli Strumenti (o il pulsante **Invalida** se si ritiene che la richiesta sia invalida).

![flusso di lavoro sulla privacy per la revisione delle richieste di informazioni](../../../en/images/privacy/privacy-workflow-review-information-request.png)

## Infine

Per rimuovere i dati del Registro Azioni Utente:

- Seleziona **Utenti → Registro Azioni Utente** dal menu Amministratore.
- Cerca il nome utente o l'indirizzo email dell'utente eliminato.
- Seleziona la casella di controllo **Seleziona tutti gli elementi**.
- Seleziona il pulsante **Elimina** nella Barra degli strumenti.

Per rimuovere i dati dei Messaggi Privati e i dati delle Richieste di Privacy:

- Non esiste un modo semplice per rimuovere in blocco nessuno di questi tipi di dati
  all'interno di Joomla. Il metodo più rapido è cercare il Nome utente
  (indirizzo email) nel database con phpMyAdmin e cancellare i record
  lì. Ecco un esempio di schermata:

![elimina flusso di lavoro privacy con phpmyadmin](../../../en/images/privacy/privacy-workflow-delete-with-phpmyadmin.png)

## Risorse aggiuntive

- [Guida per sviluppatori per la Suite di strumenti per la privacy](https://docs.joomla.org/Special:MyLanguage/J3.x:Integrate_Extensions_with_the_Privacy_Component)

*Tradotto da openai.com*

