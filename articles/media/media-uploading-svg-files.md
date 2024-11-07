<!-- Filename: J4.x:Media:_Uploading_SVG_files / Display title: Caricamento di file SVG  -->

## Introduzione

I file SVG (Scalable Vector Graphics) non sono supportati in Joomla per impostazione predefinita. Sono necessari alcuni passaggi per consentire al componente Media di supportarli.

## Opzioni Multimediali

Dal menu dell'Amministratore:

* Seleziona **Media** dalla *Dashboard Principale* o dal menu *Contenuti*.
* Seleziona il pulsante **Opzioni** dalla *Toolbar* dei Media.

Ci sono 3 campi da aggiornare, tutti elenchi separati da virgole, quindi devi solo appendere una virgola e il valore appropriato:

- In *Estensioni Consentite*, aggiungi alla fine dell'elenco già disponibile: `,svg`.
- In *Estensioni Immagine Consentite*, aggiungi alla fine dell'elenco già disponibile: `,svg`.
- In *Tipi MIME Consentiti*, aggiungi alla fine dell'elenco già disponibile: `,image/svg+xml`.
- **Salva & Chiudi**

D'ora in poi, dovresti essere in grado di caricare file SVG nel Media Manager. A meno che...

## Joomla impedisce ancora il caricamento dei file SVG?

SVG non è un formato di immagine raster (come i file PNG, che contengono pixel), ma è scritto in XML (Extensible Markup Language). È basato su testo, utilizzabile direttamente all'interno del DOM (Document Object Model), e il CSS può cambiare le proprietà mentre JavaScript può aggiungere interattività.

Pertanto, i file SVG sono suscettibili a tutti i modelli di attacco legati all'XML:

- Cross-site scripting – o XSS (tramite il tag `<script>` e gli eventi).
- Iniezioni HTML (tramite l'elemento `<foreignObject>` – foreignObject consente di includere elementi da un diverso namespace XML).
- Denial of service (se l'elemento `<xlink:href>` viene utilizzato in modo improprio).

A partire da Joomla 4.1, uno strumento di sanificazione viene utilizzato per controllare il contenuto di qualsiasi file SVG caricato tramite il Media Manager. Le regole sono rigide e assicurano che i file non possano danneggiare il sito. Pertanto, alcuni file potrebbero dover essere **puliti** manualmente (ricorda, i file SVG sono file di testo e possono essere modificati in un editor di testo) o tramite uno strumento esterno prima che possano essere caricati con successo.

**Suggerimento:** questi siti puliscono i file SVG creati in *Inkscape*:

* [SVG Sanitizer Test](https://svg.enshrined.co.uk/)
* [SVG Cleaner & Optimizer](https://iconly.io/tools/svg-cleaner)
* [SVGminify.com](https://www.svgminify.com/)

