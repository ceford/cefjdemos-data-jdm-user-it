<!-- Filename: J3.x:Plugin_Joomla_Update_Notification / Display title: Notifica di aggiornamento Joomla!  -->

## Icona e Attività

Ci sono due plugin con nomi simili:

* **Icona Rapida - Notifica Aggiornamento Joomla!**
* **Attività - Notifica Aggiornamento Joomla!**

Il primo controlla gli aggiornamenti di Joomla e ti notifica quando visiti la pagina del pannello di controllo principale. Ha un parametro: il Gruppo di questo plugin (questo valore viene confrontato con il valore del gruppo utilizzato nei moduli di Icone Rapide per inserire icone).

Il secondo controlla periodicamente la disponibilità di nuove versioni di Joomla! Quando ne viene trovata una, attiva un'attività per inviare un'email di promemoria per l'aggiornamento ai Super Utenti. L'email può essere personalizzata tramite *Sistema → Modelli di Posta*.

Le email inviate dai plugin del Sistema di Notifica Aggiornamento Joomla! sono intese ad aiutare a mantenere il software aggiornato, il che aiuta il sito web a rimanere sicuro. Gli aggiornamenti dovrebbero essere installati il prima possibile dopo il rilascio.

## Stato del Plugin

I due plugin separati possono essere abilitati o disabilitati.

- Con **Icona Rapida ... Disabilitata** l'icona *Verifica Joomla ...* nella Dashboard Principale rimane inattiva, anche se puoi selezionarla per andare alla pagina di aggiornamento di Joomla.
- Con **Attività ... Disabilitata:** l'attività per inviare un'email non viene attivata.

## Parametri dell'attività

Dal menu Amministratore, vai a **Sistema / Attività pianificate** e seleziona l'elemento **Notifica aggiornamenti** dall'elenco *Attività pianificate*. Ci sono diverse schede di parametri e informazioni lì per visualizzare e modificare, se appropriato.

### Frequenza delle email di notifica

La frequenza di esecuzione dell'attività è impostata a 24 ore per impostazione predefinita. Ciò significa che il sito Joomla controllerà un aggiornamento del core e di tutte le estensioni, plugin, moduli e template installati a intervalli di 24 ore. Un valore di 0 invierebbe un'email di aggiornamento ogni volta che il sito è accessibile. 0 è solo per il testing!

Nota che l'attività è attivata dall'attività sul sito. Se sei l'unico utente, sarà attivata alla tua prossima visita se questa supera le 24 ore.

### Email degli utenti Super

La notifica via email viene inviata solo agli utenti che hanno il privilegio di Super User. Questo campo ti consente di selezionare quali Super User riceveranno le notifiche via email.

- Se lasciato vuoto, tutti i Super User del sito riceveranno l'email di notifica dell'aggiornamento.
- Per limitare quali Super User riceveranno la notifica dell'aggiornamento, inserisci qui gli indirizzi email per i Super User. Se ci sono più indirizzi email di Super User, usa una virgola per separarli.

### Lingua dell'email

La notifica può essere inviata in qualsiasi lingua tu stia utilizzando nel tuo sito.

- **Auto (predefinito)** invia l'email di notifica dell'aggiornamento nella lingua predefinita del sito.
- Selezionare una lingua diversa da Auto (predefinito) forza l'invio delle email di notifica degli aggiornamenti in questa lingua specifica.

## Suggerimenti

- Per disattivare le notifiche email degli aggiornamenti di Joomla! è sufficiente disabilitare il plugin.
- L'oggetto e il testo del corpo dell'email possono essere modificati tramite la lista **Sistema / Modelli Email**. Seleziona l'elemento **Joomla: Notifica di Aggiornamento**. In un sito multilingue, sarà nella lingua attualmente selezionata.
  - **Oggetto** Nota che i segnaposto {SITENAME} – {URL} sono sostituiti quando il messaggio viene inviato.
  - **Corpo** Ci sono altri segnaposto anche lì!

*Tradotto da openai.com*

