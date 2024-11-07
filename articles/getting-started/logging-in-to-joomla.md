<!-- Filename: J4.x:Logging_in_to_Joomla / Display title: Accesso a Joomla -->

## Introduzione

Una delle grandi qualità di Joomla! è che offre la flessibilità di eseguire attività tramite la Dashboard Amministrativa (spesso denominata backend) e, se abilitato, eseguire attività direttamente dal frontend (la parte pubblica) del sito web.

L'accesso frontend è un modo semplice ed efficiente per consentire ai redattori di contenuti di aggiungere o modificare rapidamente articoli senza la necessità di accedere alla Dashboard Amministrativa.

Il login in Joomla è configurato per controllare cosa gli utenti possono vedere e fare (o non possono fare) usando il componente Utente di Joomla e i potenti Livelli di Controllo Accessi (ACL). Questo significa che un sito web Joomla può avere utenti che utilizzano solo il backend, alcuni che utilizzano solo il frontend e altri che utilizzano entrambi.

Di seguito viene illustrato come effettuare l'accesso e la disconnessione sia dal backend che dal frontend di un sito web Joomla.

**Nota:** Un amministratore Joomla potrebbe aver disabilitato l'accesso frontend, richiedendo che tutte le attività vengano eseguite utilizzando la Dashboard Amministrativa del backend.

### Login Amministratore

Vai alla pagina di Login Amministratore. Questo è l'indirizzo web del sito a cui si aggiunge /administrator, ad esempio, my-joomla-website.com/administrator, che apre la pagina di login dell'Amministratore di Joomla:

![Modulo di login dell'amministratore](../../../en/images/getting-started/logging-in-to-joomla-administrator-login-form.png)

1. Inserisci il tuo **Nome utente**
2. Inserisci la tua **Password**

Seleziona il pulsante **Accedi** per essere portato alla Home Dashboard di Joomla!.

**Nota:**

1. Joomla fornisce un'opzione per configurare e utilizzare l'Autenticazione Web. 
   Questo non è trattato all'interno di questo tutorial.
2. Se un sito ha più lingue installate, sarai in grado di selezionare una lingua da usare da un elenco a discesa prima di accedere.

### Logout Amministratore

Per disconnettersi, seleziona il **Menu Utente** e poi **Esci**.

![Link per il logout dell'amministratore](../../../en/images/getting-started/logging-in-to-joomla-logout-link.png)

### Login del Sito

Se l'accesso frontend è abilitato, un modulo di login sarà stato aggiunto al sito. Joomla consente diversi modi per farlo. Una installazione standard include un modulo di login nella barra laterale del sito, ma potresti trovare un link aggiunto al menu del sito, o forse nel footer. In alcuni casi potrebbe esistere un link *Crea Pagina*. Il design del sito indicherà dove accedere al modulo di login.

Questo esempio utilizza un modulo di login situato nella barra laterale destra.

![Modulo di login del sito](../../../en/images/getting-started/logging-in-to-joomla-site-login-form.png)

Nel **Modulo di Login**

1. Inserisci il tuo **Nome utente**
2. Inserisci la tua **Password**

Seleziona il pulsante **Accedi**.

Quando accedi dal frontend del sito, potresti rimanere sulla stessa pagina da cui hai effettuato l'accesso oppure potresti essere portato alla tua pagina Profilo. Noterai che il modulo di login conterrà anche un pulsante **Esci**.

### Logout del Sito

![Modulo di logout del sito](../../../en/images/getting-started/logging-in-to-joomla-site-logout-form.png)

Per disconnettersi, vai al modulo di login e seleziona il pulsante **Esci**.  

## Suggerimenti

- Alcuni amministratori di siti Joomla installano estensioni che nascondono o
  limitano l'accesso al pannello di controllo amministrativo nel backend. Potrebbe essere necessario
  eseguire passaggi aggiuntivi o visitare un URL di accesso alternativo.
- Se stai effettuando modifiche utilizzando l'accesso frontend, risparmia tempo effettuando il login
  direttamente sulla pagina che desideri modificare.

