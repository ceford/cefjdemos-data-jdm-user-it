<!-- Filename: J4.x:User_Registration / Display title: Registrazione Utente   -->

## Politica di Registrazione

In un sito Joomla, gli utenti registrati possono accedere per visualizzare contenuti 
o interagire con contenuti che gli utenti non registrati non possono vedere o utilizzare. L'accesso al sito e l'accesso all'amministratore sono gestiti separatamente, sebbene esista un'impostazione nella Configurazione Globale che permette di combinarli. Alcuni siti hanno un numero limitato di utenti creati da un Amministratore. Altri siti hanno così tanti utenti che è necessario che si registrino e attivino da soli i propri account. Il modo in cui gli utenti si registrano al tuo sito è configurato nel modulo *Utenti: Opzioni*.

## Permetti l'Auto-Registrazione

L'auto-registrazione degli utenti è disabilitata per impostazione predefinita. Qualsiasi nuovo
utente deve essere creato da un Manager o Amministratore. L'auto-registrazione
può essere consentita con alcune semplici modifiche al modulo *Utenti: Opzioni*.

- Seleziona **Utenti → Gestisci** dal menu Amministratore.
- Seleziona il pulsante *Opzioni* dalla Barra degli strumenti.
- Imposta **Consenti Registrazione Utente** su **Sì**.
- Il **Gruppo Registrazione Nuovo Utente** dovrebbe essere **- Registrato -**
  a meno che non ci sia una buona ragione per cui sia diverso.
- L'**Attivazione Nuovo Account Utente** dovrebbe essere **Self** o
  **Amministratore**.
  - Self: L'utente riceverà un'email con un link di attivazione. L'account
    sarà attivato quando l'utente cliccherà sul link di attivazione.
  - Amministratore: L'utente riceverà un'email con un link di attivazione.
    Quando l'utente cliccherà su questo link, l'Amministratore del Sito sarà
    notificato via email. L'Amministratore del Sito dovrà poi attivare
    l'account dell'utente.

![Opzioni utente della scheda di configurazione utente](../../../en/images/users/users-configuration-user-options.png)

- **Salva & Chiudi**
- Aggiungi un modulo *Login*. Oppure
- Aggiungi un elemento di menu *Utenti: Modulo Login* e un elemento di menu *Utenti: Logout*.

## Disabilita Registrazione Autonoma

- Imposta **Consenti Registrazione Utente** su **No**.

## Aggiunta di un Nuovo Utente

Se l'auto-registrazione non è consentita, ogni nuovo utente deve essere creato da un Amministratore. Procedere come segue:

- Selezionare l'icona **Users +** nel pannello Home Dashboard Site. Oppure
- Selezionare **Utenti**→**Gestisci +** dal menu Amministratore.
- Compilare il modulo **Dettagli Nuovo Utente**. La maggior parte dei campi ha valori di default adeguati.

![Pagina di inserimento dati per il nuovo utente](../../../en/images/users/users-new-user.png)

- Selezionare la scheda **Gruppi Utenti Assegnati** e spuntare la casella del gruppo utente desiderato. Registrato è selezionato di default.
- **Salva & Chiudi**.
- Nella lista degli utenti, verificare che il nuovo account utente sia Abilitato (spunta verde nelle colonne Abilitato).

## Bloccare un Utente

Il miglior metodo per gestire un utente problematico è disabilitare l'account utente piuttosto che cancellarlo. Questa misura può essere utilizzata per sospendere l'utente e può essere annullata se l'utente promette di comportarsi bene. Cancellare un account spezzerebbe qualsiasi collegamento ai contenuti forniti dall'utente, come la paternità degli articoli, e potrebbe offrire all'utente la possibilità di registrarsi nuovamente con lo stesso indirizzo email.

Per bloccare un utente:

- Seleziona **Utenti → Gestisci** dal menu dell'Amministratore.
- Trova l'utente nell'elenco *Utenti*. Utilizza il filtro testuale se necessario.
- Seleziona l'icona Abilitato che appare come un segno di spunta verde vicino al nome utente. Un'etichetta **Blocca** appare al passaggio del mouse.

![Pagina di inserimento dati nuovo utente](../../../en/images/users/users-hover-block.png)

- Seleziona l'icona *Abilitato*. La pagina si ricaricherà con l'icona Abilitato che appare come una croce grigia.  

## Sbloccare un Utente

Semplice:

- Cambia l'icona *Abilitato* di nuovo a un segno di spunta verde.

*Tradotto da openai.com*

