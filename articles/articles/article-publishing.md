<!-- Filename: J6.x:_Article_Publishing / Display title: Articolo: Modifica - Pubblicazione -->

## Introduzione

Una parte fondamentale di un Sistema di Gestione dei Contenuti (CMS) è la sua capacità di fornire contenuti a utenti selezionati per periodi specifici. Joomla! lo fa con i livelli di accesso e le date di inizio e fine pubblicazione.

Le date di inizio e fine possono essere impostate sia per articoli *In primo piano* che per articoli *Non in primo piano*. Ad esempio, un nuovo articolo potrebbe essere in primo piano per un periodo determinato, diciamo 30 giorni, dopo il quale diventerebbe un normale articolo non in primo piano. Scomparirebbe dai layout di articoli in primo piano ma continuerebbe ad apparire in altri layout di blog o di articoli singoli.

Per lo più, gli articoli vengono pubblicati nel giorno in cui sono creati e rimangono tali fino a quando non vengono ritirati, archiviati o eliminati.

## Screenshot

![La scheda di pubblicazione del modulo di modifica dell'articolo](../../../en/images/articles/articles-edit-publishing-tab.png)

Il pannello *Metadata* è spiegato in un articolo separato. Questo articolo tratta del pannello *Publishing*.  

## Pannello di pubblicazione

Alcuni campi del modulo sono destinati a informazioni e non possono essere modificati direttamente nel modulo. Sono visualizzati con sfondi grigi. Altri campi possono essere modificati se necessario.

### Inizio Pubblicazione

Questo campo è impostato sulla data e ora attuali quando l'articolo viene salvato per la prima volta. Se vuoi che l'articolo sia sotto embargo fino a una data e ora future, puoi impostare il suo valore usando lo strumento Calendario o modificando direttamente i valori del campo.

### Fine Pubblicazione

Per impostazione predefinita, questo campo è vuoto. Se desideri che l'articolo scompaia dopo una data e ora specificate, usa lo strumento Calendario o inserisci direttamente una data e un'ora future nel campo. A quel punto l'articolo scomparirà dal sito. Nell'elenco degli articoli sarà contrassegnato come *Pubblicato, ma scaduto*.

### Inizio Evidenziato

Se l'articolo è contrassegnato come *Articolo in evidenza*, questo campo può essere impostato in modo che appaia in un layout di *Articoli in evidenza* alla data specificata. Nota che la data non verrà salvata se l'articolo non è contrassegnato come *Articolo in evidenza*.

### Fine Evidenziato

Se l'articolo è contrassegnato come Articolo in evidenza, questo campo può essere impostato in modo che scompaia da un layout di *Articoli in evidenza* alla data specificata. L'articolo rimane pubblicato e può comunque apparire in altri layout. Nell'elenco degli articoli sarà contrassegnato come *In evidenza, ma scaduto*.

### Data di Creazione

Questa data viene impostata quando l'articolo viene salvato per la prima volta. Potresti volerla cambiare se hai creato una serie di articoli in ordine casuale e desideri ordinarli in ordine di data di creazione.

### Creato Da

L'ID utente del creatore viene salvato al momento della creazione e il Nome di quell'utente appare in questo campo. Puoi cambiare il Creatore selezionando l'icona della persona per rivelare un popup di dialogo *Seleziona Utente* da cui puoi trovare e selezionare un utente diverso.

### Creato da Alias

Se non desideri che il nome utente del creatore appaia nel blocco di informazioni dell'articolo, puoi inserire un Alias qui. Inserisci il tuo alias, salva l'articolo e dai un'occhiata con il pulsante Anteprima nella Barra degli Strumenti.

## Pianificazione della Pubblicazione di un Articolo

Per impostazione predefinita, gli articoli sono configurati come **Pubblicati** non appena vengono salvati. Il salvataggio iniziale dell'articolo crea le date di **Data Creazione** e **Inizio Pubblicazione**.

Pianificare un articolo comporta la modifica manuale della data e dell'ora di **Inizio Pubblicazione** per ritardare la pubblicazione. È possibile impostare anche le date e le ore per **Fine Pubblicazione**.

**Nota:** Per far funzionare la pianificazione, lo **Stato** dell'articolo deve essere impostato su **Pubblicato**.

Prima della data di Inizio Pubblicazione, gli articoli sono considerati **In Attesa** e dopo la data di Fine Pubblicazione sono considerati **Scaduti**. Nonostante l'articolo stesso sia impostato su pubblicato, Joomla utilizza le impostazioni di inizio e fine per sovrascrivere lo stato predefinito di pubblicazione.

I valori di data e ora possono essere inseriti manualmente nei campi di data oppure selezionati con lo strumento Calendario, che si apre selezionando l'icona del calendario alla fine di ciascun campo di data.

![Date di pubblicazione](../../../en/images/articles-access/article-schedule-publishing.png)

Il calendario si sposta tra giorni, mesi e anni utilizzando i tasti freccia avanti, indietro, su e giù della tastiera. Il pulsante **Oggi** imposta la data corrente. Il pulsante **Pulisci** cancella la data e l'ora.

* Seleziona la data necessaria.
* Imposta l'ora utilizzando i menu a tendina.
* Seleziona il pulsante **Chiudi Calendario** per impostare la data e l'ora selezionate.
* Seleziona **Salva** o **Salva e Chiudi** dalla barra degli strumenti per salvare le modifiche.

## Icone della Vista Elenco

Nell'elenco degli Articoli, l'icona *In Evidenza* è solitamente un cerchio grigio o una stella gialla. Allo stesso modo, l'icona *Stato* è solitamente una spunta verde o una croce grigia. Ognuna ha un Tooltip e l'azione usuale è quella di alternare lo stato.

- Pubblicato ed è Corrente: <span class="icon-publish" aria-hidden="true"></span>
- Non Pubblicato: <span class="icon-unpublish" aria-hidden="true"></span>
- In Evidenza: <span class="icon-featured" aria-hidden="true"></span>
- Non in Evidenza: <span class="icon-unfeatured" aria-hidden="true"></span>

Le icone per gli articoli con date di inizio e fine programmate sono diverse.

- Pubblicato ma in Attesa: <span class="icon-pending" aria-hidden="true"></span>
- Pubblicato ma Scaduto: <span class="icon-expired" aria-hidden="true"></span>
- In Evidenza ma in Attesa: <span class="icon-pending" aria-hidden="true"></span>
- In Evidenza ma Scaduto: <span class="icon-expired" aria-hidden="true"></span>

In ogni caso, un Tooltip mostra informazioni aggiuntive sulle date programmate.

## Suggerimenti

- Puoi programmare la pubblicazione degli articoli anche dal front end.
- È possibile programmare anche tramite l'elemento del menu per l'articolo.
- La pianificazione è disponibile anche per Contatti e Moduli.

*Tradotto da openai.com*

