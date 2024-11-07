<!-- Filename: J4.x:Adding_a_New_Article / Display title: Articolo: Modifica - Contenuto  -->

## Introduzione

L'articolo *Aggiungere un articolo* è stato trattato in un articolo della serie *Primi passi*. Questo è il primo di una serie di articoli che forniscono più dettagli sul modulo *Articolo: Modifica*. Copre la scheda *Contenuto* e alcuni aspetti dell'editor TinyMCE, l'editor predefinito fornito con Joomla.

Lo screenshot seguente mostra il modulo di modifica con un articolo che è già stato salvato.

![Il modulo di modifica del contenuto](../../../en/images/articles/articles-edit-content.png)

## Inserimento dati

Il modulo di modifica dell'articolo ha pannelli a schede. Un nuovo articolo ha la scheda **Contenuto** selezionata per impostazione predefinita. Altrimenti, viene selezionata l'ultima scheda aperta.

### Il campo Titolo

Il campo **Titolo** è *obbligatorio* e viene utilizzato ovunque venga visualizzato il titolo dell'articolo. Questo è l'unico campo che deve contenere del testo per poter salvare un modulo di modifica.

I titoli dovrebbero essere brevi ma descrittivi del contenuto dell'articolo, poiché appaiono in elenchi e voci di menu dove lo spazio è limitato.

I titoli non devono essere unici, anche se è meglio che lo siano. Ad esempio, se si seleziona *Salva come copia* dal menu a discesa *Salva e chiudi*, il processo di salvataggio salverà l'articolo corrente e ne creerà uno nuovo con un numero aggiunto al Titolo e all'Alias. Puoi rimuovere il numero dal Titolo ma non dall'Alias e *Salvare* la copia. Ciò comporta due articoli con lo stesso titolo visualizzato.

### Il campo Alias

Il campo *Alias* è solitamente lasciato vuoto. Quando l'articolo viene salvato, l'Alias viene generato dal titolo convertendolo tutto in minuscolo e sostituendo i caratteri non alfanumerici con trattini.

Se cambi il titolo dell'articolo, puoi eliminare l'Alias e ne verrà generato uno nuovo. Se l'Alias è stato utilizzato per riferirsi all'articolo in collegamenti interni ed esterni, ciò romperà i collegamenti. Quindi è meglio non cambiare l'Alias di un vecchio articolo.

### La scheda Contenuto - Testo dell'articolo

Lo screenshot sopra mostra il testo dell'articolo in un editor WYSIWYG che assomiglia a un elaboratore di testi. Tuttavia, è importante tenere presente che il testo dell'articolo viene memorizzato come HTML e il campo di inserimento dati è in realtà un'area di testo che contiene quell'HTML. Puoi vederlo tu stesso selezionando il pulsante *Toggle Editor* sotto l'area di modifica. L'editor è infatti un'applicazione JavaScript che ripristina l'HTML per renderlo facile da leggere e manipolare.

#### Tag e attributi HTML non consentiti

Sia Joomla che l'editor TinyMCE hanno impostazioni che vietano determinati tag e attributi HTML. Ad esempio, l'elenco dei tag vietati di default di Joomla include *iframe*, quindi se provi a includere quel tag in un articolo verrà rimosso silenziosamente al momento del salvataggio. I filtri di testo sono impostati nella *Configurazione globale*. Il plugin TinyMCE ha un'opzione per *Usa filtro di testo Joomla*. Se impostato su *Off*, elenca *script, applet, iframe* come *Elementi proibiti*.

#### Barre degli strumenti dell'editor

Sopra l'area di testo ci sono righe di barre degli strumenti. Due sono visualizzate per impostazione predefinita. Le altre possono essere attivate selezionando il simbolo dei puntini di sospensione (...) alla fine della seconda barra degli strumenti. Le barre degli strumenti possono essere configurate per mostrare diverse barre e contenuti di barra a diversi gruppi di utenti.

Ci sono troppi strumenti per descriverli tutti qui. Questo creerebbe un pagliaio in cui cercare un ago. Esplora!

Tuttavia, ci sono alcune funzionalità che meritano una spiegazione aggiuntiva.

#### Contenuto CMS

Questo pulsante rivela un elenco a discesa che consente l'inclusione di elementi in un articolo ottenuti da altre parti del CMS.

- **Articolo** Questo collegamento rivela un elenco popup di articoli. Seleziona un articolo per includere un collegamento a quell'articolo nell'articolo corrente.
- **Contatto** Include un collegamento a un Contatto nell'articolo corrente.
- **Campo** Include un campo nell'articolo. Viene visualizzato come `{field 1}`.
- **Media** Include un'immagine o un file da un popup del componente Media.
- **Menu** Include un collegamento a un elemento Menu da un elenco popup dei menu.
- **Interruzione di pagina** C'è un prompt per un *Titolo della pagina* e un *Alias sommario*. Questa funzione è utilizzata per suddividere documenti lunghi in diverse pagine.
- **Leggi di più** Un separatore *Leggi di più...* viene inserito alla posizione del cursore. Scegli un'interruzione tra i paragrafi prima della selezione.

#### Link esterni

L'elemento **Inserisci** nella prima barra degli strumenti ha opzioni per inserire un *Link...*, *Immagine...* o *Media...*. Questi sono per elementi esterni, quindi tieni pronta l'URL dell'elemento da utilizzare.

### La scheda Contenuto - Impostazioni

La scheda **Contenuto** è occupata principalmente dall'editor TinyMCE.

Accanto al contenuto, ci sono campi per gestire la pubblicazione, come e dove l'articolo verrà visualizzato e chi può vederlo una volta pubblicato. Nella maggior parte dei casi, queste impostazioni possono essere lasciate ai valori predefiniti.

1.  **Stato** *Pubblicato*, *Non pubblicato*, *Archiviato* o *Cestinato* - il predefinito è *Pubblicato*.
2.  **Categoria** Questo è un campo *Obbligatorio* ma predefinito a *Non categorizzato*. Puoi selezionare una categoria dall'elenco o digitare alcuni caratteri del nome di una categoria per ridurre l'elenco delle categorie tra cui scegliere.
3.  **In primo piano** Alterna tra *No* e *Sì* per visualizzare l'articolo nella home page se utilizza un layout di *Articoli in primo piano*.
4.  **Accesso** Il livello di accesso può essere modificato per limitare l'articolo ai gruppi di utenti assegnati a specifici *Livelli di accesso*: *Pubblico*, *Ospite*, *Registrati*, *Speciale* o *Super Utenti*.
5.  **Tag** Inizia a digitare per trovare e selezionare tag predefiniti o puoi aggiungerne uno nuovo digitandolo e **premendo invio**.
6.  **Nota** Qualsiasi commento su questo articolo sarà visibile sotto il Titolo nella pagina dell'elenco degli articoli.
7.  **Nota di versione** Aggiungi commenti per indicare cosa è cambiato in questa versione. Questo viene visualizzato nella finestra di dialogo *Versioni* e il campo ritorna vuoto dopo il salvataggio.

### Altre schede

**Potresti non vedere tutte le seguenti schede** poiché un amministratore del sito potrebbe nasconderne alcune per aiutare a mantenere la coerenza del layout degli articoli su tutto il sito web. Potresti anche vedere schede aggiuntive per *Campi personalizzati* se sono stati configurati.

1.  **Immagini e collegamenti** ti permette di impostare un'immagine di introduzione e in primo piano e/o collegamenti da visualizzare in posizioni predefinite. Questo può essere usato se il tuo articolo verrà visualizzato all'interno di un blog di categoria.
2.  **Opzioni** ti permette di specificare il layout dell'articolo e le informazioni associate come il titolo, la categoria, i tag, i dettagli di pubblicazione ecc. Questo è normalmente impostato globalmente ma può essere specifico dell'articolo attraverso queste opzioni.
3.  **Schema** è un metodo per aggiungere metadati a un articolo. Viene utilizzato dai robot ma non è visibile dagli esseri umani.
3.  **Pubblicazione** ti permette di impostare date e orari di pubblicazione per programmare la pubblicazione di un articolo. Per impostazione predefinita, quando un articolo viene salvato, sarà pubblicato immediatamente. Puoi anche impostare i metadati dell'articolo.
4.  **Configura schermata di modifica** ti permette di mostrare o nascondere i parametri per l'articolo.
5.  **Permessi** mostra i permessi per ogni gruppo di utenti che controllano cosa può o non può essere fatto.

Ci sono articoli separati su ciascuna di queste schede.

## Salvare l'articolo

Una volta che hai aggiunto le informazioni e il contenuto richiesti, puoi salvare l'articolo. Ci sono diversi modi per farlo a seconda di ciò che desideri fare successivamente in Joomla.

Per salvare l'articolo, puoi scegliere di *Salvare* o *Salvare & Chiudere*. Quest'ultimo ha opzioni a discesa come *Salvare & Nuovo*, *Salvare nel Menu* e *Salvare come Copia*.

- **Salvare** Salva l'articolo e mantienilo aperto per ulteriori modifiche. È buona pratica salvare regolarmente il tuo lavoro su articoli più lunghi.
- **Salvare & Chiudere** Salva l'articolo e vai alla lista degli Articoli. Il pulsante Salvare & Chiudere ha ulteriori opzioni a discesa:
  - **Salvare & Nuovo** Salva l'articolo e quindi apri una pagina **Articoli: Nuovo**. Questa opzione risparmia tempo quando si aggiungono più articoli.
  - **Salvare nel Menu** Salva l'articolo e apri una pagina **Menu: Nuovo Elemento**.
  - **Salvare come Copia** Salva l'articolo quindi apri una pagina **Articoli: Modifica** con un numero tra parentesi aggiunto al titolo e lo stesso numero seguito da un trattino, -2 per esempio, nel campo alias. Puoi cambiare il titolo e modificare o eliminare l'alias del nuovo articolo che è stato già creato.

Un messaggio di sistema indicherà che l'articolo è stato salvato con successo.

### Errori nel tentativo di salvare:

- Se non hai completato i campi richiesti, apparirà un messaggio di errore rosso che indicherà le informazioni mancanti che devi aggiungere.
- Vedrai un messaggio di errore se l'articolo ha un alias che esiste già. Puoi superare questo problema modificando il campo alias.

## Suggerimenti

- Se non sei il Super User o l'Amministratore, prenditi del tempo per
  capire come è impostato il sito web. Solo perché hai salvato un
  articolo, non significa che sia visibile sul sito. Se vengono usate le
  pagine di Categoria Blog, assegnando la categoria corretta l'articolo
  verrà visualizzato. Altrimenti, un articolo deve essere assegnato a un elemento del menu. Puoi fare questo nell'articolo o tramite il menu **Menu** dell'Amministratore.
- Cerca di mantenere i titoli degli articoli brevi e specifici.
- Anche se è possibile, se ci sono diversi utenti che aggiungono articoli al
  sito web, evita di creare nuove categorie e tag negli articoli.
  Errori di ortografia e differenze possono facilmente impedire agli articoli di
  essere visualizzati dove erano previsti. Creare categorie e tag nella
  rispettiva pagina dell'elenco garantisce coerenza in tutto il sito.
- Se necessario, usa le note degli articoli. Possono essere molto
  utili, specialmente quando molte persone aggiungono articoli.
- Ovunque ti trovi in Joomla puoi aggiungere un articolo senza andare al
  cruscotto principale - usa il Menu dell'Amministratore di Joomla.

