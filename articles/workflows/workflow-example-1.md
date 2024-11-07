<!-- Filename: J6.x:Workflow_Scenarios_Example_1 / Display title: Esempio di Workflow 1  -->

## Introduzione

Un flusso di lavoro consiste in *fasi* e *transizioni* tra queste fasi. Per qualsiasi articolo, è la fase attuale che viene registrata nel database e usata per identificare il flusso di lavoro e le transizioni utilizzate da quel flusso di lavoro.

Un singolo sito può avere molti flussi di lavoro. Qui, un *Flusso di Lavoro per una Newsletter* viene utilizzato come esempio per spiegare come tre individui con ruoli diversi possano essere coinvolti nella produzione di un articolo per la newsletter. L'esempio utilizza i gruppi utenti predefiniti di Joomla: Autore, Editore e Pubblicatore. Ciò presenta un problema: un Autore può vedere solo articoli Pubblicati, quindi non può modificare nuovamente gli articoli Non Pubblicati. Un metodo per evitare questo problema è trattato in [Esempio 2](jdocmanual?article=user/workflows/workflow-example-2).

![Elenco flussi di lavoro](../../../en/images/workflows/example-1-workflows-list.png)

Da notare che il *Flusso di Lavoro Base* è impostato come *Predefinito*. Questo può avere conseguenze problematiche che verranno trattate più avanti in questo articolo!

## Gli Utenti

- *Arthur* è un utente assegnato al **Gruppo Autori** di Joomla. Può creare nuovi
  articoli e modificare i propri articoli, ma non può modificare gli articoli scritti da
  altri utenti o cambiare lo stato degli articoli. Quindi non può pubblicare i propri
  articoli. Il suo compito è redigere nuovi articoli.
- *Eddie* è un utente assegnato al **Gruppo Editor** di Joomla. Può modificare
  articoli creati da qualsiasi altro utente, incluso Arthur e se stesso. Anche lui
  non può cambiare lo stato di un articolo. Il suo compito è recensire gli articoli
  inviati da Eddie, controllare l'accuratezza, l'ortografia e la grammatica, la qualità
  delle immagini e così via.
- *Pru* è un utente assegnato al **Gruppo Publisher** di Joomla. Può fare
  tutto ciò che possono fare Eddie e Arthur. Inoltre, può cambiare lo stato
  di un articolo. È suo compito decidere se un articolo è accettabile
  per la pubblicazione e pubblicarlo.

## Le Fasi

Ci sono quattro fasi in questo Flusso di Lavoro:

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-workflow-stages.png)

- **Bozza** è la fase creata da Arthur per un nuovo articolo.
- **Revisione** è la fase in cui Eddie si occupa di correggere il contenuto.
- **Approvazione** è la fase in cui Pru decide se l'articolo è abbastanza buono per essere pubblicato.
- **Pubblicazione** è la fase in cui l'articolo è stato approvato e pubblicato.

I moduli di inserimento dati per le fasi necessitano di poche spiegazioni, solo un Nome e una Descrizione.

## Le Transizioni

Sono necessarie due transizioni tra ogni fase: una per tornare alla fase precedente se è necessario più lavoro nella fase precedente; e una seconda per migrare alla fase successiva. Sono necessarie transizioni extra per gestire la cessazione di un articolo:

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-workflow-transitions.png)

- **Bozza/Revisione** per passare dalla fase Bozza alla Revisione.
- **Revisione/Bozza** per riportare la fase dalla Revisione alla Bozza.
- **Revisione/Approvazione** per spostare la fase da Approvazione a Revisione.
- **Approvazione/Revisione** per riportare la fase da Approvazione a Revisione.
- **Revisione/Pubblicazione** per spostare la fase a Pubblicato e cambiare lo stato dell'articolo a *Pubblicato*.
- **Pubblica** Per impostare lo stato dell'articolo su *Pubblicato* quando la transizione viene eseguita da un Autore o Editore.
- **Annulla Pubblicazione** per cambiare lo stato dell'articolo a *Non Pubblicato*.
- **Archivia** per cambiare lo stato dell'articolo a *Archiviato*.
- **Cestina** per cambiare lo stato dell'articolo a *In Cestino*.

Le ultime tre transizioni permettono a Pru di cambiare lo stato di un articolo quando non è più necessario.

### Modifica Transizione

Il modulo di inserimento data ha quattro schede iniziando con la scheda *Transizione*:

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-edit-transition.png)

- **Nome** È meglio usare le fasi Corrente e Destinazione nel nome.
- **Fase Corrente** La fase prima che avvenga la transizione.
- **Fase Destinazione** La fase dopo che la transizione ha avuto luogo.
- **Nota** Qualsiasi nota esplicativa per aiutare a spiegare la transizione.

#### La scheda *Azioni di Transizione*:

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-edit-transition-actions.png)

- **Stato Evidenziato** Definisce lo stato evidenziato che un elemento dovrebbe avere dopo l'esecuzione di questa transizione. Lasciare su *-Non Selezionato-* se è probabile che l'utente che esegue questa transizione non abbia il permesso di mettere in evidenza articoli.
- **Stato di Pubblicazione** Definisce lo stato pubblicato che un elemento dovrebbe avere dopo l'esecuzione di questa transizione. Lasciare su *-Non Selezionato-* se è probabile che l'utente che esegue questa transizione non abbia il permesso di cambiare lo stato dell'articolo.

#### La scheda *Notifiche*:

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-edit-transition-notification.png)

- **Invia Notifica** Impostare su *Sì* dove le notifiche sono necessarie, ad esempio quando Arthur deve informare Eddie che un articolo è pronto per la revisione.
- **Testo Messaggio Aggiuntivo** Questo è testo aggiuntivo generico per aiutare il destinatario.
- **Gruppi di Utenti** È possibile scegliere di inviare la notifica a uno o più gruppi di utenti o a nessuno e inviare la notifica a singoli individui invece.
- **Utenti** Selezionare utenti individuali dall'elenco degli utenti.

#### La scheda *Permessi*:

Nota che *Autore* ha *Esegui Transizione* impostato su Consentito (Ereditato). Non modificare queste impostazioni per altre transizioni che un Autore non dovrebbe utilizzare poiché questo influenzerà anche Editori e Pubblicatori.

## La Categoria dell'Articolo

Ogni articolo viene assegnato a un flusso di lavoro al primo salvataggio. Se l'articolo viene inizialmente assegnato a una Categoria che ha un Flusso di Lavoro selezionato, viene assegnato a quel flusso di lavoro. Altrimenti, viene assegnato al flusso di lavoro predefinito. Questo può essere problematico perché il componente Flusso di Lavoro non offre un metodo per cambiare il flusso di lavoro una volta assegnato. Può essere cambiato da un Super Utente utilizzando l'Azione Collettiva nella pagina di elenco degli Articoli.

### Creare una Categoria Newsletter

È necessaria una nuova categoria Newsletter per visualizzare la Newsletter come un Blog di Categoria e per garantire che gli articoli della Newsletter siano assegnati al Flusso di Lavoro della Newsletter.

![Elenco dei flussi di lavoro](../../../en/images/workflows/example-1-newsletter-category.png)

## L'opzione di menu Newsletter

Affinché i visitatori del sito possano vedere la Newsletter, essa deve essere la pagina principale o collegata con un elemento del menu. Per seguire questo esempio, crea un nuovo elemento del menu di tipo *Blog di categoria* utilizzando la categoria *Newsletter*.

Prova l'elemento del menu del sito. È probabile che sia una pagina vuota con questo messaggio:

<div class="alert alert-info">
Non ci sono articoli in questa categoria. Se le sottocategorie sono visualizzate su questa pagina, potrebbero contenere articoli.
</div>

## Accedi come Arthur

Ricordi Arthur l'Autore? Dopo l'accesso, la pagina della Newsletter dovrebbe avere un pulsante etichettato **Nuovo Articolo**. Selezionalo per scrivere un nuovo articolo.

### Comporre un Articolo

Compila il modulo di modifica dell'articolo come faresti per qualsiasi articolo. Tuttavia, prima del primo salvataggio, guarda la scheda *Pubblicazione*.

- **Fase del Flusso di Lavoro** dovrebbe essere impostata su **Esegui Transizione** *Bozza/Revisione*.
- **Categoria** dovrebbe essere impostata su *Newsletter*.

Quando hai finito di modificare l'articolo, seleziona *Salva* o *Salva e Chiudi*.

<div class="alert alert-danger">Dopo aver chiuso l'articolo, Arthur non può modificarlo di nuovo perché gli utenti del gruppo Autori non possono visualizzare gli articoli Non Pubblicati.</div>

## Accedi come Eddie

Eddie l'Editor ha il permesso di visualizzare gli articoli Non Pubblicati, quindi la pagina del Notiziario mostra qualsiasi elemento Non Pubblicato per lui da modificare.

### Revisiona l'Articolo

Seleziona l'articolo redatto da Eddie e apporta le modifiche necessarie per migliorarlo. Quando sei soddisfatto, nel *Tab di Pubblicazione*:

- **Fase del Flusso di Lavoro** deve essere impostata su **Esegui Transizione** *Revisiona/Approva*.

A differenza di Arthur, che non può vedere il suo articolo dopo averlo salvato, Eddie può vedere e modificare nuovamente l'articolo. Può anche impostare la transizione per la fase successiva su Approva/Pubblica. La transizione funzionerà ma l'articolo non verrà pubblicato poiché Eddie non ha il permesso di Pubblicare.

## Accedi come Pru

Quando la fase di Approva è stata impostata nel flusso di lavoro, Pru dovrebbe aver ricevuto un messaggio che sollecita un'azione. Accedi quindi come Pru per rivedere l'articolo e impostare la sua fase del flusso di lavoro su **Esegui Transizione** *Pubblica*. *Salva e Chiudi* l'articolo per vedere il risultato pubblicato. Disconnettiti per vedere il risultato senza il link Modifica.

Ripensamento: è necessaria un'altra fase per permettere a Pru di riportare la fase da Pubblica a Revisione se vuole che Eddie corregga qualcosa.

## Flusso di Lavoro del Backend

I gruppi di utenti Author, Editor e Publisher sono destinati all'uso frontend. Il problema per Arthur è che non può accedere ai suoi articoli in bozza dal frontend perché il suo gruppo di utenti non ha accesso alla visualizzazione degli articoli non pubblicati.

Puoi consentire l'accesso al backend per tutti i membri di questi gruppi come segue:

- Vai alla pagina **Configurazione Globale**.
- Seleziona la scheda **Permessi**.
- Seleziona *Author* e imposta **Accesso Amministratore** su *Consentito*.
- **Salva**
- Vai alla pagina **Articoli: Opzioni**.
- Seleziona la sua scheda **Permessi**.
- Seleziona *Author* e imposta **Accesso all'Interfaccia di Amministrazione** su *Consentito*.

Questo permetterà ad Arthur, Eddie e Pru di accedere al backend con accesso agli elementi di Contenuto. Una Dashboard Home molto ridotta:

![Home dashboard per arthur](../../../en/images/workflows/example-1-backend-home.png)

Ma Arthur ha accesso ai suoi articoli in bozza:

![Lista articoli per Arthur](../../../en/images/workflows/example-1-backend-articles.png)

Nota che Arthur non può modificare l'ultimo elemento nella lista perché non è uno dei suoi articoli. Il titolo dell'articolo non è collegato. Allo stesso modo, Arthur non può modificare nessuna delle categorie esistenti perché non ha il permesso e anch'esse non sono collegate. Può creare una nuova Categoria ma è Non Pubblicata e non può pubblicarla!

## Correzione per Workflow Errato

Se assegni un articolo al workflow sbagliato, ci sono due metodi disponibili per risolvere il problema.

### Metodo Super Utente

- Vai all'elenco **Articoli**.
- Seleziona la casella di controllo per l'articolo problematico.
- Seleziona il pulsante **Azioni** nella Barra degli Strumenti.
- Seleziona il pulsante **Batch** dall'elenco.
- Seleziona **Cambia Fase** dal dialogo *Processo Batch Articoli Selezionati*.
- Seleziona un Workflow e una Fase adeguati come destinazione.
- Seleziona il pulsante **Processa**.

![Elenco degli articoli per Arthur](../../../en/images/workflows/example-1-backend-batch.png)

### Metodo Alternativo

In alternativa, puoi modificare una tabella del database con phpMyAdmin o simili.

Informazioni richieste:

- L'ID dell'articolo dall'ultima colonna nell'elenco degli Articoli.
- L'ID di una fase nel workflow richiesto dall'ultima colonna dell'elenco Fasi del Workflow che desideri utilizzare.

In phpMyAdmin:

- Sfoglia la tabella #__workflow_associations per trovare l'item_id che contiene l'ID del tuo articolo.
- Cambia il valore di stage_id all'ID della fase che hai individuato nel workflow richiesto.

Torna al tuo elenco articoli e verifica che l'elemento problematico stia ora utilizzando il workflow corretto.

*Tradotto da openai.com*

