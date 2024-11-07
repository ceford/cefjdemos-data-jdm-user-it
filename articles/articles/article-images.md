<!-- Filename: Adding_an_image_to_an_article / Display title: Articolo: Modifica - Immagini  -->

## Introduzione

È importante comprendere che le immagini per i documenti web sono memorizzate separatamente dal testo HTML. Quando viene richiesta una pagina web, il browser recupera prima il testo e file di supporto separati come fogli di stile e script JavaScript. Le immagini vengono recuperate successivamente. Spesso il browser e il server web negoziano quale versione di un'immagine recuperare per adattarsi alla dimensione e risoluzione dello schermo del browser. Esiste persino un'estensione di Joomla disponibile che crea diverse versioni di un'immagine principale in diverse dimensioni e formati per migliorare la velocità di consegna e rendering.

Le immagini sono incorporate nelle pagine web mediante l'inclusione di link opportunamente formattati. Esistono due meccanismi diversi per includere immagini negli articoli:

- La scheda *Contenuto* del modulo di modifica consente l'inserimento di uno o più link di immagini direttamente nel testo dell'articolo. Questo è l'argomento di questo articolo.
- La scheda *Immagini e Link* del modulo di modifica prevede l'inclusione di un'immagine come *Immagine Introduttiva* o *Immagine Articolo Completo* oppure entrambi. Questo è trattato in un articolo separato su [Immagini e Link](jdocmanual?article=user/articles/article-images-and-links).

Vale la pena fare una distinzione tra immagini locali e immagini remote:

- **Immagini Locali** si trovano sullo stesso sito dell'installazione di Joomla, di solito nella cartella *immagini*. I link delle immagini non necessitano di includere il protocollo e il nome di dominio poiché sono presi dalle impostazioni del sito.
- **Immagini Remote** si trovano altrove su internet. È necessario includere il protocollo e il nome di dominio nel link. L'uso di immagini remote tramite tale *hot-linking* potrebbe essere consentito oggi ma non domani. L'utilizzo di immagini remote senza permesso è considerato una cattiva etichetta o addirittura un furto.

## Aggiunta di un'immagine locale

Il modo migliore per inserire immagini locali è utilizzare il pulsante **CMS Content → Media** nella barra degli strumenti di modifica di TinyMCE. Questo apre una finestra di dialogo Media che consente di selezionare qualsiasi immagine nella cartella delle immagini del sito.

**Importante:** Posiziona prima il cursore nel punto in cui desideri che l'immagine appaia. Questo potrebbe essere all'inizio o alla fine di un paragrafo o in un paragrafo vuoto.

![La finestra di dialogo popup dei media](../../../en/images/articles/articles-edit-images-media.png)

Nella finestra di dialogo popup, naviga fino all'immagine che vuoi utilizzare e selezionala. Al momento della selezione apparirà un modulo che richiederà ulteriori dati.

- **Descrizione Immagine (Testo Alt)** Questo è importante per scopi di accessibilità e conformità con gli standard web.
- **Classe Immagine** Se un'immagine viene utilizzata senza didascalia, possono essere applicate alcune classi personalizzate qui. Ad esempio, *float-end ms-2 mb-1* allineerà l'immagine a destra e il testo fluirà attorno ad essa con margini a sinistra e in basso per evitare che il testo tocchi l'immagine.
- **Classe Figura** Se viene impostata una didascalia, una classe di allineamento, se presente, può essere applicata alla Figura. Nota che in Cassiopeia i margini vengono applicati alla figura tramite il foglio di stile del modello, quindi *float-start* o *float-end* sono sufficienti.
- **Didascalia Figura** Abilita la didascalia che visualizza il contenuto di questo campo come una didascalia sotto l'immagine.

**Importante:** Se il campo *Didascalia Figura* è vuoto, l'immagine verrà inserita all'interno di un tag `<img...>` e non verrà utilizzato il campo *Classe Figura*. Se il campo *Didascalia Figura* contiene testo, il tag `<img...>` sarà incapsulato nei tag `<figure>...</figure>`. Le classi più utili da aggiungere sono *float-start* e *float-end* per posizionare l'immagine a sinistra o a destra della pagina con il testo che fluisce attorno ad essa.

Seleziona il pulsante *Inserisci Media* per inserire l'immagine. La schermata Inserisci Immagine si chiuderà e l'immagine verrà visualizzata nell'editor. Oppure seleziona il pulsante *Annulla* per uscire dalla schermata Inserisci Immagine.

**Suggerimento:** seleziona il pulsante Toggle Editor per vedere gli stili applicati a Immagine e Figura. Potrebbe essere necessario tagliare e incollare una figura o un'immagine per spostarla.

### Uso della funzione Drag and Drop per immagini locali

Puoi trascinare un'immagine dal desktop o da un browser di file direttamente nel testo dell'articolo e l'immagine verrà caricata nella cartella media e inserita nell'articolo. L'unico inconveniente è che tutte le immagini caricate in questo modo verranno inserite nella stessa cartella media.

La posizione della *Directory Immagini* utilizzata per il caricamento e se questa funzione è abilitata (attiva per impostazione predefinita) sono impostate nelle Opzioni di configurazione di TinyMCE.

## Aggiungere un collegamento a un'immagine remota

Se l'immagine che desideri utilizzare non si trova nella cartella delle immagini della tua installazione Joomla, sarà necessario seguire una procedura leggermente diversa.

- Seleziona **Inserisci → Immagine** dalla barra degli strumenti di TinyMCE per aprire una finestra di dialogo.
- Nel campo **Fonte** inserisci l'URL dell'immagine.
- Compila gli altri campi come richiesto.
- La scheda **Avanzate** offre alcune opzioni di formattazione applicate come stili in linea. Prova con 1rem, 2, groove.

![La finestra di dialogo di inserimento immagine](../../../en/images/articles/articles-edit-images-external-image.png)

### Usare il Drag and Drop per inserire collegamenti a immagini remote

Puoi trascinare e rilasciare un link a un'immagine da un sito web remoto direttamente nel testo del tuo articolo. Ma fai attenzione, poiché ciò potrebbe copiare anche il contenitore HTML dell'immagine con dichiarazioni di classe non valide per il tuo sito.

## Caricamento di immagini utilizzando la finestra di dialogo Media

Puoi caricare nuove immagini nella cartella delle immagini dalla pagina 
*CMS Content -> Media*.

- Apri la finestra di dialogo Media e naviga fino alla cartella in cui desideri
  memorizzare le nuove immagini per l'articolo corrente.
- Seleziona il pulsante Carica in alto a sinistra nella schermata Media per aprire un
  browser dei file.
- Seleziona i file immagine che desideri caricare. Seleziona Apri nel browser
  dei file per confermare la selezione. Nota: Lo stile e il layout del browser
  dei file dipendono dal browser e dal sistema operativo in uso.
- I file selezionati appaiono in ordine alfabetico nella schermata Media/Immagine.
- Quando il caricamento è completo, un avviso di conferma verde apparirà in
  cima allo schermo.

Puoi ora selezionare e inserire l'immagine caricata come prima.

