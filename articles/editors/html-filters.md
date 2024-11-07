<!-- Filename: Entering_raw_HTML_in_editors / Display title: Filtri HTML  -->

## Tag HTML Textarea

In HTML, un campo di input a più linee è noto come textarea. Qualsiasi testo tra i tag di apertura e chiusura viene visualizzato come testo che può contenere markup HTML. Esempio:
```
<textarea><p class="poem">La veloce volpe marrone<br>
salta sopra il cane pigro.</textarea>
```
Editor, come TinyMCE o Code Mirror, usano JavaScript per sovrapporre la textarea con una visualizzazione diversa per consentire l'inserimento dati WYSIWYG e/o l'evidenziazione della sintassi. Il pulsante di attivazione sotto un campo dell'editor alterna tra la visualizzazione della textarea e la visualizzazione WYSIWYG.

Le visualizzazioni dell'editor sono utilizzate per il contenuto degli Articoli e alcuni Moduli. Tuttavia, è necessario essere consapevoli che non tutti i tag e gli attributi HTML (come class="xyz") sono consentiti a tutti gli utenti. Alcuni o tutti potrebbero scomparire quando salvi il contenuto di una textarea o di un campo di modifica.

Questo è causato da meccanismi di filtraggio, sia nella Configurazione Globale di Joomla! che nella configurazione dell'editor. Un filtro dell'editor può essere bypassato selezionando *Nessun Editor* nelle impostazioni del tuo *Profilo Utente*. Non è possibile bypassare i filtri globali, ma è possibile modificarli per adattarli agli scopi del tuo sito.

## Selezione dell'Editor Utente

Puoi selezionare uno degli editor disponibili, incluso Nessuno, dal tuo Profilo Utente accessibile tramite il menu Account Utente / Modifica Profilo in alto a destra nella schermata dell'Amministratore. Il modulo di Modifica: Profilo contiene una scheda Impostazioni di Base con un campo per selezionare un Editor. Di solito è impostato su *- Usa Predefinito -*, che solitamente è TinyMCE. Puoi selezionare *Editor Nessuno*. In questo modo si eviterà qualsiasi filtraggio dei tag HTML e degli attributi non consentiti dalle impostazioni di configurazione di TinyMCE.

**Avviso:** se selezioni *Editor - Nessuno* per creare contenuti contenenti tag HTML non consentiti da un filtro editor e poi torni al editor predefinito, dovresti fare attenzione a non modificare e salvare nuovamente quei contenuti o perderai qualsiasi tag e attributo filtrato. È facile farlo per errore e non c'è nessun avviso.

## Configurazione Globale: Filtri di Testo

Dalla Dashboard Principale, seleziona Configurazione Globale e poi la scheda Filtri di Testo. Le impostazioni predefinite hanno *Nessun HTML* selezionato per i gruppi di utenti Ospite, Pubblico e Registrato. Qualsiasi di questi gruppi potrebbe avere l'opportunità di compilare un campo di area testo, ad esempio in un modulo di contatto che richiede informazioni aggiuntive su un problema, quindi la rimozione automatica di tutti i tag HTML è solitamente appropriata. Altri gruppi, ad eccezione dei Super Utenti, sono limitati dall'Elenco Predefinito delle Restrizioni. I Super Utenti non hanno filtri.

![configurazione globale dei filtri di testo](../../../en/images/configuration/global-configuration-filters-tab.png)

Le note spiegano cosa è incluso nell'elenco predefinito delle restrizioni e come utilizzare gli altri elenchi.  

## Configurazione di TinyMCE per Filtri di Testo

Gli editor sono implementati come Plugin in Joomla. L'editor CodeMirror non ha impostazioni per i filtri di testo. Per personalizzare l'editor TinyMCE trovalo e selezionalo nell'elenco dei plugin. A metà dell'elenco di impostazioni troverai un campo etichettato *Usa Filtro di Testo di Joomla* che è **Disattivo** di default. I tre campi successivi sono:
* **Elementi Proibiti** un elenco di tag che saranno sempre rimossi. L'elenco predefinito di *script,applet,iframe* ha tutte preoccupazioni di sicurezza.
* **Elementi Valid** utilizza questo elenco per limitare i tag validi a un sottoinsieme di tutti i tag HTML comuni. Esempio: `a[href|target=_blank],strong/b,div[align],br`
* **Elementi Validi Estesi** utilizza questo elenco per aggiungere un elemento al set di regole esistente o per modificare un elemento nel set di regole predefinito. Esempio: `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

Consulta la Documentazione di TinyMCE per maggiori spiegazioni.

Per bypassare i filtri di testo di TinyMCE e utilizzare i filtri di testo di Joomla, imposta *Usa Filtro di Testo di Joomla* su **Attivo**. I tre campi aggiuntivi descritti sopra scompaiono poiché non vengono utilizzati.

*Tradotto da openai.com*

