<!-- Filename: J4.x:Workflow / Display title: Flusso di Pubblicazione  -->

## Introduzione

In Joomla, un flusso di lavoro è una sequenza di passaggi nella vita di un articolo, dalla concezione alla cessazione. I passaggi vengono generalmente svolti da persone diverse con responsabilità diverse. Ad esempio, nel mondo dei giornali, un redattore subisce prende un racconto da un giornalista e verifica l'accuratezza, la grammatica, la leggibilità e la lunghezza, e forse di più. Il redattore passerà poi il racconto al direttore editoriale che potrà accettare o rifiutare il racconto, decidere dove collocarlo nel giornale, e così via.

Il componente Flusso di lavoro viene utilizzato per aggiungere **fasi** agli articoli per migliorare gli stati statici (non pubblicato, pubblicato, cestinato e archiviato) con **transizioni**. Gli stati statici e le transizioni vengono registrati separatamente in modo che i Flussi di lavoro possano essere abilitati o disabilitati secondo le necessità senza influire sullo stato degli elementi di contenuto. I Flussi di lavoro vengono abilitati o disabilitati nella pagina *Articoli: Opzioni* scheda *Integrazione*.

Esiste una pagina tutorial contenente passaggi per la creazione di un esempio di flusso di lavoro: [Scenari di flusso di lavoro](jdocmanual?article=user/workflows/workflow-scenarios). 

## Termini e Definizioni

- *Flusso di lavoro:* Un flusso di lavoro è una sequenza completa di passaggi. Possono essere creati diversi flussi di lavoro per scopi differenti. Il componente Flusso di lavoro contiene un *Flusso di lavoro di base* e i dati di esempio del Blog hanno un *Flusso di lavoro del Blog* più complesso.
- *Fase:* Una fase è una posizione all'interno di un flusso di lavoro. Ad esempio, un articolo non pubblicato può essere alla Fase 1: In preparazione o alla Fase 2: Pronto per la revisione, e così via. È la fase dell'elemento che viene registrata nel database.
- *Transizione:* Una transizione è un passaggio da una fase a un'altra, spesso alla successiva nel flusso di lavoro, ma potrebbe essere alla fase precedente o alla fase iniziale.
- *Stato:* Lo stato di un articolo può essere non pubblicato, pubblicato, eliminato o archiviato. Uno stato può essere cambiato eseguendo una transizione del flusso di lavoro, a condizione che l'utente abbia il permesso di cambiare stato.
- *Categoria:* Quando i flussi di lavoro sono in uso, un Flusso di lavoro specifico può essere selezionato per una categoria nella scheda *Flusso di lavoro* del modulo *Articolo: Modifica categoria*.

## L'elenco dei flussi di lavoro

Quando i flussi di lavoro sono abilitati, l'elenco dei flussi di lavoro disponibili può essere visualizzato selezionando **Contenuto → Flussi di lavoro** dal menu dell'amministratore.

![Elenco dei flussi di lavoro](../../../en/images/workflows/workflows-list.png)

- Lo **Stato** di un flusso di lavoro può essere Abilitato, Disabilitato o Cestinato.
- Il **Nome** è un collegamento al modulo di modifica del flusso di lavoro.
- L'elemento **Predefinito** è utilizzato per nuovi elementi che non sono assegnati a una
  categoria che ha un flusso di lavoro definito.
- L'elemento **Fasi** è un pulsante che mostra il numero di fasi e un collegamento
  all'elenco delle fasi per il flusso di lavoro.
- L'elemento **Transizioni** è un pulsante che mostra il numero di transizioni e 
  un collegamento all'elenco delle transizioni per il flusso di lavoro.
- L'**ID** è il valore numerico del flusso di lavoro usato internamente.

## Fasi

Le fasi sono accessibili tramite l'elenco *Flussi di lavoro*. Seleziona il pulsante giallo che mostra il numero di fasi.

![Elenco fasi del flusso di lavoro](../../../en/images/workflows/workflow-stages-list.png)

Seleziona il nome di una fase per modificarla.

![Modulo di modifica della fase del flusso di lavoro](../../../en/images/workflows/workflow-stage-edit.png)

## Transizioni

Nei flussi di lavoro, gli articoli passano da una fase all'altra. Le transizioni sono gestite attraverso la lista delle *Transizioni*.

![La lista delle transizioni](../../../en/images/workflows/workflow-transitions-list.png)

- La *Fase Attuale* definisce dove inizia questa transizione.
- La *Fase di Destinazione* definisce dove termina questa transizione.

### Fasi di Transizione

Le fasi *Attuale* e di *Destinazione* sono impostate nel modulo di *Modifica Transizione*:

![Modulo di modifica transizione](../../../en/images/workflows/workflow-transition-edit.png)

La scheda *Azioni di Transizione* viene utilizzata per definire lo *Stato* in cui si troverà l'elemento dopo il completamento della transizione.

![Scheda azioni modulo di modifica transizione](../../../en/images/workflows/workflow-transition-edit-actions-tab.png)

- **Stato in Evidenza** Se l'elemento sarà o meno *Evidenziato*.
- **Stato di Pubblicazione** Seleziona dallo elenco lo stato di destinazione.

La scheda *Notifiche di Transizione* viene utilizzata per definire se viene inviata una notifica per quello stato. Ad esempio, se un articolo è stato scritto ma necessita di revisione, potrebbe essere inviato un'email per notificare l'editor.

![Scheda notifiche modulo di modifica transizione](../../../en/images/workflows/workflow-transition-edit-notifications-tab.png)

- **Invia Notifica** Se impostato su *Sì* appariranno campi extra.
- **Testo Messaggio Aggiuntivo** Aggiungi testo messaggio aggiuntivo o utilizza una stringa lingua per rendere il testo del messaggio traducibile.
- **Gruppi di Utenti** Seleziona chi riceverà la notifica, ad esempio tutti gli utenti nel gruppo *Editor*.
- **Utenti** Seleziona utenti singoli per ricevere questa notifica.

### Permessi

La scheda dei permessi controlla l'accesso a questa transizione da parte dei gruppi di utenti selezionati. Normalmente i permessi sono ereditati dalle impostazioni di Permessi in *Articoli: Opzioni*.

### Plugin di Transizione del Flusso di Lavoro

I plugin del flusso di lavoro sono usati per azioni invocate dalle transizioni. Vai a **Sistema → Plugin** e cambia il filtro *- Seleziona Tipo -* in *flusso di lavoro*. Ognuno di questi plugin può essere disattivato se non richiesto.

![Lista dei plugin del flusso di lavoro](../../../en/images/workflows/workflow-plugins.png)

- **Evidenziazione del Flusso di Lavoro** Questa azione implementa il cambiamento dello stato *Evidenziato* di un articolo da *Sì* a *No*.
- **Notifica del Flusso di Lavoro** Questa azione implementa la notifica a un utente che un cambio di fase richiede attenzione.
- **Pubblicazione del Flusso di Lavoro** Questa azione implementa un cambiamento di stato di un articolo da uno a un altro tra *Pubblicato*, *Non Pubblicato*, *Cestinato* o *Archiviato*. Se l'utente non ha il permesso di cambiare stato, il processo fallirà con un messaggio esplicativo. La transizione che ha richiesto il cambiamento di stato avrà comunque successo!

## Categorie

Gli articoli possono essere assegnati a categorie. Esse corrispondono a un certo flusso di lavoro e possono essere personalizzate in vari modi. È possibile impostare uno stato, una categoria principale e anche limitare l'accesso così come i permessi. Questa opzione non si trova nella schermata dei flussi di lavoro. Per accedere a questa opzione è necessario andare su **Contenuto → Categorie**. Una volta lì, apri qualsiasi categoria e vedrai una scheda *Flussi di lavoro*.

![Flusso di lavoro modifica categorie articoli](../../../en/images/workflows/workflow-categories-blog.png)

### Esempio

Certi articoli devono essere disponibili solo per gli amministratori o per utenti di un rango superiore.

- Crea una categoria chiamata *Riservato*
- Imposta tutti i permessi su *Permesso* per amministratori o ranghi superiori.
- Sposta gli articoli interessati nella categoria *Riservato*.

Questo consente di evitare di impostare i permessi sui singoli articoli.

## Versionamento

Quando il flusso di lavoro è abilitato, i campi gestiti dal flusso di lavoro vengono esclusi dal versionamento (come "stato" e "in evidenza") per evitare conflitti di permessi.

## Esempi

Alcuni esempi specifici sono disponibili per illustrare come utilizzare i Workflow per diversi gruppi di utenti:

- [Esempio 1](jdocmanual?article=user/workflows/workflow-example-1) utilizza i gruppi di utenti predefiniti Autore, Redattore e Editore per preparare gli articoli di una newsletter.
- [Esempio 2](jdocmanual?article=user/workflows/workflow-example-2) utilizza gruppi di utenti personalizzati per preparare articoli per le riunioni di comitato.

*Tradotto da openai.com*

