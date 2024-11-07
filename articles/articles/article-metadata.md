<!-- Filename: J6.x:_Article_Metadata / Display title: Articolo: Modifica - Metadati  -->

## Introduzione

I metadati sono informazioni su una pagina web contenute nella prima parte della pagina tra i tag `<head>...</head>`. La maggior parte di queste informazioni non è visibile ai visitatori del sito, ma viene utilizzata dai motori di ricerca per fornire risultati appropriati per le richieste di ricerca. Pertanto, è nel tuo interesse utilizzare metadati informativi.

Alcuni degli elementi dei metadati sono forniti dal modello in uso e non è necessario impostarli personalmente. Esempi comuni:

```html
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="generator" content="Joomla! - Open Source Content Management">
```

Esistono altre forme di metadati, come i dati Open Graph utilizzati da Facebook e gli schemi usati per descrivere tipi specifici di pagine come Persona, Luogo o Prodotto. Questi non sono trattati qui.

Gli elementi di metadati che spesso vengono trascurati sono il **Titolo** della pagina, che si trova tra i tag `<title>...</title>` nella `<head>` della pagina, e la **Descrizione** della pagina, che si trova all'interno dei tag `<meta>` ma potrebbe essere assente. Essi sono trattati qui.

## Il Titolo della Pagina

Un titolo dell'articolo è necessario per qualsiasi nuova pagina. Alcune linee guida e suggerimenti per comporre buoni titoli dal Mozilla Developer Network:

>* Evita titoli di una o due parole. Usa una frase descrittiva o un abbinamento termine-definizione per pagine di glossario o di riferimento.
>* I motori di ricerca solitamente mostrano i primi 55–60 caratteri di un titolo di pagina. Il testo oltre quel limite potrebbe non essere visualizzato, quindi cerca di non avere titoli più lunghi di così. Se devi usare un titolo più lungo, assicurati che le parti importanti vengano prima e che non ci sia nulla di critico nella parte del titolo che potrebbe essere troncata.
>* Non usare "ammassi di parole chiave". Se il tuo titolo è solo un elenco di parole, gli algoritmi spesso riducono la posizione della tua pagina nei risultati di ricerca.
>* Cerca di assicurarti che i tuoi titoli siano il più unici possibile all'interno del tuo sito. Titoli duplicati - o quasi duplicati - possono contribuire a risultati di ricerca inaccurati.

Raccomandazioni aggiuntive da parte di Google:

>- Specifica un titolo unico per ogni pagina
>- Rendi il tuo titolo descrittivo del contenuto della pagina e conciso
>- Evita il riempimento di parole chiave (l'uso ripetuto di parole simili come "Foobar, foo bar, foobars, foo bars")
>- Evita i titoli generici - ogni pagina dovrebbe avere un titolo unico, idealmente aggiornato dinamicamente in relazione al contenuto visualizzato
>- Brandizza i tuoi titoli, ma fallo in modo conciso e in relazione al contenuto offerto

Esistono vari Strumenti per Webmaster che possono essere utilizzati per identificare eventuali problemi con le tue inserzioni in un particolare motore di ricerca - vale sempre la pena prestare attenzione e correggere eventuali problemi. Un esempio:

[Articolo di supporto Google sull'uso dei titoli per le tue pagine web](http://support.google.com/webmasters/bin/answer.py?hl=it&amp;answer=35624)

In Joomla, per una singola pagina il titolo dell'articolo diventa il titolo della pagina utilizzato nella testa e visualizzato nella scheda del browser. Per una pagina composita, come *Articoli in Evidenza* o un *Blog di Categoria*, il Titolo della voce di menu diventa il titolo della pagina. Pertanto, è necessario riflettere attentamente sulla composizione di buoni titoli descrittivi sia per gli articoli sia per le voci di menu.

## Descrizione della Pagina

L'articolo *Meta Description* è un campo nella scheda *Publishing* del modulo di inserimento dati dell'articolo:

![La scheda di modifica dell'articolo nella scheda di pubblicazione](../../../en/images/articles/articles-edit-publishing-tab.png)

Se non c'è una descrizione dei metadati dell'articolo, verrà utilizzata una descrizione dei metadati dell'elemento menu dell'articolo singolo se è impostata. Se non c'è una descrizione dei metadati dell'elemento menu, allora si utilizza la descrizione meta globale del sito, se è impostata. Altrimenti, il campo della descrizione dei metadati viene omesso.

Google consiglia quanto segue per garantire che si ottenga il massimo dall'indicizzazione del motore di ricerca:

>- Assicurarsi che ogni pagina abbia descrizioni meta uniche e pertinenti
>- Assicurarsi di applicare i metadati per le pagine di elenco (ad esempio, blog e layout lista) oltre agli articoli singoli - questo è comunemente trascurato sui siti Joomla!
>- Includere informazioni fattuali, se pertinenti (ad esempio, gli articoli del blog potrebbero includere l'autore, i prodotti potrebbero includere il prezzo o il produttore)
>- Considerare l'uso di metadati generati automaticamente - ma assicurarsi che siano pertinenti, leggibili e accurati.
>- Fare in modo che le vostre descrizioni siano descrittive!

Un altro riferimento:

[Articolo di supporto di Google sull'uso dei metadati](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

## Parole chiave

C'era una volta, i motori di ricerca usavano le parole chiave per aiutare a classificare i contenuti. Così, gli autori riempivano i loro metadati con un vasto numero di parole chiave sperando di aumentare il loro posizionamento SEO. E in risposta, Google ha smesso di usare le parole chiave ai fini del posizionamento. Cerca sul web consigli e troverai alcune fonti che dicono di non preoccuparsene e altre che affermano che hanno ancora valore.

Le parole chiave non sono usate dal core di Joomla. Se hai dei dubbi, non preoccuparti.

## Robot

Il valore predefinito di *Usa Globale* non inserisce un meta tag nella sezione head della pagina HTML. Altri valori lo fanno. C'è un file `robots.txt` nella directory principale del sito Joomla. Se desideri controllare i robot, dovresti leggere questo file. Contiene una spiegazione su come utilizzarlo.

## Autore

Puoi inserire il nome formale dell'autore per apparire come metadati. 

## Diritti

Puoi inserire un avviso di copyright da visualizzare come metadati.  

## Esempio di metadati

Ecco come appaiono i metadati nella visualizzazione della sorgente dell'articolo:
Qui c'è un esempio del contenuto del `<head>` dopo il completamento di tutti i campi di metadati:

```html
    <meta charset="utf-8">
    <meta name="rights" content="Charles Darwin © 1859">
    <meta name="author" content="Charles Darwin">
    <meta name="robots" content="noindex, nofollow">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Pubblicità per L'Origine delle Specie.">
    <meta name="generator" content="Joomla! - Open Source Content Management">
    <title>Pubblicità</title>
```
Nota che il campo di output delle parole chiave è assente.

*Tradotto da openai.com*

