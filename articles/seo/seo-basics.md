<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Fondamenti di SEO   -->

## Definizione

L'Ottimizzazione per i Motori di Ricerca (SEO) è il processo di miglioramento di una vasta gamma di caratteristiche di un sito web con l'intenzione di migliorare la posizione in cui si classifica nei motori di ricerca.

Il processo di ottimizzazione di un sito web è multifattoriale poiché ci sono molti fattori che influenzano il posizionamento di una pagina in un motore di ricerca.

- Garantire che il contenuto abbia una struttura appropriata utilizzando HTML Semantico
- Migliorare la qualità del contenuto delle singole pagine.
- Assicurarsi che il sito web possa gestire rapidamente le richieste
- Abilitare URL Amichevoli per i Motori di Ricerca per rendere l'indirizzo web delle pagine 'leggibile da un umano'
- Aggiungere Markup Semantico Contestuale utilizzando dati di Schema

Risorsa: Guida Introduttiva all'Ottimizzazione per i Motori di Ricerca (SEO)  

## Struttura del Sito e URL Descrittivi

Nei primi giorni del web, i siti erano strutturati come singoli file HTML in una gerarchia ad albero. Alcuni siti web sono ancora strutturati in questo modo. I CMS (Content Management Systems) sono diversi. Le singole pagine sono assemblate da contenuti memorizzati in tabelle di database. Gli URL per i primi e i secondi sono diversi, forse qualcosa di simile:
```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```
Chiaramente, il primo è più facile da ricordare e da digitare. I motori di ricerca li preferiscono.

Nel CMS Joomla, un URL della prima forma può essere configurato come segue:

1. Creare una Categoria di Contenuti chiamata **Utente**.
2. Creare una Categoria di Contenuti chiamata **SEO** che sia figlia di *Utente*.
3. Creare un articolo e assegnarlo alla categoria *SEO*.
4. Creare un elemento di menu **Utente** di tipo **Lista Categoria** usando la categoria *Utente*.
5. Creare un elemento di menu **SEO** di tipo **Lista Categoria** usando la categoria *SEO*.
6. Configurare la funzionalità SEO di Joomla in *Configurazione Globale*.

Testalo con il tuo URL SEO: naviga attraverso le liste Utente e SEO fino alla pagina SEO Basics. Il Breadcrumb dovrebbe mostrare: `Sei qui: Home / Utente / SEO / SEO Basics`. Ma non se hai creato un tipo di elemento di menu Articolo Singolo per *SEO Basics*!

## Riduci la Duplicazione

Il problema con i CMS è che lo stesso contenuto può essere reso disponibile con URL diversi. Nell'esempio sopra, entrambi gli URL funzioneranno (ma non su questo sito), così come `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Solo uno di questi dovrebbe essere riconosciuto dai motori di ricerca e impostato come URL **canonico**. Ma quale e come?

Il plugin **System - SEF** fornisce qualche aiuto. Ha tre impostazioni:

* **Dominio del sito:** Se il tuo sito può essere accessibile tramite più di un dominio, inserisci qui il dominio preferito (a volte chiamato canonico). **Nota:** `https://example.com` e `https://www.example.com` sono domini diversi.
* **Gestione rigorosa di index.php:** Questa opzione consente una gestione più rigorosa di 'index.php' negli URL quando 'Usa riscrittura URL' è abilitata nella Configurazione Globale. Rimuoverà 'index.php' se un URL lo contiene ancora e reindirizzerà le richieste in arrivo con 'index.php' alla versione senza 'index.php'.
* **Slash finale per gli URL:** Forza Joomla a utilizzare solo URL con o senza slash finale. Quando impostato, forzerà l'URL corretto con reindirizzamenti ed è applicato solo quando 'Aggiungi suffisso all'URL' è disabilitato.

**Spiegazione dei Tag Canonici** di Daniel Morell:

* Come Creare Tag Canonici in Joomla
* Plugin e Documentazione:

Per Joomla 4 e 5, prima di abilitare, il plugin necessita che `if ($app->isAdmin()) {` sia cambiato in `if ($app->isClient('admin')) {` alle righe 72 e 99 di *plugins /system / customcanonical / customcanonical.php*.

In un articolo, seleziona la scheda Pubblicazione e poi il pulsante *URL Canonico* **Auto**. Questo posizionerà un link come il seguente su qualsiasi pagina che visualizza l'articolo singolo:
```
	<link href="/jdm3/en/user/seo/seo-basics.html" rel="canonical" />
```

## Qualità del Contenuto

Rendi ciò che scrivi interessante e facile da leggere. I paragrafi lunghi sono spesso opprimenti e difficili da leggere. I paragrafi di una sola riga sembrano fuori luogo! Forse dovrebbero essere effettivamente punti elenco. Punta a paragrafi di circa tre righe. Leggi ciò che scrivi ed elimina eventuali parole superflue.

Mantieni il tuo contenuto aggiornato ed evita di copiare informazioni da altri siti. Se possibile, verifica il tuo contenuto.

### HTML Semantico

Il contenuto dovrebbe consistere in una gerarchia di intestazioni e paragrafi con altri elementi come richiesto (elenchi, tabelle e così via). Non confondere la struttura con l'aspetto - quindi non utilizzare un'intestazione per l'enfasi né l'enfasi per un'intestazione. Questo è un esempio di marcatura semantica di un articolo:

```html
  <h2>Uso delle intestazioni</h2>
  <p>Questo è un articolo sull'importanza delle intestazioni.</p>

  <h2>Perché usare le intestazioni?</h2>
  <p>È importante usare le intestazioni in modo che i bot dei motori di ricerca possano identificare quale parte del tuo articolo sia <strong>importante</strong>.</p>

  <h3>Tipi di intestazioni</h3>
  <p>Puoi usare tipi di intestazioni specifici, ma devono essere ordinati e strutturati all'interno della tua pagina. H1 sarà il titolo della pagina inserito da Joomla, con H2 utilizzato per i sottotitoli della pagina. Eventuali intestazioni all'interno dei tuoi sottotitoli dovrebbero scalare utilizzando H3, H4 e H5 se appropriato.</p>

  <h2>È difficile implementare le intestazioni?</h2>
  <p>È davvero facile implementare le intestazioni, basta usare il codice HTML appropriato.</p>
```
Nota che un *Titolo* di un articolo diventerà un'intestazione `<h1>` se necessario, quindi non utilizzarlo nel corpo dell'articolo.  

## Anticipare i Termini di Ricerca

Scegli titoli espliciti per le tue pagine e per i titoli all'interno delle pagine. Ad esempio, se non sai cosa sia l’*HTML Semantico* o desideri maggiori informazioni su quell'argomento, quelle sarebbero le parole che inserisci in un motore di ricerca. Pensa alle persone che potrebbero essere interessate alle informazioni che stai fornendo. Cosa cercheranno? Ma mantieni i Titoli e le Intestazioni piuttosto brevi - alcune fonti suggeriscono non più di 60 caratteri.

## Attenzione agli Annunci Pubblicitari

Niente scoraggerà i visitatori del sito più degli annunci che compaiono qui, lì e ovunque e spostano le informazioni reali davanti ai tuoi occhi. Gli annunci che cambiano ogni pochi secondi sono anche fastidiosi e un peso per le risorse degli utenti finali. Molti useranno i blocchi per gli annunci pubblicitari!

## Attenzione ai Link

I link sono sia una benedizione sia una maledizione! Possono influenzare il punteggio SEO del tuo sito in modo positivo o negativo a seconda che tu abbia collegamenti a fonti rispettabili o non rispettabili. E devono essere mantenuti. Potresti avere link a articoli interni o esterni che sono spariti, presentano informazioni obsolete o non sono più rilevanti. Il miglior consiglio: collegati se il target aggiunge un reale vantaggio per i visitatori del tuo sito e utilizza l'attributo `nofollow` per i link se non vuoi che il sito di destinazione sia associato al tuo sito.

Ci sono molti strumenti di verifica dei link disponibili, alcuni gratuiti o freemium e altri a pagamento, spesso come parte di un servizio di monitoraggio del sito.

## Titolo della Pagina e Descrizione

Nell'`<head>` di ogni pagina dovrebbe esserci un tag `<title>` e un tag `<description>`. Joomla rende molto facile impostare un titolo diverso per ogni pagina. Sfortunatamente, rende anche molto facile trascurare l'impostazione di un Titolo e una Descrizione adeguati su ogni pagina.

Come esempio, prendiamo la pagina dell'elenco della categoria **SEO** menzionata sopra. Il `<title>` del sorgente della pagina dice **SEO** e manca la `<description>`. Nel modulo **Menu: Modifica Voce** per questo elemento di menu c'è una scheda **Visualizzazione Pagina** con un campo **Titolo della Pagina del Browser**. Inserisci `SEO - Elenco di Articoli` lì e quello è ciò che appare nel tag `<title>` e nella scheda del browser.

Nella scheda **Metadati**, con il campo **Descrizione Meta** impostato su `Elenco di articoli sull'Ottimizzazione per i Motori di Ricerca.`, è esattamente ciò che appare nel campo `<description>`. La Descrizione viene talvolta utilizzata per accompagnare un Titolo di pagina nei risultati di ricerca, quindi dovrebbe essere pertinente.

Ulteriori informazioni:
* Articolo di rivista: Tag titolo SEO di Joomla
* Esplora il Core: Opzioni SEO Nativi

## Ottimizzare le Immagini

Inutile dire che immagini attraenti possono migliorare enormemente un sito. Ma troppe immagini troppo grandi attirano penalità SEO. Ecco alcuni consigli:

* Posiziona le immagini accanto al testo che illustrano.
* Usa un testo **alt** descrittivo.
* Usa parole separate da segni meno per i nomi delle immagini, ad esempio cat-on-hot-tin-roof.jpg.
* Usa il tipo giusto di immagine per il lavoro: png per manifesti, jpg per fotografie.
* Usa immagini responsive - c'è un plugin Joomla che crea dinamicamente versioni webp di immagini png e jpg in diverse dimensioni.

*Tradotto da openai.com*

