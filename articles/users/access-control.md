<!-- Filename: J4.x:Access_Control / Display title: Controllo Accessi   -->

## Introduzione

Joomla ha un meccanismo sofisticato per controllare chi può vedere e manipolare il contenuto su un sito Joomla. La parte del **chi** è impostata nelle opzioni del componente Utenti con Gruppi di Utenti e Livelli di Accesso. La parte del **manipolare** è impostata nei Permessi di Azione, sia nelle impostazioni di Configurazione Globale che nelle impostazioni del Componente o nelle impostazioni dell'Elemento. Ad esempio, i valori predefiniti impostati nei Permessi Globali possono essere sovrascritti nei Permessi degli Articoli (tutti gli articoli) e i Permessi degli Articoli possono essere sovrascritti nei Permessi dell'Articolo individuale.

## Gruppi di Utenti

I Gruppi di Utenti sono utilizzati per dividere gli utenti del sito in gruppi con diverse responsabilità. Ad esempio, i membri del gruppo di utenti Autore hanno il permesso di accedere al sito, creare articoli e modificare i propri articoli. Nient'altro! I membri del gruppo Super Utenti hanno la responsabilità di tutti gli aspetti della gestione e del funzionamento del sito. Joomla fornisce nove gruppi di utenti predefiniti e puoi crearne altri se ne hai bisogno.

![Elenco gruppi utenti](../../../en/images/users/access-control-users-groups-list.png)

I gruppi di utenti predefiniti sono organizzati con relazioni di tipo genitore-figlio per minimizzare la duplicazione dei permessi. Esempi di eredità:

- Un membro del gruppo Registrato non ha il permesso di accesso come Amministratore. Neanche Editor o Editore.
- Un membro del gruppo Autore ha il permesso di Creare e Modificare Propri. Anche Editor e Editore, ma hanno permessi aggiuntivi.

Puoi creare nuovi gruppi di utenti per scopi speciali secondo necessità. Ad esempio, potresti voler creare un gruppo che abbia il permesso di accesso come Amministratore ma con l'accesso limitato a un singolo componente. C'è un esempio di tale gruppo di utenti personalizzato verso la fine di questo tutorial.

## Livelli di Accesso

Ogni volta che crei un oggetto, come un articolo, un modulo o un elemento di menu, vedrai un campo Accesso, solitamente nella colonna di destra del modulo di inserimento dati. È un elenco a discesa che offre una scelta tra Pubblico, Ospite, Registrato, Speciale e Super Utenti. L'impostazione predefinita è Pubblico. I livelli di accesso alla visualizzazione predefiniti sono mostrati nella seguente schermata:

![Livelli di accesso degli utenti](../../../en/images/users/access-control-users-access-levels.png)

Esempi:

- Se crei un modulo del sito e imposti l'Accesso su Registrato, sarà visibile solo agli utenti che hanno effettuato l'accesso al sito.
- Se crei un elemento di menu del sito e imposti l'Accesso su Super Utenti, sarà visibile solo ai Super Utenti che hanno effettuato l'accesso al sito.

## Autorizzazioni

Le autorizzazioni di configurazione globale sono il punto di partenza da cui le impostazioni di autorizzazione nei componenti o nei singoli elementi possono ereditare o sovrascrivere. Screenshot:

![autorizzazioni di configurazione globale](../../../en/images/users/access-control-global-configuration-permissions.png)

Lo screenshot mostra che i membri del gruppo Pubblico non hanno il permesso di eseguire alcuna azione. Se selezioni ogni gruppo a turno, vedrai come le autorizzazioni cambiano da gruppo a gruppo. Nota che Manager e Administrator sono autorizzati all'accesso come Amministratore, ma Author, Editor e Publisher no. Questi ultimi sono effettivamente ruoli del Sito piuttosto che ruoli di Amministratore.

Tutte le autorizzazioni di gruppo ereditano dal gruppo Pubblico. Non ha il permesso per alcuna azione. Tuttavia, per impostazione predefinita, gli elementi nel gruppo Pubblico possono essere visualizzati, quindi assegnare l'autorizzazione Pubblico a un elemento permetterà che sia visibile a tutti i visitatori del sito, sia che abbiano effettuato l'accesso o meno.

### Autorizzazioni degli Articoli

Le azioni delle autorizzazioni degli Articoli differiscono dalle azioni delle Autorizzazioni di Configurazione Globale. Non sono presenti voci relative al login e sono presenti voci relative ai flussi di lavoro. Questo è un modello piuttosto tipico: un componente avrà autorizzazioni rilevanti per il componente; un elemento del componente (come un articolo) avrà autorizzazioni rilevanti per quell'unico elemento.

![Autorizzazioni dei contenuti](../../../en/images/users/access-control-global-content-permissions.png)

### Autorizzazioni di un Singolo Articolo

Le autorizzazioni di un singolo articolo hanno solo tre voci: Elimina, Modifica e Modifica Stato:

![autorizzazioni di un singolo articolo](../../../en/images/users/access-control-article-permissions.png)

## Esempio di Controllo Accessi: Utente a Scopo Speciale

Supponiamo di dover creare un Gruppo Utenti per utenti che hanno una sola responsabilità, in questo esempio un Amministratore di Articoli. Gli utenti in questo gruppo dovrebbero avere il permesso di Login Amministratore ma non dovrebbero vedere altro che gli elementi di Contenuto. Procedura:

### Crea un nuovo Gruppo Utenti

- Seleziona **Utenti → Gruppi** dal menu dell'Amministratore.
- Seleziona il pulsante `Nuovo` dalla Toolbar.
- Compila il campo Titolo del Gruppo: Amministratore di Articoli
- Il Genitore del Gruppo deve essere Pubblico - non ha permessi per niente.

![Nuovo modulo gruppo utenti](../../../en/images/users/access-control-new-group.png)

### Assegna a Speciale

- Seleziona **Utenti → Livelli d'accesso** dal menu dell'Amministratore.
- Seleziona l'elemento **Speciale**.
- Seleziona la casella di controllo Amministratore di Articoli nel modulo **Utenti: Modifica Livello di Visualizzazione Accesso**.
- Salva & Chiudi.

![Seleziona accesso per gruppo](../../../en/images/users/access-control-select-access-for-group.png)

### Permessi di Configurazione Globale

- Seleziona **Home Dashboard → Configurazione Globale** dal menu
  dell'Amministratore.
- Seleziona la scheda **Permessi**.
- Seleziona il gruppo **Amministratore di Articoli**.
- Imposta **Login Amministratore** su Consentito.
- Salva & Chiudi

![Seleziona accesso per gruppo](../../../en/images/users/access-control-article-administrator-global-permissions.png)

### Permessi Opzioni Articoli

- Seleziona **Contenuti → Articoli** dal menu dell'Amministratore.
- Seleziona il pulsante `Opzioni` dalla Toolbar.
- Seleziona la scheda **Permessi**.
- Seleziona il gruppo **Amministratore di Articoli**.
- Imposta su Consentito tutti gli elementi eccetto i primi due (Configura ACL & Opzioni e
  Configura solo Opzioni).
- Salva & Chiudi

![Seleziona accesso per gruppo](../../../en/images/users/access-control-article-administrator-content-permissions.png)

### Crea o Modifica Utente

- Crea un nuovo utente o modifica un utente esistente che non è assegnato a nessun gruppo
- Seleziona **Amministratore di Articoli** nella scheda **Gruppi Utente Assegnati** 
  del modulo di modifica Utente.
- Salva & Chiudi.
- Effettua l'accesso come un utente nel solo Gruppo Amministratore di Articoli. Il menu
  dovrebbe mostrare solo elementi relativi agli articoli:

![Seleziona accesso per gruppo](../../../en/images/users/access-control-article-administrator-home-dashboard.png)

*Tradotto da openai.com*

