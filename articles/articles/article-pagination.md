<!-- Filename: J4.x:Article_Pagination / Display title: Articolo: Modifica - Paginazione  -->

## Articoli Lunghi

L'unico limite sulla lunghezza di un articolo in Joomla è la dimensione del campo del database utilizzato per contenere il testo dell'articolo. Questo è molto grande! Gli articoli lunghi possono contenere molte immagini e richiedere tempo per essere elaborati, il che potrebbe risultare un inconveniente per il lettore e per il sito web. Pertanto, esiste un meccanismo semplice per suddividere gli articoli lunghi in pagine separate con una tabella dei contenuti.

## Inserisci un'interruzione di pagina

Per aggiungere interruzioni di pagina, apri prima un articolo nell'editor di testo, TinyMCE è l'impostazione predefinita, e procedi come segue:

- Posiziona il cursore nel punto in cui desideri inserire un'interruzione di pagina.
- Dall'elenco a discesa **Contenuto CMS** seleziona l'elemento *Interruzione di Pagina*.
- Nella finestra di dialogo Interruzione di Pagina inserisci:
  - *Titolo della Pagina* - questo verrà aggiunto al titolo della pagina esistente. Esempio: Pagina 2
  - *Alias Sommario* - questo verrà utilizzato come testo nel Sommario. Esempio: Capitolo 2
- Seleziona il pulsante **Inserisci Interruzione di Pagina**.

![Modulo della finestra di dialogo di interruzione di pagina](../../../en/images/articles/articles-edit-pagination.png)

- Ripeti per ogni interruzione di pagina che desideri creare.
- Salva l'articolo e dai un'occhiata all'Anteprima o alla vista del Sito.

![Vista del sito della paginazione dell'articolo](../../../en/images/articles/articles-site-pagination.png)

## Modificare o Spostare un'interruzione di pagina

Puoi selezionare un'interruzione di pagina ed eliminarla. Tuttavia, non puoi ritagliarla e incollarla e non puoi aprire un'interruzione di pagina esistente nel modulo dell'interruzione di pagina. Quindi, per spostare o cambiare un'interruzione di pagina, utilizza l'editor del codice sorgente come segue:

- Seleziona la voce **Strumenti -> Codice sorgente+** dell'editor di testo.
- L'editor del codice sorgente mostra il codice HTML sorgente con evidenziazione della sintassi.
- Scorri fino all'interruzione di pagina che desideri modificare o spostare.
- Per spostare un'interruzione di pagina:
  - Seleziona e Taglia la riga contenente l'interruzione di pagina.
  - Posiziona il cursore nella nuova posizione e Incolla la riga tagliata.
- Per modificare:
  - Cambia il testo del titolo e/o il testo alternativo secondo le tue esigenze.
- Seleziona **Salva**.
- Salva l'articolo e dai un'occhiata all'Anteprima o alla visualizzazione del Sito.

L'editor del codice sorgente si trova in una finestra di dialogo popup:

![Editor del codice sorgente](../../../en/images/articles/articles-edit-pagination-source-code.png)

*Tradotto da openai.com*

