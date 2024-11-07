<!-- Filename: contacts.md / Display title: Contatti -->

## Introduzione

Un contatto è una raccolta di informazioni personali su un individuo. Potresti desiderare rendere tali informazioni disponibili sul tuo sito web per una visualizzazione pubblica o privata. Ad esempio, potresti voler elencare membri chiave della tua organizzazione o comunità. Il componente Contatti di Joomla! è progettato per questo scopo. Ti consente di elencare persone e le loro informazioni personali sul tuo sito web, non necessariamente utenti registrati. Puoi anche permettere a chiunque, o solo agli utenti registrati, di inviare e-mail a queste persone.

Come esempio dell'uso dei dati personali, potresti guardare la pagina di WikiPedia sui comitati parlamentari del Regno Unito. Lì vedrai elenchi di comitati con informazioni popup sui presidenti individuali. Se segui un link a qualsiasi comitato, vedrai un elenco di membri con informazioni selezionate su ciascun individuo. Per fare qualcosa di simile in Joomla, dovresti configurare categorie e sottocategorie per ciascun comitato. Come questo:

```
Camera dei Comuni
- Affari
- Cultura
- ...
Camera dei Lord
- Comunicazioni
- Costituzione
- ...
```
Ogni membro del comitato ha informazioni aggiuntive non presenti nei dati predefiniti - affiliazione politica, come Conservatori, Laburisti o SNP, e collegio elettorale, l'area del paese che rappresentano. Questi elementi possono essere raccolti usando i Campi Personalizzati.

È necessaria cura nella raccolta e visualizzazione delle informazioni personali. Gli individui possono essere molto sensibili alla disponibilità di qualsiasi informazione online.

## Dati di Contatto

I contatti vengono creati tramite la pagina dell'elenco dei contatti. Seleziona il pulsante `Nuovo` nella barra degli strumenti per aggiungere una nuova voce. C'è anche un plugin **Utente - Creatore di Contatti** che crea automaticamente un contatto quando viene registrato un nuovo utente.

Nel modulo **Contatti: Modifica**, inserisci i dati disponibili sul contatto.

![screenshot inserimento dati](../../../en/images/contacts/contact-data-entry.png "Screenshot inserimento dati")

**Note:**

Nello screenshot, la **Posizione** è stata inserita come *Presidente*, il che aveva senso nel contesto di un elenco di membri del comitato, ma non ha senso nel contesto di un elenco di contatti in primo piano che comprende tutti i Presidenti di tutti i Comitati. Questo deve essere più specifico: *Presidente del Comitato Cultura, Media e Sport*.

I campi **Primo...**, **Secondo...** e **Terzo Campo di Ordinamento** richiedono l'aggiunta di parole per ogni voce per abilitare l'ordinamento secondo un ordine definito dall'utente, come un convenzionale ordine cognome, nome. Questo è trattato più avanti in questo articolo.

La scheda **Informazioni Varie** contiene un campo di modifica del testo con una breve dichiarazione personale.

La scheda **Extra** contiene i campi personalizzati *Partito* e *Collegio Elettorale*.

La scheda **Modulo** contiene le impostazioni per il modulo di contatto via email. Se non viene inserito un indirizzo email, questo campo non viene visualizzato.

## Visualizzazione Contatti

Il componente Contatto fornisce quattro elementi di menu per visualizzare i dati di contatto:

* Contatto Singolo
* Contatti In Primo Piano
* Elenco Contatti in una Categoria
* Elenco Tutti i Contatti in un Albero di Categoria

È una buona idea provare ogni tipo di menu per vedere come appare il risultato.
Alcuni esempi:

### Elenco di Tutte le Categorie in un Albero di Categoria di Contatti

In questo caso, l'albero di categoria consiste in una categoria principale e due sotto-categorie:
```
Camera dei Comuni
- Commissione Affari
- Commissione Cultura
```
![tutte le categorie in un albero di categoria](../../../en/images/contacts/contact-all-committees.png "Tutte le Categorie in un Albero di Categoria di Contatti")

La seconda riga di ciascuna voce proviene dalla Descrizione della Categoria.

Se selezioni uno dei link della Commissione, la pagina della Commissione potrebbe apparire in questo modo:

![contatti in una categoria](../../../en/images/contacts/contact-culture-committee.png "Contatti in una Categoria")

Il layout non è proprio come desiderato. Sarebbe stato utile includere
un'anteprima di ciascun individuo e un layout migliore dei dettagli. Questo
può essere fatto con una sovrascrittura del template (in seguito).

### Elenco Contatti in una Categoria

Per la Commissione Affari c'è un elemento di menu Elenco Contatti in una Categoria.
Ciò causa l'uso di un layout diverso:

![elenco di categoria contatti](../../../en/images/contacts/contact-category-list.png "Elenco di Categoria Contatti")

Meglio ma ancora non del tutto corretto! È stata necessaria una sovrascrittura 
di stile per ridurre lo stile dell'immagine. Ancora una volta sembra che una sovrascrittura del template potrebbe essere utile.

### Contatti In Primo Piano

Per questo esempio, i Presidenti di tutte le commissioni sono stati contrassegnati come in primo piano.

![contatti in primo piano](../../../en/images/contacts/contact-featured.png "Contatti In Primo Piano")

## Ordine di Classificazione

L'ordine in cui compaiono i contatti può essere impostato nelle opzioni del componente Contatto o in un elemento di menu. Quest'ultimo prevale sul primo se impostato. Le impostazioni disponibili sono le seguenti:
* **Nome** Il nome del contatto. Questo potrebbe non essere adatto per l'ordinamento alfabetico.
* **Nome di Ordinamento** Questi sono i tre campi *Campo di Ordinamento* nel modulo dati del Contatto menzionati in precedenza.
* **Ordinamento** Questo è l'ordine in cui i contatti appaiono nell'elenco Contatti.
* **Ordinamento dei Contatti in Evidenza** I contatti in evidenza appaiono prima degli altri contatti ma altrimenti i contatti vengono visualizzati in ordine di elenco.

