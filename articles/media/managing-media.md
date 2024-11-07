<!-- Filename: J4.x:Managing_Media / Display title: Gestione dei Media -->

## Introduzione

In Joomla, i media sono immagini e file che appaiono come illustrazioni o link in articoli, moduli, template e così via. Una caratteristica importante dei media è che vengono consegnati direttamente dal server web senza essere processati dal codice Joomla. Questo è veloce ed efficiente. Inoltre, è importante essere consapevoli che i media sono solitamente memorizzati nella cartella **images** del tuo sito web Joomla. Non confondere questa con la cartella **media**, che contiene file javascript e fogli di stile.

Le immagini e i file multimediali sono gestiti con il componente Media di Joomla. Questo permette di organizzare i contenuti multimediali in una struttura a cartelle, caricare singoli elementi, eseguire alcune funzioni elementari di modifica delle immagini e inserire immagini e link direttamente negli articoli.

## Come Accedere

Dall'interfaccia di amministrazione di Joomla ci sono diversi modi per aprire
il componente Media:

- Seleziona **Contenuto → Media** dal menu dell'Amministratore.
- Seleziona **Pannello del sito → Media** dalla Dashboard principale.
- Seleziona **Contenuto CMS → Media** dalla schermata di modifica di un articolo.

Nei primi due casi, il componente Media appare in una normale schermata del componente. Nell'ultimo appare in una finestra di dialogo modale.

## Schermata

L'immagine seguente mostra la pagina Media subito dopo l'installazione di Joomla
ma con la cartella cassiopeia/sampledata selezionata. È stata aggiunta una cartella *files*
per memorizzare file non di immagine ed è stata aggiunta una cartella extra denominata *garbage*
per illustrare l'eliminazione di cartelle:

![Pagina Media che mostra i dati di esempio cassiopeia](../../../en/images/media/media-sample-data-cassiopeia.png)

## Gestione delle Cartelle

I nomi delle sottocartelle nel tuo albero delle immagini diventano parte dell'URL dell'immagine, quindi è importante per scopi di collegamento e ottimizzazione dei motori di ricerca che i nomi rispettino una convenzione:

- tutto in minuscolo
- senza spazi o punteggiatura
- se necessario, utilizza un trattino per creare parole leggibili, ad esempio alberi-decidui anziché alberi_decidui.

Prima di creare molti contenuti per il tuo sito, potrebbe essere utile pensare in anticipo a come potresti categorizzare i tuoi contenuti e forse creare un albero delle cartelle delle immagini simile al tuo albero delle categorie. Altrimenti potresti finire con un numero molto elevato di immagini e file nella radice del tuo albero delle immagini e questo diventerà difficile da gestire. Se decidi di spostare le immagini in una struttura migliore in un secondo momento, dovrai trovare i collegamenti a quelle immagini nei tuoi articoli e cambiarli. Questo potrebbe essere un compito lungo e scoraggiante!

### Navigazione nelle Cartelle

Utilizza l'albero delle cartelle nella colonna **Locale** per selezionare una cartella. Nel caso illustrato sopra, è stata prima selezionata la cartella cassiopeia. Ciò ha rivelato la cartella *sampledata* che è stata poi selezionata per mostrare il suo contenuto.

La posizione attuale è indicata anche nel percorso ("breadcrumbs") sopra le immagini. In questo caso **immagini → cassiopeia → sampledata**.

Se selezioni una cartella diversa, la cartella precedente allo stesso livello si chiude.

### Creazione di una cartella

- Seleziona la cartella principale sotto la quale la nuova cartella dovrebbe essere creata.
- Seleziona il pulsante **Crea Nuova Cartella**.
- Nella finestra popup *Crea Nuova Cartella*, inserisci un nome per la cartella nel campo **Nome Cartella**.
- Clicca sul pulsante **Crea**.
- La nuova cartella apparirà nella cartella principale selezionata insieme a un messaggio di sistema verde di Successo.

### Eliminazione di una cartella

**Attenzione: l'eliminazione di una cartella eliminerà anche tutti i contenuti della cartella!**

- Seleziona la cartella principale della cartella da eliminare utilizzando l'albero delle directory mostrato sotto **Locale**. Questo mostrerà tutte le cartelle e i file nella cartella principale.
- Sposta il cursore sulla cartella da eliminare nell'area multimediale. Diventerà grigia e un pulsante apparirà vicino all'angolo in alto a sinistra.
- Seleziona il pulsante. Un segno di spunta apparirà per indicare che è selezionato.
- Seleziona il pulsante **Elimina** dalla Barra degli Strumenti.
- Nella finestra di dialogo **Conferma Eliminazione** seleziona il pulsante **Elimina**. La cartella sarà eliminata insieme a tutti i suoi file, sottocartelle e i loro file.

La cartella selezionata per l'eliminazione è illustrata qui sotto:

![Pagina dei media che mostra la cartella spazzatura](../../../en/images/media/media-sample-data-garbage-select.png)

## Barra degli Strumenti dell'Area Media

Questa è la barra sopra l'elenco di immagini, file e cartelle che presenta pulsanti per una varietà di compiti.

### Casella di Selezione

Una casella di controllo che ti permette di selezionare tutti gli elementi nella cartella mostrata nell'area media. Potresti volerla usare per eliminare tutti gli elementi correnti senza eliminare la cartella.

### Breadcrumbs

Usa i nomi delle cartelle sopra l'area media per tornare indietro nella gerarchia delle cartelle.

Fai doppio clic su un nome di cartella nell'area media per aprire quella cartella.

### Ricerca

Se hai un lungo elenco di immagini e file, puoi cercare elementi contenenti qualsiasi gruppo di caratteri. La ricerca è progressiva: mentre aggiungi caratteri al termine di ricerca, l'elenco si riduce solo a quelli che contengono quella stringa di caratteri.

### Ingrandire

Usa i pulsanti di ingrandimento per aumentare o ridurre la dimensione delle miniature. A seconda delle dimensioni del tuo schermo, potresti vedere 2, 4, 6 o 8 immagini in miniatura affiancate.

### Vista Elenco o Miniature

Nella vista miniature, seleziona il simbolo dell'elenco per passare alla vista elenco. Nella vista elenco, seleziona il simbolo delle miniature per passare alla vista miniature. Nella vista elenco vedrai informazioni sulla dimensione e le dimensioni delle immagini, tra altri dati.

### Icona Informazioni

Seleziona l'icona delle informazioni per aprire un pannello laterale che mostra informazioni su ciò che è selezionato.

*Tradotto da openai.com*

