<!-- Filename: J4.x:User_Password_Reset / Display title: Reimpostazione Password Utente  -->

## Ripristino Utente

Se ai tuoi utenti è consentito l'accesso al sito e un utente non riesce a ricordare il Nome utente o la Password, è meglio richiedere all'individuo di reimpostare autonomamente le credenziali utilizzando i link presenti nel modulo di accesso:

![modulo di accesso utente sito](../../../en/images/users/user-site-login-module.png)

In ogni caso, selezionando un link si accede a un modulo per l'inserimento dell'indirizzo email associato all'account:

![modulo di reimpostazione password dimenticata sito](../../../en/images/users/user-forgot-password-reset.png)

L'intero processo è compiuto dall'utente senza alcun intervento da parte di un Amministratore. Questo è il modulo di verifica della password dimenticata:

![modulo di conferma password dimenticata sito](../../../en/images/users/user-forgot-password-confirm.png)

Infine, all'utente viene richiesto di inserire una nuova password:

![modulo di completamento reimpostazione password dimenticata sito](../../../en/images/users/user-forgot-password-complete.png)

## Reimpostazione dell'Amministratore

Se c'è solo l'accesso come Amministratore, il reset della password di un utente deve essere eseguito da un Super Utente o da un Amministratore. Se l'unico Super Utente non conosce le credenziali di accesso, consultare l'articolo separato sul Recupero della Password dell'Amministratore. Altrimenti:

- Seleziona **Utenti → Gestisci** dal menu Amministratore o seleziona
  *Utenti* dal pannello della Home Dashboard del Sito.
- Trova l'utente che ha bisogno di un reset della password.
- Seleziona il **Nome** collegato per aprire il modulo *Utente: Modifica*.
- Inserisci una nuova password nei campi Password e Ripeti Password.
- Imposta il campo **Richiedi Reset della Password** su *Sì*.
- **Salva & Chiudi**

![modulo di modifica utente degli amministratori](../../../en/images/users/users-edit-user-john-doe.png)

Dovrai quindi inviare un'email all'utente con la nuova password temporanea in testo semplice. Dopo il login, l'utente potrà vedere la pagina Home del sito, ma ogni tentativo di navigare verso un'altra pagina lo porterà al modulo per la nuova password.

