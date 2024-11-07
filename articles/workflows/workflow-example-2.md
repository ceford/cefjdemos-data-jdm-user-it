<!-- Filename: J6.x:Workflow_Scenarios_Example_2 / Display title: Esempio di Flusso di Lavoro 2   -->

## Introduzione

Questo esempio coinvolge due utenti, Alice e Bob, che sono rispettivamente il presidente e il segretario di un comitato. Il flusso di lavoro prevede la preparazione e l'approvazione degli ordini del giorno e dei verbali delle riunioni del comitato. Charlie è un membro del comitato che avrà accesso ai documenti del comitato quando verranno pubblicati. Il flusso di lavoro utilizza solo il frontend.  

## Gruppi di Utenti

Per prima cosa, crea nuovi Gruppi di Utenti, tutti figli di *Registrato*.

- **Comitato** Un figlio di *Registrato* 
- **Presidente** Un figlio di *Comitato*
- **Segretario** Un figlio di *Comitato*

![Gruppi di utenti personalizzati](../../../en/images/workflows/example-2-user-groups.png)

## Livello di Accesso Utente

- Crea un nuovo livello, **Comitato** e aggiungi *Comitato* ai Gruppi Utente con Accesso di Visualizzazione.
- Nel livello di accesso *Speciale*, aggiungi *Comitato* ai Gruppi Utente con Accesso di Visualizzazione.

![Livelli di Accesso di Visualizzazione](../../../en/images/workflows/example-2-viewing-access-levels.png)

## Creare Utenti

- **Alice** nel gruppo *Chair*.
- **Bob** nel gruppo *Secretary*.
- **Charlie** nel gruppo *Committee*.

## Creare il Flusso di Lavoro

- **Nome** *Flusso di Lavoro del Comitato*
- **Descrizione** *Flusso di lavoro per la preparazione dei documenti del Comitato.*
- **Autorizzazioni**
  - **Comitato** Tutte impostate su *Ereditato* Non consentito (ereditato).
  - **Presidente** Tutte impostate su *Consentito* tranne *Elimina*. Forse...
  - **Segretario** Tutte impostate su *Consentito* tranne *Elimina* e *Modifica Stato*.

![Lista flussi di lavoro](../../../en/images/workflows/example-2-workflows-list.png)

### Creare le Fasi del Flusso di Lavoro

- **Bozza** 
  - **Nota** *Documenti in preparazione.* 
  - **Autorizzazioni** Tutte lasciate su *Ereditato*.
- **Revisione**
  - **Nota** *Documenti in attesa di approvazione.* 
  - **Autorizzazioni** Tutte lasciate su *Ereditato*.
- **Pubblicazione**
  - **Nota** *Documenti pubblicati.* 
  - **Autorizzazioni** Tutte lasciate su *Ereditato*.

![Fasi del flusso di lavoro](../../../en/images/workflows/example-2-stages-committee-workflow.png)

### Creare le Transizioni del Flusso di Lavoro

#### Bozza a Revisione

Questa è la normale transizione in avanti nella sequenza delle fasi.

- **Nome** *Bozza/Revisione*
- **Scheda Transizione**
  - **Fase Attuale** *Bozza*
  - **Fase Obiettivo** *Revisione*
  - **Nota** *Transizione alla fase successiva.*
- **Scheda Azioni di Transizione**
  - **Stato in Evidenza** *- Nessuno Selezionato -*
  - **Stato di Pubblicazione** *- Nessuno Selezionato -*
- **Scheda Notifiche**
  - **Invia Notifica** *Sì* I destinatari devono avere attivato *Ricevere Email di Sistema* per ricevere le notifiche via email. 
  - **Testo del Messaggio Aggiuntivo** Qualcosa di specifico per questo flusso di lavoro?
  - **Gruppi di Utenti** *Presidente*
  - **Utenti** Un'alternativa all'uso dei Gruppi di Utenti.
- **Scheda Autorizzazioni** Tutte impostate su **Ereditato**.

#### Revisione a Bozza

Questa è la retromarcia a una fase precedente della sequenza quando il Presidente richiede più lavoro da parte del Segretario. I campi del modulo sono simili a quelli della Bozza/Revisione eccetto per la Nota e per il *Fase Attuale* e *Fase Obiettivo* che sono invertiti.

#### Revisione a Pubblicazione

Questa è la transizione che cambia lo stato di un elemento da *Non Pubblicato* a *Pubblicato*. Solo il Presidente ha il permesso di effettuare tale modifica.

- **Nome** *Revisione/Pubblicazione*
- **Scheda Transizione**
  - **Fase Attuale** *Revisione*
  - **Fase Obiettivo** *Pubblicazione*
  - **Nota** *L'ultima transizione per la pubblicazione.*
- **Scheda Azioni di Transizione**
  - **Stato in Evidenza** *- Nessuno Selezionato -*
  - **Stato di Pubblicazione** *Pubblicato*
- **Scheda Notifiche**
  - **Invia Notifica** *Sì* I destinatari devono avere attivato *Ricevere Email di Sistema* per ricevere le notifiche via email. 
  - **Testo del Messaggio Aggiuntivo** *Un documento del comitato è stato pubblicato ed è ora disponibile per la visualizzazione.*
  - **Gruppi di Utenti** *Comitato*
  - **Utenti** Un'alternativa all'uso dei Gruppi di Utenti.
- **Scheda Autorizzazioni**
  - **Segretario** Impostare *Esegui Transizione* su *Negato*.

#### Pubblicazione a Revisione

Questo è un cambiamento da Pubblicazione a Revisione. È davvero necessario? Un articolo pubblicato può ancora essere modificato dal Segretario o dal Presidente. Forse un documento del Comitato con dati sensibili è stato pubblicato per errore.

Se necessario, creare una Transizione simile alla transizione *Revisione a Pubblicazione* ma con le Fasi invertite, le *Azioni di Transizione / Stato di Pubblicazione* impostate su *Non Pubblicato* e un messaggio generico di *Testo del Messaggio Aggiuntivo*.

#### Archivia

Questa è la transizione effettuata quando un documento del Comitato non è più necessario. Nel flusso di lavoro rimane nella fase di Pubblicazione ma lo Stato dell'articolo viene cambiato da Pubblicato a Archiviato.

- **Nome** *Archivia*
- **Scheda Transizione**
  - **Fase Attuale** *Pubblicazione*
  - **Fase Obiettivo** *Pubblicazione*
  - **Nota** *Modifica lo stato dell'elemento da Pubblicato a Archiviato.*
- **Scheda Azioni di Transizione**
  - **Stato in Evidenza** *- Nessuno Selezionato -*
  - **Stato di Pubblicazione** *Archiviato*
- **Scheda Notifiche**
  - **Invia Notifica** *No* Questa non è una transizione che richiede azione. 
- **Scheda Autorizzazioni**
  - **Segretario** Impostare *Esegui Transizione* su *Negato*.

![Transizioni del flusso di lavoro](../../../en/images/workflows/example-2-transitions-committee-workflow.png)

## Creare una Nuova Categoria

<div class="alert alert-warning">Questo passaggio è davvero importante! I nuovi documenti del Comitato devono essere creati con questa categoria o acquisiranno il flusso di lavoro predefinito che necessita di un Super Utente per essere modificato.</div>

- **Titolo** *Comitato* 
- **Flusso di lavoro** Seleziona *Flusso di lavoro del Comitato* dalla lista di Flussi di lavoro.
- **Permessi**
  - Autore, Editore e Pubblicatore: Tutti impostati su *Non Consentito* o lasciati su *Non Consentito (Ereditato)*.
  - Comitato: Tutti lasciati su *Ereditato*.
  - Presidente: Tutti eccetto *Eliminare* impostati su *Consentito*.
  - Segretario: Tutti eccetto *Eliminare* e *Modificare Stato* impostati su *Consentito*.

## Creare un Elemento di Menu

- **Titolo** *Documenti del Comitato*
- **Tipo di Elemento di Menu** Elenco di Categorie
- **Scegli una Categoria** *Comitato*
- **Accesso** *Comitato*

![Elemento di menu documenti del comitato](../../../en/images/workflows/example-2-menu-item.png)

## Controlla il Sito

Accedi a turno come Alice, Bob, Charlie e un Super Utente per vedere cosa possono vedere:

Alice, Bob e Charlie possono vedere la voce di Menu ma nessun altro può vederla, neanche un Super Utente. Dopo aver selezionato la voce di menu, Alice e Bob possono vedere una tabella dei documenti del Comitato, inclusi quelli non pubblicati. Charlie può solo vedere una tabella dei documenti del Comitato pubblicati o un messaggio esplicativo se non ne sono stati pubblicati.

Alice e Bob possono anche vedere un link Modifica per ogni articolo e un pulsante **Nuovo Articolo**. Questo viene solitamente utilizzato da Bob per creare un documento del Comitato ma anche Alice può farlo.

![Vista di Bob della pagina di elenco delle categorie dei documenti del comitato](../../../en/images/workflows/example-2-committee-papers.png)

### Per Creare e Pubblicare un Documento del Comitato

- Accedi come Segretario e seleziona il pulsante **Nuovo Articolo** nella pagina 
  *Documenti del Comitato*.
- Inserisci il testo e *Salva*. Questo può essere fatto in diverse sessioni di modifica, 
  forse in diversi giorni o settimane. L'articolo rimane Non Pubblicato e nella fase di 
  Bozza fino a quando...
- Seleziona la scheda *Pubblicazione* nel modulo di modifica e imposta lo *Stadio del 
  Flusso di Lavoro* su Esegui Transizione **Bozza/Revisione**. 
- Seleziona **Salva & Chiudi** per eseguire la transizione.
- Il lavoro del Segretario è completato per il momento e un messaggio è stato inviato 
  al Presidente del Comitato.
- Il Presidente accede, verifica il documento pronto per la Revisione e utilizza la 
  transizione **Revisione/Pubblicare** per rendere il documento *Pubblicato*. Il lavoro 
  del Presidente è completato per il momento e un messaggio viene inviato ai membri 
  del Comitato.
- I membri del Comitato possono accedere e visualizzare il documento pubblicato.

*Tradotto da openai.com*

