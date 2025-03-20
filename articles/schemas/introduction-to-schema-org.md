<!-- Filename: J5.x:Schema_org / Display title: Introduzione agli Schemi -->

## Rich Snippets

I frammenti arricchiti (noti anche come *rich results*) sono risultati di ricerca Google normali con dati aggiuntivi visualizzati. Questi dati extra sono solitamente compilati dai dati strutturati trovati nell'HTML di una pagina. I tipi comuni di frammenti arricchiti includono recensioni, ricette ed eventi. I frammenti arricchiti possono aiutare i siti web a distinguersi nei risultati di ricerca, attirare più clic e fornire agli utenti una migliore comprensione del contenuto prima che vi accedano.

Joomla implementa i Rich Snippets utilizzando JSON-LD. Questa è una notazione JavaScript incorporata in un tag `<script>` nell'elemento `<head>` di una pagina HTML. Il markup non è intercalato con il testo visibile all'utente. Il contenuto degli snippet viene inserito nei campi di un modulo implementati con plugin.

## Schema.org

>Schema.org è un'attività collaborativa della comunità con la missione di creare, mantenere e promuovere schemi per i dati strutturati su Internet, sulle pagine web, nei messaggi di posta elettronica e oltre.

I dati strutturati sono un formato standardizzato per organizzare e rappresentare informazioni sul web. Forniscono un modo per descrivere il contenuto e il significato dei dati in maniera strutturata, facilitando la comprensione e l'elaborazione delle informazioni da parte dei motori di ricerca e altre applicazioni. Sono disponibili maggiori informazioni dettagliate sul [sito web di Schema.org](https://schema.org/).

## Implementazione di Joomla

In Joomla, i Rich Snippets vengono generati utilizzando il markup dei dati strutturati basato sugli schemi di Schema.org. Ogni tipo di schema è implementato come un plugin separato. Questo consente un'architettura più modulare ed estensibile. Ogni plugin è responsabile della generazione del markup dello schema per un tipo specifico di contenuto, il che consente maggiore flessibilità e opzioni di personalizzazione. Questo rende più facile per gli sviluppatori di terze parti contribuire allo sviluppo delle capacità di dati strutturati di Joomla.

Per iniziare, vai su **Sistema -> Plugin** e abilita il plugin *Sistema - Schema.org*. Se questo plugin non è abilitato, non ci sarà la scheda Schema in un modulo di modifica articolo, anche se tutti i singoli plugin sono abilitati.

![List of schema plugins](../../../en/images/schemas/schema-plugins-list.png)

### Modifica Sistema - Plugin Schema.org

- **Tipo di base** Scegli se il tuo sito web rappresenta un'organizzazione o una singola persona.
- **Nome** Inserisci il nome dell'organizzazione o della persona che il sito web rappresenta.
- **Immagine** Aggiungi l'immagine della tua azienda o personale
- **Account social media** Aggiungi gli account social media della tua azienda o personali. Seleziona il pulsante verde con il segno più per aggiungere righe al modulo.
- Seleziona **Salva e Chiudi**.

![edit system schema org plugin](../../../en/images/schemas/edit-system-schema-org-plugin.png)

### Modifica un articolo

Vai a uno qualsiasi dei tuoi articoli e compila i campi del modulo Schema. Se il *Tipo di Schema* è impostato su *Nessuno*, l'impostazione predefinita, non ci sono campi da completare. Seleziona qualsiasi Schema per vedere un elenco di campi appropriati per quello schema. Lo screenshot seguente mostra un articolo con lo schema Articolo selezionato:

![edit article scheme form](../../../en/images/schemas/schema-form-in-an-article.png)

### Output

Non vedrai nulla relativo allo schema nella pagina web. Tuttavia, se guardi il codice sorgente della pagina, vedrai un'entrata script, come nel seguente esempio:

```json
	<script type="application/ld+json">{
    "@context": "https://schema.org",
    "@graph": [
        {
            "@type": "Organization",
            "@id": "http://localhost/jcms-testing/#/schema/Organization/base",
            "name": "Joomla Documentation Team",
            "url": "http://localhost/jcms-testing/"
        },
        {
            "@type": "WebSite",
            "@id": "http://localhost/jcms-testing/#/schema/WebSite/base",
            "url": "http://localhost/jcms-testing/",
            "name": "JCMS Testing",
            "publisher": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            }
        },
        {
            "@type": "WebPage",
            "@id": "http://localhost/jcms-testing/#/schema/WebPage/base",
            "url": "http://localhost/jcms-testing/index.php/en/article-en-gb",
            "name": "Article (en-gb)",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebSite/base"
            },
            "about": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            },
            "inLanguage": "en-GB",
            "breadcrumb": {
                "@id": "http://localhost/jcms-testing/#/schema/BreadcrumbList/139"
            }
        },
        {
            "@type": "Article",
            "headline": "Article Schema Test",
            "description": "Latin text used to simulate layouts.",
            "author": {
                "@type": "person",
                "name": "Superman"
            },
            "@id": "http://localhost/jcms-testing/#/schema/com_content/article/1",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebPage/base"
            }
        }
    ]
}</script>
```

È possibile testare i dati strutturati tramite la [pagina di test dei dati strutturati](https://developers.google.com/search/docs/appearance/structured-data) di Google.

## Plugin disponibili

| Plugin | Descrizione |
|--------|-------------|
| Article Plugin | Il punto di partenza per utilizzare schema.org |
| Blogposting Plugin | Per contenuti di Post del Blog |
| Book Plugin | Per contenuti di Libri |
| Custom Plugin | Per l'inserimento diretto del codice JSON-LD |
| Event Plugin | Per contenuti di Eventi |
| JobPosting Plugin | Per contenuti di Annunci di Lavoro |
| Organization Plugin | Per contenuti di Aziende e Organizzazioni |
| Person Plugin | Per contenuti di Persone |
| Recipe Plugin | Per contenuti di Ricette |

*Tradotto da openai.com*

