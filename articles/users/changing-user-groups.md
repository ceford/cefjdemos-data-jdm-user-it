<!-- Filename: Changing_user_groups / Display title: Modifica dei Gruppi dell'Utente   -->

## Ereditarietà dei Gruppi

Le liste dei gruppi utilizzano un modello di ereditarietà. Ad esempio, un utente appartenente al gruppo Autore eredita tutti i privilegi del gruppo Registrato e ottiene alcuni privilegi extra. Allo stesso modo, un utente appartenente al gruppo Editore eredita tutti i privilegi del gruppo Autore e ottiene ulteriori privilegi extra. I gruppi del backend ereditano il livello di privilegio più alto nel frontend.

Per questo motivo, è necessario selezionare un solo gruppo per un singolo utente - il gruppo con più privilegi.

## Passaggi

Puoi modificare il gruppo di un utente seguendo questi passaggi. Devi accedere come Amministratore o Super Utente per poter cambiare i gruppi di un utente. Inoltre, un Amministratore non può rendere sé stesso o altri un Super Utente.

1. Dal *Home Dashboard*, seleziona l'elemento **Utenti**. Oppure...
2. Dal menu *Utente*, seleziona **Utenti** e poi **Gestisci**.
3. Trova l'utente richiesto nell'elenco degli utenti. Puoi cercare per nome, nome utente, email o prefisso id.
4. Seleziona il nome dell'utente da modificare.
5. Seleziona la scheda *Gruppi Utente Assegnati*.
6. Seleziona il gruppo a cui l'utente deve appartenere.
7. Seleziona *Salva*.

## Elenco di Controllo Accessi (ACL) per Joomla

Di seguito è riportato l'elenco dell'Elenco di Controllo Accessi
(ACL) per Joomla. È indicato il gruppo di utenti, e i punti elenco sottostanti
descrivono i permessi associati a quel gruppo.

### Gruppi Frontend

#### Ospite

- Visualizzare il sito pubblico e gli articoli pubblici

#### Registrato

- Privilegi del Gruppo Ospite
- Visualizzare articoli riservati ai registrati
- Nessun accesso agli elementi riservati al Gruppo Ospite

#### Autore

- Privilegi del Gruppo Registrato
- Creare nuovi articoli
- Modificare articoli di cui sono proprietari
- Visualizzare contenuti speciali

#### Editore

- Privilegi del Gruppo Autore
- Modificare tutti gli articoli, inclusi quelli non pubblicati

#### Pubblicatore

- Privilegi del Gruppo Editore
- Pubblicare articoli

### Gruppi Backend

Questi gruppi permettono di accedere al Pannello di Amministrazione tramite l'URL
*/administrator*.

#### Manager

- Privilegi del Gruppo Pubblicatore
- Accesso al Backend dell'Amministratore

#### Amministratore

- Privilegi del Gruppo Manager
- Creare nuovi utenti
- Installare estensioni

#### Super Utente

- Privilegi di Amministratore
- Modificare il template del sito
- Modificare la configurazione globale

*Tradotto da openai.com*

