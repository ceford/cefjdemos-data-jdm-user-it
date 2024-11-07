<!-- Filename: Smart_Search_content_change_test_plan / Display title: Piano di Test per la Ricerca Intelligente -->

Il seguente è un piano di test approssimativo che copre (principalmente) l'aggiornamento dell'indice di Ricerca Intelligente quando si verificano vari tipi di aggiornamenti dei contenuti.

È necessario testare la Ricerca Intelligente per ciascuno dei tipi di contenuto principali supportati. Questi sono:

- Articoli
- Categorie
- Contatti
- Feed di notizie
- Collegamenti web

Per ognuno dei tipi di contenuto sopra citati, dobbiamo testare quanto segue:

## Modifiche al testo

Modificare vari campi di testo all'interno di un elemento di contenuto dovrebbe cambiare i termini di ricerca nell'indice (con un'eccezione notevole descritta di seguito). Non è necessario testare tutti i campi di testo per un determinato tipo di contenuto, poiché se funziona per uno, funzionerà per tutti; quindi, basta sceglierne uno per ciascun tipo di contenuto. I seguenti campi di testo sono indicizzati per i componenti principali:

- Articoli
  - Titolo
  - Alias
  - Testo dell'articolo
  - Descrizione dei metadati
  - Parole chiave dei metadati
  - Autore dei metadati
  - Autore
  - Creato da alias
- Categorie
  - Titolo
  - Alias
  - Descrizione
  - Link ??? (non sono sicuro che esista un campo del genere)
  - Descrizione dei metadati
  - Parole chiave dei metadati
  - Autore dei metadati
  - Autore
- Contatti
  - Nome
  - Alias
  - Nome utente collegato
  - Altre informazioni
  - Posizione (se abilitata nelle Opzioni)
  - Indirizzo (se abilitato nelle Opzioni)
  - Città (se abilitata nelle Opzioni)
  - Regione (se abilitata nelle Opzioni)
  - Paese (se abilitato nelle Opzioni)
  - CAP (se abilitato nelle Opzioni)
  - Telefono (se abilitato nelle Opzioni)
  - Fax (se abilitato nelle Opzioni)
  - Email (se abilitata nelle Opzioni)
  - Cellulare (se abilitato nelle Opzioni)
  - Pagina web (se abilitata nelle Opzioni)
- Feed di notizie
  - Titolo
  - Alias
  - Link
  - Descrizione dei metadati
  - Parole chiave dei metadati
  - Autore dei metadati
  - Autore
  - Creato da alias
- Collegamenti web
  - Titolo
  - Alias
  - URL
  - Descrizione
  - Descrizione dei metadati
  - Parole chiave dei metadati
  - Autore dei metadati
  - Autore
  - Creato da alias

Per testare, aggiungi semplicemente una stringa casuale, come "xyz", all'interno di di un testo regolare e verso l'inizio, quindi prova a cercare quel termine nel front-end.

- la tua stringa casuale dovrebbe apparire nella lista di completamento automatico mentre la digiti.
- la tua stringa casuale dovrebbe apparire 3 volte nella lista di completamento automatico.
  - da sola
  - assieme alla parola successiva che la segue
  - assieme alle 2 parole successive che la seguono
- l'elemento di contenuto contenente la tua stringa casuale dovrebbe apparire nella lista dei risultati di ricerca.
- la tua stringa casuale dovrebbe essere evidenziata nei risultati di ricerca, a condizione che tu l'abbia inserita vicino alla parte superiore del testo (poiché il testo nei risultati di ricerca è troncato).

Rimuovi la tua stringa casuale dal testo: questo dovrebbe rimuovere i 3 termini di ricerca/frasi dall'indice. Cercare uno qualsiasi dei 3 termini di ricerca non dovrebbe produrre risultati di ricerca.

Elimina l'elemento di contenuto: questo rimuoverà tutti i termini di ricerca/frasi utilizzati nell'elemento di contenuto dall'indice, tranne in quei casi in cui i termini di ricerca/frasi sono ancora utilizzati in altri elementi di contenuto.<sup>[\[1\]](#cite_note-1)</sup>

L'elemento di contenuto eliminato non dovrebbe apparire in nessuna lista di risultati di ricerca.

## Modifiche dello stato dell'elemento di contenuto

Trova un elemento di contenuto del tipo richiesto utilizzando la Ricerca Intelligente. Quindi esegui questi test:

- Sposta l'elemento nel cestino e ripeti la ricerca. L'elemento non dovrebbe più apparire nei risultati di ricerca.
- Pubblica nuovamente l'elemento e ripeti la ricerca. L'elemento dovrebbe riapparire nei risultati di ricerca.
- Annulla la pubblicazione dell'elemento e ripeti la ricerca. L'elemento non dovrebbe più apparire nei risultati di ricerca.
- Archivia l'elemento e ripeti la ricerca. L'elemento dovrebbe riapparire nei risultati di ricerca.

## Modifiche alla mappa dei contenuti (tassonomia)

Anche se le modifiche alla categoria sono un caso speciale di modifiche alla mappa dei contenuti, dobbiamo testare anche le modifiche ai rami della mappa dei contenuti non di categoria, poiché le modifiche alle categorie mettono alla prova alcuni codici diversi. Questi sono i campi non di categoria soggetti alle mappe dei contenuti nei componenti principali:

- Articoli
  - Autore
  - Categoria
  - Lingua
- Contatti
  - Categoria
  - Paese
  - Lingua
  - Regione
- Feed di notizie
  - Categoria
  - Lingua
- Collegamenti web
  - Categoria
  - Lingua

Quindi, scegli uno (se uno funziona, funzioneranno tutti per quel tipo di contenuto) di quelli sopra, che sia appropriato al tipo di contenuto, e verifica che:

- la modifica del campo faccia sì che l'elemento appaia in una ricerca utilizzando il menu a tendina pertinente (nella ricerca avanzata) per il campo che hai modificato. <sup>[\[2\]](#cite_note-2)</sup>
- l'elemento di contenuto non appaia in una ricerca utilizzando il vecchio valore del campo.

Elimina l'elemento di contenuto e verifica che non appaia più nei risultati di ricerca utilizzando il filtro a tendina pertinente. Nota che **non** ci si aspetta che un nodo non utilizzato venga rimosso dal filtro a tendina pertinente. <sup>[\[3\]](#cite_note-3)</sup>

## Modifiche di stato della categoria

Cambiare lo stato della categoria a cui un elemento appartiene dovrebbe
aggiornare l'indice per quell'elemento. Inoltre, cambiare lo stato di una
categoria genitore della categoria a cui un elemento appartiene dovrebbe anche
aggiornare l'indice per quell'elemento. Per testare, trova o crea un elemento con la
seguente struttura:

    Categoria A contenente Categoria A.1 contenente elemento di contenuto

Cambia lo stato di Categoria A.1 e testa come segue:

- Sposta nel cestino Categoria A.1 e ripeti la ricerca. L'elemento non dovrebbe più
  comparire nei risultati di ricerca.
- Pubblica nuovamente Categoria A.1 e ripeti la ricerca. L'elemento dovrebbe
  comparire nuovamente nei risultati di ricerca.
- Depubblica Categoria A.1 e ripeti la ricerca. L'elemento non dovrebbe
  più comparire nei risultati di ricerca.
- Archivia Categoria A.1 e ripeti la ricerca. L'elemento dovrebbe comparire
  nuovamente nei risultati di ricerca.

Ripristina Categoria A.1, quindi cambia lo stato di Categoria A e testa come
segue:

- Sposta nel cestino Categoria A e ripeti la ricerca. L'elemento non dovrebbe più
  comparire nei risultati di ricerca.
- Pubblica nuovamente Categoria A e ripeti la ricerca. L'elemento dovrebbe
  comparire nuovamente nei risultati di ricerca.
- Depubblica Categoria A e ripeti la ricerca. L'elemento non dovrebbe più
  comparire nei risultati di ricerca.
- Archivia Categoria A e ripeti la ricerca. L'elemento dovrebbe comparire
  nuovamente nei risultati di ricerca.

## Modifiche al livello di accesso dell'elemento di contenuto

Modifica il livello di accesso di un elemento di contenuto a qualcosa che un utente front-end non dovrebbe poter vedere.

- verifica che l'elemento di contenuto non compaia nelle liste dei risultati di ricerca.

Cambia il livello di accesso di nuovo a qualcosa che un utente front-end dovrebbe poter vedere.

- verifica che l'elemento di contenuto ora compaia nelle liste dei risultati di ricerca.

Nota che i termini di ricerca all'interno dell'elemento di contenuto appariranno ancora nella lista di autocompletamento anche se l'utente non ha accesso all'elemento di contenuto stesso. Questo è il comportamento previsto, sebbene sia qualcosa su cui potremmo voler indagare. <sup>[\[4\]](#cite_note-4)</sup>

## Modifiche al livello di accesso della categoria

Modificare il livello di accesso della categoria a cui appartiene un elemento
dovrebbe aggiornare l'indice per quell'elemento. Inoltre, modificare il livello di accesso
di una categoria genitore della categoria a cui appartiene un elemento
dovrebbe anche aggiornare l'indice per quell'elemento. Per testare, trova o crea un
elemento con la seguente struttura:

    Categoria A contenente Categoria A.1 contenente elemento di contenuto

Esegui i seguenti test:

- Modifica il livello di accesso di Categoria A.1 a qualcosa che un utente
  front-end non dovrebbe essere in grado di vedere.
  Verifica che l'elemento di contenuto non appaia nelle liste dei risultati di ricerca.
- Modifica il livello di accesso di Categoria A.1 di nuovo a qualcosa
  che un utente front-end dovrebbe essere in grado di vedere.
  Verifica che l'elemento di contenuto ora appaia nelle liste dei risultati di ricerca.
- Modifica il livello di accesso di Categoria A a qualcosa che un utente
  front-end non dovrebbe essere in grado di vedere.
  Verifica che l'elemento di contenuto non appaia nelle liste dei risultati di ricerca.
- Modifica il livello di accesso di Categoria A di nuovo a qualcosa
  che un utente front-end dovrebbe essere in grado di vedere.
  Verifica che l'elemento di contenuto ora appaia nelle liste dei risultati di ricerca.

## Modifiche allo stato di Ricerca Intelligente

Nella schermata Amministratore → Componenti → Ricerca Intelligente → Mappe di Contenuto
è possibile modificare lo stato di pubblicazione/non pubblicazione dei rami e nodi delle mappe di contenuto. I seguenti test dovrebbero essere eseguiti:

- Non pubblicare un ramo della mappa di contenuto (es. Autore).
  Verifica che il menu a tendina del filtro per quel ramo non sia più visibile
  nella ricerca avanzata.
- Non pubblicare un nodo della mappa di contenuto (all'interno di un ramo pubblicato). Per esempio,
  "Animali" all'interno del ramo "Categoria".
  Verifica che il nodo non sia elencato nel menu a tendina del filtro per il ramo
  nella ricerca avanzata.

Nella schermata Amministratore → Componenti → Ricerca Intelligente → Contenuto Indicizzato
esegui il seguente test:

- Non pubblicare un elemento di contenuto.
  Verifica che l'elemento di contenuto non appaia più nei risultati di ricerca.

Nella schermata Amministratore → Estensioni → Gestione Plugin esegui il
seguente test:

- Imposta il filtro "Seleziona tipo" su "finder" o "ricerca intelligente".
- Scegli uno dei plugin di tipo contenuto e non pubblicarlo.
  Tutti i dati per quel tipo di contenuto dovrebbero essere rimossi dall'indice.

Nota: se pubblichi di nuovo il plugin, non aggiungerà i dati di nuovo
nell'indice. Questo è il comportamento previsto. Dovrai eseguire di nuovo
l'indicizzatore per recuperare i dati.

*Tradotto da openai.com*

