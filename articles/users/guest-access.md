<!-- Filename: J4.x:Guest_Access / Display title: Accesso Ospiti  -->

## Livelli di Accesso

I visitatori del sito possono visualizzare elementi come articoli, moduli e voci di menu perché quegli elementi sono assegnati per impostazione predefinita al livello di accesso Pubblico. Questo livello di accesso consente anche agli utenti loggati di visualizzare gli stessi elementi di contenuto. Tuttavia, ci sono occasioni in cui non è appropriato per un utente loggato visualizzare un elemento di contenuto. Ad esempio, una voce di menu di Login dovrebbe essere vista dagli utenti che non sono loggati ma non dagli utenti che sono loggati. Questo è il motivo per cui esiste il livello di accesso Ospite. Gli utenti loggati dovrebbero invece vedere una voce di menu di Logout. Tali elementi devono essere assegnati al livello di accesso Registrato.

In alcuni casi è anche opportuno limitare l'accesso a un articolo o un modulo agli utenti che non sono loggati o agli utenti che sono loggati.

## Accesso Ospite

L'uso del livello di accesso Ospite può essere illustrato con un elemento di menu Login:

- Seleziona **Menu → Menu Principale → +** dal menu Amministratore. Utilizza il menu che preferisci per i nuovi elementi.
- Nel modulo **Menu: Nuovo Elemento**, inserisci un titolo adatto nel campo **Titolo**, ad esempio **Login**.
- Nel campo **Tipo di Elemento di Menu** utilizza il pulsante **Seleziona** per aprire la finestra di dialogo popup Tipo di Elemento di Menu.
- Nella lista **Tipo di Elemento di Menu** seleziona la sezione Utenti e seleziona l'elemento **Modulo di Login**.
- Tornato nel modulo **Menu: Nuovo Elemento**, imposta il campo **Accesso** su **Ospite**.
- Salva
- Facoltativamente, seleziona la lista Ordine e seleziona l'elemento **dopo** il quale desideri che l'elemento Login appaia.

![form del menu di login limitato all'accesso ospite](../../../en/images/users/guest-access-menu-login.png)

- Salva e Chiudi.
- Visualizza il sito. Verifica che l'elemento di menu Login funzioni. Controlla che scompaia dopo il login.  

## Accesso Registrato

L'uso del livello di accesso Registrato può essere illustrato con un elemento di menu Logout:

- Seleziona **Menu → Menu Principale → +** dal menu dell'Amministratore. Utilizza il menu che preferisci per i nuovi elementi.
- Nel modulo **Menu: Nuovo Elemento**, inserisci un titolo adatto nel campo **Titolo**, ad esempio **Logout**.
- Nel campo **Tipo di Voce di Menu** utilizza il pulsante **Seleziona** per aprire la finestra di dialogo popup Tipo di Voce di Menu.
- Nell'elenco **Tipo di Voce di Menu** seleziona la sezione Utenti e scegli l'elemento **Logout**.
- Tornando al modulo **Menu: Nuovo Elemento**, imposta il campo **Accesso** su **Registrato**.
- Salva
- Facoltativamente, seleziona il menu a tendina Ordinamento e scegli l'elemento **dopo** il quale desideri che appaia l'elemento Login.

![modulo menu logout limitato all'accesso registrato](../../../en/images/users/guest-access-menu-logout.png)

- Salva e Chiudi.
- Visualizza il sito. Verifica che l'elemento del menu Logout funzioni. Verifica che scompaia dopo il logout.

