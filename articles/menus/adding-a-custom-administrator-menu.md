<!-- Filename: J4.x:Adding_a_Custom_Administrator_Menu / Display title: Menu Personalizzato dell'Amministratore  -->

## Introduzione

Supponiamo che tu abbia un utente a cui desideri consentire di eseguire un solo compito sul tuo sito web. Prendiamo il caso di un'organizzazione che ha filiali in tutto il mondo e l'unico compito che ogni filiale è autorizzata a svolgere è quello di posizionare le località su una mappa per la visualizzazione sul sito. Il componente per questo compito è Ffmap, ma non sarà trattato qui a parte gli elementi del menu Amministratore coinvolti.

Per realizzare questo compito è necessario creare un Gruppo Utenti personalizzato, assegnare un utente a quel gruppo e creare un menu personalizzato da utilizzare da parte di quell'utente.

## Creare un Gruppo Utenti

- Seleziona **Utente → Utenti → Gruppi** nel menu Amministratore.
- Seleziona il pulsante **Nuovo** nella Toolbar.
  - Inserisci un **Titolo *per il Gruppo,*** *Filiale* in questo caso.
  - Seleziona **Pubblico** come gruppo principale. Questo è importante - non vuoi ereditare i permessi da un altro gruppo.
- Seleziona **Salva e Chiudi** dalla Toolbar.

## Imposta le autorizzazioni globali per il gruppo

- Seleziona **Configurazione Globale** dalla Dashboard Home.
- Seleziona la scheda **Permessi**.
- Seleziona l'elemento **Branch**.
- Imposta **Accesso Amministratore** su **Consentito**.
- Seleziona **Salva e Chiudi** dalla barra degli strumenti.

A questo punto, qualsiasi utente assegnato al gruppo di utenti Branch sarà in grado di accedere all'interfaccia Amministratore e vedere la Dashboard Home. Potrebbero esserci moduli della dashboard visibili perché il loro livello di accesso è stato impostato su Pubblico, ad esempio: Utenti Connessi, Articoli Popolari e Articoli Aggiunti di Recente. È meglio impostare l'accesso a questi moduli su Speciale. Non ci saranno voci di menu visibili per l'utente.

## Impostare i Permessi del Componente per il Gruppo

Opzioni:

- Seleziona il componente **Ffmap** nel menu Amministratore.
- Seleziona il pulsante **Opzioni** di FFmap dalla barra degli strumenti per aprire la sua schermata di Configurazione.

Oppure:

- Seleziona **Configurazione Globale** dalla Home Dashboard.
- Seleziona Ffmap dall'elenco dei componenti.

Poi:

- Seleziona la scheda **Permessi** e quindi l'elemento **Branch**.
- Imposta Interfaccia di Accesso Amministrazione, Crea, Elimina, Modifica, Modifica Stato, Modifica Proprio e Modifica Valore Campo Personalizzato su **Consentito**.
- Seleziona **Salva e Chiudi** dalla barra degli strumenti.

## Creare un nuovo menu Amministratore

- Seleziona **Menu → Gestisci** dal menu Amministratore.
- Seleziona **Amministratore** dal menu a discesa Sito/Amministratore.
- Seleziona il pulsante **Nuovo** dalla Barra degli strumenti.
- Inserisci un titolo per il menu, ad esempio **Menu Filiale** e un id univoco, ad esempio **menu-filiale**.
- Seleziona **Salva e Chiudi** dalla Barra degli strumenti.

## Creare un Modulo per il menu

Nell'elenco dei menu, seleziona il pulsante **Moduli Collegati** nel record del Menu Filiale.

- Inserisci un Titolo per il modulo, ad esempio **Menu Filiale**.
- Seleziona Menu da Mostrare: **Menu Filiale**.
- Imposta Controlla Menu su **No**, altrimenti ci sono messaggi di avviso riguardo alle funzioni di Amministratore mancanti.
- Seleziona la posizione: **menu**.

## Creare un Contenitore del Menu Componenti

- Nella lista dei menu, seleziona l'icona degli Elementi del Menu per il Menu Filiale. Questo
  aprirà la lista degli elementi, che sarà vuota in questa fase.
- Seleziona il pulsante **Nuovo** dalla Barra degli strumenti.
- Inserisci un titolo per l'elemento del menu: **Componenti Filiale**.
- Seleziona il Tipo di Elemento del Menu **Seleziona Pulsante**.
  - Nella finestra di dialogo modale, scorri verso il basso fino all'elemento **Link di Sistema** e
    espandi il pannello.
  - Seleziona il tipo di elemento **Contenitore del Menu Componenti**.
- Tornando al modulo di configurazione del menu, seleziona **Mostra Nessuno** per nascondere tutti
  gli elementi del menu Componenti (rosso).
- Scorri verso il basso fino agli elementi Ffmap e clicca sui pulsanti Nascondi per passarli
  a Mostra (verde).
- Seleziona **Salva e Chiudi** dalla Barra degli strumenti.

## Schermata

![selezione componente menu amministratore personalizzato](../../../en/images/menus/menus-custom-administrator-menu.png)

## Risultato

Crea un utente nel Gruppo di Filiali per te stesso per effettuare un test. Accedi all'interfaccia amministrativa come quell'utente per vedere il risultato:

![risultato menu amministratore personalizzato](../../../en/images/menus/menus-custom-administrator-menu-result.png)

## Note

Se in seguito aggiungi un altro componente, verrà aggiunto al Menu Componenti Contenitore ed sarà visibile per impostazione predefinita. Sarà necessario tornare alla voce di menu dell'Amministratore e impostare il nuovo contenuto su Nascondi.

Se il componente è configurato per includere voci di menu in ciascuna delle visualizzazioni elenco dell'Amministratore, includendo i file default.xml, potresti aggiungere voci di menu direttamente al menu personalizzato ed evitare di utilizzare il Menu Componenti Contenitore.

Il menu dei Componenti Branch rimarrà parte del menu Amministratore - duplicazione inevitabile!

*Tradotto da openai.com*

