<!-- Filename: J4.x:Setup_a_Multilingual_Site / Display title: Configurare un Sito Multilingue  -->

## Dati di esempio

Joomla viene fornito con due set di dati di esempio: Blog e Multilingue. C'è un terzo set di Test ma solo per gli utenti che lavorano con la versione di Sviluppo di Joomla. Se hai un sito esistente con articoli, menu e moduli, sarà simile in linea di principio a un sito con installati i dati di esempio del Blog.

Nel cruscotto principale, i dati di esempio Multilingue dicono **Prima di avviare, assicurati di avere installato almeno 2 lingue con le loro Lingue dei Contenuti e che nessun dato di esempio sia stato installato**. Probabilmente ciò ti porterà a creare un sito multilingue eseguendo manualmente i passaggi richiesti uno per uno. Questo è un procedimento soggetto a errori in cui è probabile commettere un errore, soprattutto se stai utilizzando più lingue. Gli errori possono essere corretti, ma l'intero processo è un po' noioso e può creare confusione.

Puoi ignorare quel consiglio e utilizzare i dati di esempio multilingue per configurare un sito multilingue se comprendi come apportare alcune correzioni ai menu e moduli originali in un secondo momento.  

## Sito Iniziale

Un sito Joomla appena installato ha un **Menu Principale** nella barra laterale destra. Contiene un solo elemento di menu chiamato **Home** di tipo Articoli in Primo Piano. C'è anche un **Modulo di Accesso** nella barra laterale destra.

Inizialmente, non ci sono articoli in primo piano quindi la parte principale della pagina è vuota.

## Dati di esempio del blog

Se hai creato il contenuto del tuo sito, **non** dovresti installare i dati di esempio del blog. Tuttavia, leggi questa sezione per vedere come si confronta. Altrimenti:

- Seleziona **Installa** dalla sezione Dati di esempio multilingue del cruscotto principale. Le fasi dell'installazione appariranno brevemente e poi scompariranno.
- Dovresti notare che sono stati installati diversi nuovi menu (ricarica la pagina dell'amministratore ed espandi il menu dei menu):
  - Menu principale del blog.
  - Menu inferiore, contenente voci di menu di accesso/uscita.
  - Menu speciale, visibile dopo l'accesso.
- Seleziona l'icona **Apri frontend** dalla barra di stato in alto o ricarica il sito se è già aperto in una scheda separata.

Dovresti aspettarti di vedere un layout pieno di informazioni sugli articoli in evidenza:

- In alto si trova il nuovo menu **Menu principale del blog** per vari layout e articoli del blog.
- Nella barra laterale destra ci sono moduli per un modulo di accesso, un menu principale e un feed RSS del mio blog.
- Dopo l'accesso, la barra laterale destra presenta un menu speciale per azioni riservate all'amministratore.
- La voce **Home** del menu principale porta al layout degli articoli in evidenza.
- La voce di menu superiore **Blog** conduce a un layout di categoria del blog leggermente diverso dal layout degli articoli in evidenza.

Prenditi qualche minuto per esplorare le voci di menu e i tipi di informazioni a cui conducono.  

## Installazione e Pubblicazione delle Lingue dei Contenuti

Prima di tutto, installa tutte le lingue che intendi utilizzare. Se hai bisogno di installare una lingua aggiuntiva successivamente, dovrai completare manualmente i passaggi di configurazione per quella lingua uno per uno. Questo sarà trattato altrove. Per questo tutorial, il francese, il tedesco e il gallese sono stati aggiunti alla lingua predefinita inglese durante l'installazione di Joomla. Per aggiungere lingue dopo l'installazione:

- Seleziona **Sistema** → **Installa Lingue** dal menu dell'Amministratore.
- Seleziona il pulsante **Installa** per ciascuna lingua che intendi utilizzare.

Le lingue installate devono essere **Pubblicate** per renderle disponibili. Dal menu dell'Amministratore:

* Seleziona **Sistema / Pannello di Gestione / Lingue dei Contenuti**
* Nella colonna dello Stato, **Pubblica** ciascuna delle lingue che desideri utilizzare.

## Dati di Esempio Multilingue

L'installazione dei Dati di Esempio Multilingue ha effetti di cui dovrai occuparti successivamente:

- I menu nella barra laterale destra verranno non pubblicati. Ciò significa che il modulo del Menu Principale verrà non pubblicato e non ci sarà alcun link al layout degli Articoli in Evidenza. Se avevi altri link nel Menu Principale, anche questi saranno non disponibili.
- Il Menu Speciale verrà non pubblicato. Questo forniva un link per creare un nuovo post.

I Dati di Esempio Multilingue offrono le seguenti funzionalità aggiuntive:

- Una categoria d'articolo per ogni lingua.
- Un articolo configurato per ogni lingua, sebbene in testo pseudo Lorem ipsum.
- Un menu separato per ogni lingua. Lo vedrai nell'elenco **Amministratore**→**Menu**.
- Un modulo di menu **Main Menu xx-YY** nella barra laterale destra del Sito, dove xx-YY è un codice lingua come en-GB.
- L'elemento di menu **Main** ora conduce a un layout Blog Categoria per articoli nella Lingua selezionata. Contiene solo un articolo.
- C'è un modulo **Language Switcher** nella barra laterale destra. È senza titolo per evitare la necessità di un modulo separato per ogni lingua con titoli tradotti. La selezione avviene tramite la bandiera della lingua. Provalo.

Qualcosa da notare: le parole fornite da Joomla saranno tradotte, ad esempio nei Percorsi di Navigazione e nel Modulo di Accesso. Le parole digitate dagli utenti devono essere tradotte manualmente, ad esempio Modulo di Accesso e Menu Principale. Maggiori dettagli su questo più avanti.

## Risoluzione dei Problemi Iniziali

### Ordine delle Lingue

Potresti notare che il selettore delle lingue ha le lingue in ordine alfabetico inverso. Per cambiare l'ordine:

- Seleziona **Sistema → Lingue Contenuto** dal menu dell'Amministratore.
- Usa le icone di ellissi verticali per trascinare le lingue nell'ordine desiderato.
- Ricarica il Sito e vedrai che il Selettore delle Lingue ora ha le lingue nell'ordine da te preferito.

### Ordine dei Moduli della Barra Laterale Destra

L'ordine dei moduli nella barra laterale destra è una questione di preferenza personale. Per cambiare l'ordine:

- Seleziona **Contenuti → Moduli del Sito** dal menu dell'Amministratore.
- Filtra per **Posizione → sidebar-right**.
- Seleziona l'icona della colonna di ordinamento per rivelare le maniglie di ordinamento (icone di ellissi verticali). L'icona dell'intestazione della colonna dovrebbe essere un chevron che punta verso l'alto.
- Trascina gli elementi in ordine:
  - Selettore delle Lingue
  - Menu Principale (tutte le varianti - l'ordine non è importante).
  - Menu Speciale
  - Form di Login
  - Articoli Archiviati
  - Syndication

### Articoli in Evidenza

Il Menu Principale originale è non pubblicato ma l'elemento di menu della Home che contiene può essere riprodotto altrove. Il luogo più conveniente è il menu in alto.

- Seleziona **Menu → Blog del Menu Principale** dal menu dell'Amministratore.
- Seleziona il pulsante **Nuovo** dalla Barra degli Strumenti.
- Inserisci un **Titolo** nel modulo **Menu: Nuovo Elemento**, per esempio **In Evidenza**.
- Usa il pulsante **Seleziona** nel campo **Tipo di Elemento di Menu**.
- Seleziona **Articoli → Articoli in Evidenza** dalla lista **Tipo di Elemento di Menu**.
- Seleziona **Salva** dalla Barra degli Strumenti.
- Nel campo **Ordinamento** seleziona **- Primo -**.
- Nella scheda **Layout del Blog** imposta **Articoli di Introduzione** a 3.
- Seleziona **Salva & Chiudi** dalla Barra degli Strumenti.

### Assegnazione dei Moduli del Sito

Il layout originale degli Articoli in Evidenza della Home page è stato prodotto assegnando moduli selezionati in modo che appaiano solo su quella pagina. La nuova pagina degli Articoli in Evidenza deve essere aggiunta per ciascuno di quei moduli.

- Seleziona **contenuti → Moduli del Sito** dal menu dell'Amministratore.
- Trova e seleziona l'elemento **Immagine**.
- Nella scheda **Assegnazione del Menu**, trova e seleziona l'elemento **In Evidenza** nella sezione **Blog del Menu Principale**.
- Seleziona **Salva & Chiudi** dalla Barra degli Strumenti.
- Trova e seleziona l'elemento **Ultimi Post**.
- Nella scheda **Assegnazione del Menu**, trova e seleziona l'elemento **In Evidenza** nella sezione **Blog del Menu Principale**.
- Seleziona **Salva & Chiudi** dalla Barra degli Strumenti.

## Ricarica Sito

Quando ricarichi il sito, il primo elemento nel menu superiore sarà il
link In Evidenza che porta al layout degli Articoli in Evidenza. L'elemento Blog adiacente è un layout di Blog di Categoria più compatto. Prova il selettore di lingua. Il testo fornito da Joomla, nei breadcrumb e nel modulo di Login, cambia di conseguenza. Inoltre, ora gli articoli in evidenza includono un articolo dai Dati di Esempio Multilingue, in quella lingua selezionata. Potrebbe essere nell'ultima pagina.

### Sito Ibrido o Puramente Multilingue

A questo punto hai un sito ibrido: alcuni contenuti sono disponibili in tutte le lingue e alcuni contenuti sono disponibili in una lingua specifica. Se vuoi un sito puramente multilingue dovrai rendere non pubblicato il modulo Blog del menu principale superiore e forse anche altri. In alcuni casi potresti voler produrre moduli specifici per ogni lingua, ad esempio il modulo di Login potrebbe avere versioni con i titoli Formulaire de connexion, Login Formular e Ffurflen Mewngofnodi.

Cosa farai dopo è una tua decisione!

## Menu Principale Originale

Il tuo modulo del Menu Principale originale, che ora non è pubblicato, potrebbe aver
contenuto ulteriori voci di menu. Potresti pubblicarlo. Il problema è che
la voce Home si collega alla stessa posizione delle pagine Home del menu specifico per ciascuna lingua, ma solo in inglese. Puoi risolvere il problema nel seguente modo:

- Seleziona **Menu** → **Menu Principale** dal menu dell'Amministratore.
- Seleziona la voce di menu **Home**.
- Seleziona la scheda **Tipo di Collegamento**.
- Imposta **Visualizza nel Menu** su **No**.
- Seleziona **Salva & Chiudi** dalla barra degli strumenti.
- Seleziona **Contenuti** → **Moduli del Sito** dal menu dell'Amministratore.
- Trova il **Menu Principale** e pubblicalo, trasformando la croce grigia
  in un segno di spunta verde.

Le voci visibili nel Menu Principale originale dovrebbero ora funzionare normalmente. Se il Menu Principale non ha voci visibili, non verrà visualizzato.

## Aggiungere una Lingua Extra

Dopo la configurazione iniziale di un sito multilingue, se desideri aggiungere un'altra lingua, dovrai seguire i passaggi manualmente uno per uno:

### Passo 1: Installare la Lingua

- Seleziona **Sistema**→**Installa**→**Lingue** dal menu dell'Amministratore.
- Trova la lingua richiesta nell'elenco **Estensioni: Lingue**.
- Seleziona il pulsante **Installa**.
- Apparirà un messaggio: **Installazione del pacchetto lingua riuscita.**

In questa sequenza d'esempio, la lingua aggiuntiva è lo spagnolo.

### Passo 2: Pubblicare e Ordinare

- Seleziona **Sistema**→**Gestisci**→**Lingue dei Contenuti** dal menu dell'Amministratore.
- Abilita la nuova lingua installata: seleziona il pulsante di Stato per trasformare la croce grigia in un segno di spunta verde.
- Usa le icone con tre punti verticali per trascinare le lingue nell'ordine desiderato.

### Passo 3: Creare un Menu

- Seleziona **Menu**→**Gestisci** dal menu dell'Amministratore.
- Seleziona il pulsante **Nuovo** dalla Barra degli Strumenti.
- Inserisci un titolo adeguato per il menu e un nome univoco, esempi: Menu Principale (es-ES) e menuprincipale-es-es.
- Inserisci una Descrizione, esempio: Il menu principale per il sito in lingua spagnola (es-ES).

### Passo 4: Aggiungere un Modulo di Menu

- Seleziona **Menu**→**Gestisci** dal menu dell'Amministratore.
- Seleziona il pulsante **Aggiungi un modulo per questo menu** per il menu appena creato.
- Inserisci un titolo appropriato, esempio: Menu Principale es-ES.
- Seleziona una Posizione: Sidebar-destro.
- Seleziona una Lingua: Spagnolo (es-ES).
- Seleziona **Salva**.
- Ordina il modulo: dall'elenco Ordinamento seleziona l'elemento dopo il quale dovrebbe apparire questo nuovo elemento.
- Seleziona **Salva & Chiudi**.

### Passo 5: Aggiungere una Categoria

- Seleziona **Contenuti**→**Categorie** dal menu dell'Amministratore.
- Seleziona il pulsante **Nuovo** nella Barra degli Strumenti.
- Inserisci un titolo adeguato, esempio: Categoría (es-es).
- Seleziona la lingua corretta: Spagnolo (es-ES).
- Seleziona la scheda **Associazioni**.
- Per ogni lingua seleziona una Categoria. Ci sarà solo una scelta in ogni caso.
- Seleziona **Salva & Chiudi**.

### Passo 6: Aggiungere un Elemento di Menu

- Seleziona **Menu**→**Menu Principale (es-ES)**, il menu appena creato.
- Seleziona il pulsante **Nuovo** nella Barra degli Strumenti.
- Inserisci un titolo adeguato, esempio: Página de inicio.
- Usa il pulsante Seleziona alla fine del campo **Tipo di Elemento di Menu** per selezionare un tipo di elemento.
- Dall'elenco a comparsa seleziona **Articoli**→**Blog di Categoria**.
- Nel campo Scegli una Categoria usa il pulsante Seleziona.
- Dall'elenco a comparsa delle Categorie seleziona la categoria Categoría (es-es).
- Imposta il campo **Pagina Predefinita** su **Sì**.
- Nell'elenco a discesa **Lingua** seleziona **Spagnolo (es-ES)**.
- **Salva & Chiudi**

### Passo 7: Aggiungere un Articolo

Il modo più semplice per aggiungere un articolo per la nuova lingua è copiare un articolo esistente.

- Seleziona **Contenuti**→**Articoli** dal menu dell'Amministratore.
- Seleziona l'articolo da copiare, in questo esempio **Articolo (en-GB)**.
- Nel modulo **Articoli: Modifica** cambia il titolo in **Articolo (es-ES)**.
- Cambia la **Categoria** in **Categoria (es-es) (es-ES)**.
- Cambia la **Lingua** in Spagnolo (es-ES)**.**
- Seleziona **Salva come Copia** dall'elenco a discesa **Salva & Chiudi** nella Barra degli Strumenti. **Attenzione!**
- Seleziona la scheda **Associazioni**.
- Per ogni lingua seleziona un articolo da associare - l'articolo equivalente in ciascuna lingua.
- Seleziona **Salva & Chiudi** dalla Barra degli Strumenti.

## Aggiunta di un Articolo Multilingue

Supponiamo che tu voglia creare un articolo in ciascuna delle lingue selezionate.

- Seleziona **Contenuto** → **Articoli** → **+** dal menu dell'Amministratore
  oppure il pulsante **Nuovo** dalla Barra degli strumenti nella lista degli Articoli.
- Inserisci un titolo per l'articolo, ad esempio **William Shakespeare**.
- Imposta il campo **Categoria** su **Categoria (en-gb) (en-GB)**.
- Imposta il campo **Lingua** su **Inglese (en-GB)**.
- Inserisci il **Testo dell'Articolo**, ad esempio da Wikipedia:

"William Shakespeare (battezzato il 26 aprile 1564 – 23 aprile 1616) è stato un drammaturgo, poeta e attore inglese. È ampiamente considerato il più grande scrittore in lingua inglese e il più grande drammaturgo del mondo. Spesso è chiamato il poeta nazionale dell'Inghilterra e il "Bardo dell'Avon" (o semplicemente "il Bardo"). Le sue opere esistenti, incluse le collaborazioni, consistono in circa 39 opere teatrali, 154 sonetti, tre lunghi poemi narrativi, e pochi altri versi, alcuni di dubbia paternità. Le sue opere sono state tradotte in tutte le principali lingue viventi e vengono rappresentate più frequentemente di quelle di qualsiasi altro drammaturgo. Rimane indiscutibilmente lo scrittore più influente in lingua inglese e le sue opere continuano a essere studiate e reinterpretate."

- Seleziona **Salva** dalla Barra degli strumenti.
- Seleziona la scheda **Associazioni**.
- Per ogni lingua:
  - Seleziona il pulsante **Crea**.
  - Nel modulo popup **Nuovo Articolo** inserisci un titolo tradotto,
    **William Shakespeare**.
  - Imposta la Categoria per la lingua che hai selezionato.
  - Inserisci il testo tradotto nel campo **Testo dell'Articolo** (puoi
    provare <a href="https://translate.google.com/" rel="nofollow noreferrer noopener">https://translate.google.com/</a>).
  - Seleziona **Salva & Chiudi**.
- Dopo che un nuovo articolo per ciascuna lingua è stato creato, seleziona **Salva
  & Chiudi**.

## Menu Principale

Se hai un collegamento a un articolo per tutte le lingue nel Menu Principale e in seguito usi quell'articolo come base per articoli associati in altre lingue, dovrai modificare il collegamento nel Menu Principale. Altrimenti, cambiando lingua con quell'articolo selezionato, si incorrerà in un errore di Pagina Non Trovata nella lingua selezionata.

- Seleziona **Menu **→** Menu Principale** dal menu dell'Amministratore.
- Seleziona la voce di menu che devi modificare, ad esempio **William Shakespeare**.
- Cambia il campo **Lingua** in **Inglese (en-GB)**.
- Seleziona **Salva & Chiudi** dalla Barra degli Strumenti.

Se c'è solo quell'unico elemento nel Menu Principale, quel modulo sparirà quando si passa ad altre lingue.

*Tradotto da openai.com*

