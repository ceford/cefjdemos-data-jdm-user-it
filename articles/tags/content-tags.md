<!-- Filename: J4.x:How_To_Use_Content_Tags_in_Joomla / Display title: Tag dei Contenuti   -->

## Introduzione

I tag forniscono un modo facile e efficiente per organizzare e visualizzare i contenuti. Il **Componente Tag** consente di utilizzare i tag su diversi tipi di contenuti, inclusi articoli, categorie, contatti e newsfeed. Permette anche la creazione di tag genitori e figli.

A differenza delle **Categorie** di Joomla, dove solo una categoria può essere assegnata a un elemento, è possibile assegnare più tag a un singolo elemento, ma non è obbligatorio assegnare tag agli elementi.

Una volta che un elemento è stato taggato con un tag specifico, cliccando sul pulsante del tag nel contenuto che mostra i tag si verrà indirizzati a una pagina che visualizza un elenco di tutti gli elementi che sono stati taggati con quel particolare tag. Per questo motivo, i tag sono spesso utilizzati come un modo per presentare elenchi *filtrati* di contenuti.

I tag possono essere aggiunti in diversi luoghi, offrendo flessibilità nella creazione dei tag.

## Considerazioni

Prima di iniziare, considera lo scopo dei tag sul sito web, specialmente se altri aggiungeranno contenuti. A meno che non siano aggiunti e gestiti correttamente, i tag possono diventare controproducenti. I problemi comuni includono gli scrittori di contenuti che aggiungono nuovi tag non necessari e nomi di tag scritti male. Alcuni amministratori del sito potrebbero decidere di modificare i permessi di accesso in modo che solo utenti specifici possano aggiungere nuovi tag.

Quando i tag vengono creati, verranno visualizzati come link negli elementi taggati. Gli stili e le posizioni dei tag sono definiti dal template del sito. Spesso sono stilizzati come pulsanti o etichette.

La visualizzazione dei tag potrebbe essere disattivata! Questo potrebbe sembrare illogico, ma è una funzione utile quando i tag vengono usati, ad esempio, per filtrare il contenuto per casi d'uso specifici.

## Elenco dei Tag

- Seleziona **Componenti → Tag** dal menu Amministratore.

![la pagina dell'elenco dei tag](../../../en/images/tags/tags-list.png)

Indipendentemente da come sono creati, i tag possono essere trovati in questo elenco.

## Aggiunta di Tag

### Tramite l'elenco Tag

Seleziona il pulsante **Nuovo** nella toolbar dell'elenco dei tag.

![nuovo tag chiamato predator](../../../en/images/tags/new-tag-predator.png)

- **Titolo** Questo è l'unico campo *obbligatorio*.
- **Alias** Questo viene creato dal Titolo al momento del salvataggio.
- **Descrizione** È sempre meglio aggiungere una Descrizione. Viene visualizzata nei moduli dell'amministratore e può essere utile quando si utilizzano molti tag.
- **Genitore** Lascia impostato su *Nessuno* se si tratta di un tag genitore principale. Oppure scegli un tag genitore dall'elenco se si tratta di un tag figlio.
- **Stato** Questo campo è impostato su *Pubblicato* di default. Può essere impostato su *Non Pubblicato*, *Archiviato* o *Nel Cestino*.
- **Accesso** Il livello di Accesso è Pubblico di default.
- **Nota** e **Nota di Versione:** Se necessario, puoi aggiungere note.
- **Salva & Chiudi** Il nuovo tag apparirà nell'elenco dei tag. Se stai creando più tag, puoi scegliere di cliccare **Salva & Nuovo** invece per crearne un altro.

Una volta salvato, il tag sarà disponibile per l'uso nei vari tipi di contenuto che lo utilizzano.

### Dall'interno di un Articolo

È possibile aggiungere nuovi tag mentre si crea o modifica un articolo. Nella scheda Contenuto dell'articolo, nel **Campo Tag**, inserisci il nome del nuovo tag e premi **Invio** per salvare e assegnare il tag all'articolo.

### Dall'interno di una Categoria

I tag possono essere aggiunti durante la creazione o la modifica di una categoria. Nella scheda **Categoria**, inserisci il nome del tag nel **Campo Tag** e premi **Invio** per creare e assegnare il nuovo tag.

### Dall'interno di un Contatto

I tag possono essere aggiunti durante la creazione o la modifica di un Contatto. Nella scheda **Nuovo/Modifica Contatto**, inserisci il nome del tag nel **Campo Tag** e premi **Invio** per creare e assegnare il nuovo tag. Puoi anche aggiungere nuovi tag durante la creazione di Categorie di Contatti.

### Dall'interno di un Feed di Notizie

I tag possono essere aggiunti durante la creazione o la modifica di un nuovo Feed di Notizie. Nella scheda **Nuovo/Modifica Feed di Notizie**, inserisci il nome del tag nel **Campo Tag** e premi **Invio** per creare e assegnare il nuovo tag. Puoi anche aggiungere nuovi tag durante la creazione di Categorie di Feed di Notizie.

## Gestione dei Tag

Ogni volta che aggiungi nuovi Tag all'interno di Joomla, essi appariranno tutti nella lista dei Tag. Usa la lista dei Tag per trovare, aprire e regolare le impostazioni dei tag.

### Il Filtro della Lista dei Tag

![filtro della lista dei tag per tipo](../../../en/images/tags/tags-list-filter.png)

Puoi manipolare la lista in diversi modi:

- Cerca un tag utilizzando parte o tutto il suo titolo nel campo di ricerca.
- Riordina la lista utilizzando il drag and drop per ottimizzare l'ordine di output.
- Pubblica o Sospendi la pubblicazione dei tag utilizzando il pulsante nella colonna di Stato.
- Seleziona uno o più tag e utilizza il pulsante **Azioni** per Pubblicare, Sospendere la pubblicazione, Archiviare, Verificare o Cestinare i tag selezionati.
- Seleziona uno o più tag e utilizza il pulsante **Azioni → Blocco** per impostare la Lingua o il Livello di Accesso.

### Impostazioni del Tag

- Seleziona un **Titolo** del tag per apportare modifiche alle sue impostazioni.

Nel modulo di modifica del tag:

- Le impostazioni della scheda **Dettagli del Tag** sono state trattate sopra.
- La scheda **Opzioni**:
  - Cambia il layout della pagina del tag (la pagina che appare quando
    clicchi sul link del tag - ad esempio, miosito.com/tags/il-mio-tag). Questo
    layout è normalmente l'impostazione predefinita e dipende dal tema.
  - Aggiungi una Classe CSS per applicare uno stile (aspetto) diverso al link
    per il tag. Questo sarebbe normalmente utilizzato solo dall'Amministratore
    del sito.
  - Imposta le immagini per il tag - un'immagine teaser per la lista dei tag e/o un'immagine completa per la pagina del tag.
- La scheda **Pubblicazione**: Imposta i Metadati per la pagina del tag per l'Ottimizzazione per i Motori di Ricerca (SEO).

## Come Joomla Visualizza i Tag

Una volta creati i tag sul tuo sito, saranno disponibili per l'uso non solo nei contenuti, ma anche in alcuni utili moduli come **Tag Popolari** e **Tag Simili**. I seguenti esempi mostrano come appaiono in un'installazione standard utilizzando il template predefinito **Cassiopeia**.

![esempio di utilizzo dei tag sito labrador giallo](../../../en/images/tags/tag-examples-yellow-labrador.png)

Quando clicchi su uno dei tag, sarai portato a una pagina che elenca tutti gli elementi assegnati a quel particolare tag:

![esempio di utilizzo dei tag sito labrador nero](../../../en/images/tags/tag-examples-black-labrador.png)

Cliccando su un tag verrai portato a una pagina che visualizza un elenco di tutti gli elementi assegnati a quel particolare tag - in pratica è una lista filtrata del contenuto del tuo sito web taggato. È fornita una casella di filtro per facilitare la ricerca degli elementi man mano che la lista cresce. Puoi anche impostare il numero di risultati che desideri vedere in una singola vista.

## Configurazione dei Tag

I singoli tag ereditano le impostazioni dalle opzioni del componente Tag. Questo
argomento è trattato in un tutorial separato. [DaFare] Seleziona il pulsante **Opzioni** nella barra degli strumenti della pagina dell'elenco Tag.

La configurazione del componente Tag può essere sovrascritta a livello di voce di menu.

## Suggerimenti

- Ricorda che i Tag sono utilizzati in diversi tipi di contenuti
- Puoi aggiungere più di un Tag a un elemento
- Usa il pulsante Guida se non sei sicuro

*Tradotto da openai.com*

