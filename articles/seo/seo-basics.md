<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Nozioni di base sulla SEO -->

## Definizione

L'ottimizzazione dei motori di ricerca è il processo di miglioramento di una vasta gamma di caratteristiche di un sito web con l'intenzione di migliorare la posizione nella quale si classifica nei motori di ricerca.

Il processo di ottimizzazione di un sito web è sfaccettato poiché ci sono molti fattori che influenzano la posizione di una pagina nei risultati di un motore di ricerca.

- Garantire che i contenuti abbiano una struttura adeguata utilizzando l'HTML semantico
- Migliorare la qualità del contenuto delle singole pagine.
- Assicurarsi che il sito web possa gestire le richieste rapidamente.
- Abilitare URL amichevoli per i motori di ricerca per rendere l'indirizzo web delle pagine *leggibile dall'uomo*.
- Aggiungere markup semantico contestuale utilizzando i dati Schema.

Risorsa: [Search Engine Optimization (SEO) Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

## Struttura del Sito e URL Descrittivi

Nei primi giorni, i siti web erano strutturati come singoli file HTML in una gerarchia ad albero. Alcuni siti web sono ancora strutturati in questo modo. I CMS sono diversi. Le singole pagine sono assemblate da contenuti memorizzati in tabelle di database. Gli URL per i primi e i secondi sono diversi, forse in questo modo:

```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```

Chiaramente il primo è più facile da ricordare e da digitare. I motori di ricerca li preferiscono.

Nel CMS Joomla un URL del primo tipo può essere impostato come segue:

1. Crea una Categoria Contenuto chiamata **Utente**.
2. Crea una Categoria Contenuto chiamata **SEO** che sia figlia di *Utente*.
3. Crea un articolo e assegnalo alla categoria *SEO*.
4. Crea un elemento di menu **Utente** di tipo **Elenco Categoria** utilizzando la categoria *Utente*.
5. Crea un elemento di menu **SEO** di tipo **Elenco Categoria** utilizzando la categoria *SEO*.
6. Configura la funzionalità SEO di Joomla in *Configurazione Globale*.

Provalo con il tuo URL SEO: naviga tramite gli elenchi Utente e SEO fino alla pagina SEO Basics. I Breadcrumbs dovrebbero mostrare: `Sei qui: Home / Utente / SEO / SEO Basics`. Ma non se hai creato un tipo di voce di menu Articolo Singolo per *SEO Basics*!

## Ridurre la Duplicazione

Il problema con i CMS è che lo stesso contenuto può essere reso disponibile con URL diversi. Nell'esempio sopra, entrambe le URL funzioneranno (ma non su questo sito), così come `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Solo uno di questi dovrebbe essere riconosciuto dai motori di ricerca e impostato come URL **canonico**. Ma quale e come?

Il plugin **System - SEF** fornisce alcuni aiuti. Ha tre impostazioni:

- **Dominio del Sito** Se il tuo sito può essere accessibile tramite più di un dominio, inserisci qui il dominio preferito (a volte chiamato canonico). **Nota:** `https://example.com` e `https://www.example.com` sono domini diversi.
- **Gestione rigorosa di index.php** Questa opzione abilita una gestione più rigorosa di `index.php` negli URL quando **Usa Riscrittura URL** è abilitato nella Configurazione Globale. Rimuoverà `index.php` se un URL lo contiene ancora e reindirizzerà le richieste in arrivo con `index.php` alla versione senza `index.php`.
- **Barra finale per URL** Forza Joomla a utilizzare solo URL con o senza barra finale. Quando impostato, questo forzerà l'URL corretto con reindirizzamenti e viene applicato solo quando 'Aggiungi suffisso agli URL' è disabilitato.

Altrimenti, vedi la spiegazione dei **Tag Canonici** di [Daniel Morell](https://www.danielmorell.com/blog/how-to-create-joomla-canonical-tags).

## Qualità del Contenuto

Rendi ciò che scrivi interessante e facile da leggere. I paragrafi lunghi sono spesso opprimenti e difficili da leggere. I paragrafi di una sola riga sembrano sbagliati! Forse dovrebbero essere davvero punti elenco. Mira a paragrafi di circa tre righe. Leggi ciò che scrivi ed elimina le parole non necessarie.

Mantieni il tuo contenuto aggiornato ed evita di copiare informazioni da altri siti. Se possibile, verifica il tuo contenuto.

### HTML Semantico

Il contenuto dovrebbe consistere in una gerarchia di intestazioni e paragrafi con altri elementi secondo necessità (elenchi, tabelle e così via). Non confondere la struttura con l'aspetto - quindi non utilizzare un'intestazione per rendere il testo in grassetto o il testo in grassetto per creare un'intestazione. Questo è un esempio di marcatura semantica di un articolo:

```html
  <h2>Using headings</h2>
  <p>This is an article about the importance of headings.</p>

  <h2>Why use headings?</h2>
  <p>It is important to use headings so that search engine bots can tell what
  is an <strong>important</strong> part of your article.</p>

  <h3>Types of headings</h3>
  <p>You can use set types of headings, but they should be ordered, and
  structured, within your page.  H1 will be the page title inserted by Joomla,
  with H2 being used for sub-headings of the page.  Any headings within your
  sub-headings should cascade using H3, H4, and H5 as appropriate.</p>

  <h2>Is it hard to implement headings?</h2>
  <p>It is really easy to implement headings, you just use the appropriate
  HTML code.</p>
```

Si noti che un articolo *Titolo* diventerà un'intestazione `<h1>` se necessario, quindi non usarlo nel corpo dell'articolo.

## Prevedere i Termini di Ricerca

Scegli titoli espliciti per le tue pagine e intestazioni all'interno delle pagine. Ad esempio, se non sai cosa sia *HTML Semantico* o vuoi ulteriori informazioni su quell'argomento, quelle sarebbero le parole che inserisci in un motore di ricerca. Pensa alle persone che potrebbero essere interessate alle informazioni che stai fornendo. Cosa cercheranno? Ma mantieni i titoli e le intestazioni abbastanza brevi - alcune fonti dicono non più di 60 caratteri.

## Cura con le Pubblicità

Niente scoraggerà di più i visitatori del sito di quanto facciano gli annunci pubblicitari che compaiono qui, lì e ovunque, spostando le vere informazioni davanti ai tuoi occhi. Gli annunci che cambiano ogni pochi secondi sono anche fastidiosi e un consumo di risorse per l'utente finale. Molti utilizzeranno i blocchi per gli annunci!

## Attenzione ai link

I collegamenti sono sia una benedizione che una maledizione! Possono influenzare il rating SEO del tuo sito in modo positivo o negativo a seconda che tu abbia collegamenti a fonti affidabili o inaffidabili. E devono essere mantenuti. Potresti avere collegamenti a articoli interni o esterni che sono scomparsi, presentano informazioni obsolete o non sono più pertinenti. Il miglior consiglio: collega se la destinazione apporta un beneficio reale ai visitatori del tuo sito e usa l'attributo di collegamento `nofollow` se non desideri che il sito di destinazione sia associato al tuo sito.

Ci sono molti strumenti di controllo dei link disponibili, alcuni gratuiti o freemium e altri a pagamento, spesso come parte di un servizio di monitoraggio del sito.

## Titolo della Pagina e Descrizione

Nel `<head>` di ogni pagina dovrebbe esserci un tag `<title>` e un tag `<description>`. Joomla rende molto facile impostare un titolo diverso per ogni pagina. Sfortunatamente, rende anche molto facile trascurare di impostare un Titolo e una Descrizione adeguati su ogni pagina.

Ad esempio, prendi la pagina di elenco della categoria **SEO** menzionata sopra. Il codice sorgente della pagina `<title>` dice **SEO** e alla `<description>` manca. Nel modulo **Menu: Modifica Elemento** per questo elemento di menu, c'è una scheda **Visualizzazione Pagina** con un campo **Titolo della Pagina del Browser**. Inserisci `SEO - Elenco degli Articoli` lì e questo è ciò che appare nel tag `<title>` e nella scheda del browser.

Nella scheda **Metadata**, con il campo **Meta Description** impostato su `List of articles on Search Engine Optimisation.`, è esattamente ciò che appare nel campo `<description>`. La Descrizione a volte viene utilizzata per accompagnare il titolo di una pagina nei risultati di ricerca, quindi dovrebbe essere rilevante.

Maggiori informazioni:  
* Articolo della rivista: [Joomla SEO title tags](https://magazine.joomla.org/all-issues/september/joomla-seo-title-tags)  
* [Esplora il Core: Opzioni SEO Nativi](https://magazine.joomla.org/all-issues/june/explore-the-core-native-seo-options)

## Ottimizzare le immagini

Inutile dire che immagini attraenti possono migliorare enormemente un sito. Ma troppe immagini troppo grandi attirano penalità SEO. Ecco alcuni consigli:

- Posizionare le immagini accanto al testo che illustrano.
- Utilizzare un testo **alt** descrittivo.
- Usare nomi di immagini separati da trattini, ad esempio cat-on-hot-tin-roof.jpg.
- Utilizzare il tipo di immagine giusto per il lavoro: png per i poster, jpg per le fotografie.
- Usare immagini responsive - c'è un [plugin Joomla](https://responsive-images.dgrammatiko.dev/) che crea dinamicamente versioni webp di immagini png e jpg in diverse dimensioni.

*Tradotto da openai.com*

