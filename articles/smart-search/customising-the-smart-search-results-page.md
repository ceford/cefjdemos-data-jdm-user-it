<!-- Filename: Customising_the_Smart_Search_results_page / Display title: Override Layout di Ricerca Intelligente  -->

## Pagine dei Risultati

Il componente Smart Search ha cinque file di layout che puoi sovrascrivere per creare un layout a tuo piacimento. Per avviare il processo dal menu dell'Amministratore:

* Seleziona **Sistema / Template del sito / Dettagli e File di Cassiopeia**.
* Seleziona la scheda **Crea Override**.
* Dal pannello Componenti seleziona **com_finder**.
* Seleziona l'elemento **Search**.
* Dal pannello dell'Editor seleziona **html / com_finder / search** per vedere l'elenco dei file di override creati.

Questi file non saranno influenzati dagli aggiornamenti di Joomla, ma potresti ricevere un promemoria per controllarli se le fonti originali vengono aggiornate.

## La Vista di Ricerca (Layout Predefinito)

La vista di ricerca con layout predefinito è divisa in diverse parti: il layout predefinito, il layout del modulo, il layout dei risultati e il layout di ordinamento.

### Il layout predefinito (default.php)

Questo layout è molto semplice. Definisce semplicemente la struttura in cui il modulo di ricerca e i risultati della ricerca vengono visualizzati. Questo layout è anche responsabile del caricamento del foglio di stile CSS predefinito per Smart Search che si trova in `media/com_finder/css/finder.css`, quindi potresti voler modificare ciò per caricare le tue regole CSS per Smart Search.

### Il layout del modulo (default_form.php)

Questo layout definisce il codice necessario affinché il modulo di ricerca funzioni correttamente. Il layout utilizza codice JavaScript, quindi è necessario prestare attenzione a preservare i selettori che non dovrebbero essere modificati a meno che tu non sappia cosa stai facendo.

Il metodo della vista `getFields` include un numero di campi nascosti che sono necessari per una ricerca affidabile. Il termine di ricerca è definito dal campo di input con il nome "q".

### Il layout dei risultati (default_results.php)

Questo layout produce l'elenco dei risultati che corrispondono al termine di ricerca. Gestisce anche la paginazione e carica un layout per ciascun risultato di ricerca individuale.

### Il layout del risultato (default_result.php)

Questo è il layout caricato per visualizzare un singolo risultato.

### Il layout di ordinamento (default_sorting.php)

Questo elemento è presente solo se Mostra Campi di Ordinamento è impostato su Sì e uno o più Campi di Ordinamento Aggiuntivi sono selezionati nella scheda Avanzate dell'Elemento di Menu.

*Tradotto da openai.com*

