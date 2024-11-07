<!-- Filename: J4.x:Template_Basics / Display title: Nozioni di Base sui Modelli -->

## Introduzione

In Joomla! un template è una raccolta di file che insieme definiscono l'aspetto del sito web. Joomla 4 fornisce due template: Atum è il template dell'amministratore utilizzato per la gestione del sito; e Cassiopeia è il template del sito utilizzato per i visitatori del sito. Molti altri template per siti sono disponibili da fornitori indipendenti, sia gratuiti che a pagamento. Infatti, esiste un'intera industria basata sulla fornitura di template specializzati per siti.

Un tipico template per siti contiene file PHP per disporre il contenuto e file CSS per stilizzare il contenuto. Spesso ci sono file aggiuntivi come immagini utilizzate nel layout e file JavaScript usati per interagire con le funzionalità del sito come collegamenti e pulsanti. Il seguente screenshot mostra le cartelle e i file del template Cassiopeia in una nuova installazione di Joomla 4:

![templates customise cassiopeia page](../../../en/images/templates/templates-customise-cassiopeia.png)

Nota che i file php si trovano nella cartella /templates del sito e i file multimediali si trovano nella cartella /media del sito.

## Posizioni del Template

Il modello del sito definisce le posizioni del contenuto principale, ad esempio un articolo individuale o un layout di blog con articoli in evidenza, e di eventuali moduli da visualizzare sopra, sotto, a sinistra o a destra del contenuto principale. La seguente illustrazione mostra le posizioni disponibili in Cassiopeia:

![diagramma delle posizioni del template](../../../en/images/templates/cassiopeia-template-positions.png)

Inoltre, è possibile vedere le posizioni del template in qualsiasi template impostando Anteprima delle posizioni dei moduli su Abilitato nel modulo Opzioni Template e quindi aggiungendo ?tp=1 all'URL. Se c'è già una stringa di query aggiunta all'URL, allora aggiungi &tp=1 invece.

## Stile dell'Utente

Cassiopeia offre alcune opzioni che puoi modificare per alterare l'aspetto del sito (esiste un articolo separato sulla personalizzazione di Cassiopeia). Questo potrebbe non essere sufficiente per i tuoi scopi. Puoi apportare le tue modifiche all'aspetto con un foglio di stile user.css. Devi crearlo tu stesso nel modulo Templates: Customise. Basta selezionare Nuovo File e inserire Nome File: user, selezionare Tipo di File: .css e scegliere la cartella css dall'elenco. Quindi seleziona il file user.css appena creato nel modulo di Modifica ed inserisci alcuni stili, ad esempio, per rendere i titoli verde scuro:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Sostituzioni del Modello

Oltre al layout complessivo definito dal modello del sito, ogni
componente o modulo ha un modello per definire il proprio aspetto
all'interno del layout generale. Tali modelli si trovano in una cartella
'tmpl' all'interno del componente o modulo. Alcuni plugin hanno anche
dei modelli. E ci sono layout che possono essere richiamati da qualsiasi
tipo di estensione.

A volte uno di questi modelli di *estensione* non è proprio di tuo
gradimento. In tal caso, puoi creare una sostituzione del modello. Si
tratta di una copia del codice utilizzato per generare il layout
dell'estensione che puoi modificare per adattarlo ai tuoi scopi. Lo
screenshot seguente mostra il Modello: il modulo 'Personalizza Crea
Sostituzioni':

![sostituzioni del modello](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Cassiopeia ha già alcune sostituzioni installate. Questo potrebbe sembrare un problema. Se modifichi uno qualsiasi dei file predefiniti di Cassiopeia, le tue modifiche verranno sovrascritte (e quindi perse) al prossimo aggiornamento di Joomla. La soluzione è nei modelli figli.

## Layout alternativi

Un template, o una sostituzione di template, definisce l'aspetto di un'estensione in un file specifico, come default.php. In alcuni casi, potresti voler scegliere tra il layout predefinito e un layout alternativo. Ad esempio, un menu in una posizione superiore solitamente necessita di un layout diverso rispetto allo stesso menu in una posizione laterale. In un modulo menu, c'è un parametro Layout nella scheda Avanzate del modulo che consente di selezionare tra i layout alternativi disponibili. C'è un tutorial separato sui Layout alternativi di template.

## Modelli Figlio

Un modello figlio utilizza i file presenti nel suo modello genitore, eccetto per i file che si trovano nel modello figlio. Ad esempio, potresti avere file user.css diversi nel genitore e nel figlio in modo che le pagine possano avere schemi di colori differenti. Oppure potresti copiare il file index.php dal genitore al figlio e modificarlo per ottenere un layout diverso da quello del genitore. Esiste un tutorial separato sui modelli figlio.

*Tradotto da openai.com*  

