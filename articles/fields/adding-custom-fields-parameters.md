<!-- Filename: J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields / Display title: Parametri del Campo  -->
## Modulo di Inserimento Dati dei Campi

Nel modulo di inserimento dati dei campi sono disponibili 16 o più tipi di campi dalla lista di selezione Tipo. La maggior parte dei campi del modulo è uguale per tutti i tipi di campi, ma altri cambiano in base al tipo selezionato. Questo articolo descrive i parametri comuni per tutti i campi. Il modulo di inserimento dati è uguale anche per i campi di **Articolo**, **Contatto** e **Utente** e i loro campi di Categoria.

L'elenco dei campi inizialmente sarà vuoto. Per iniziare, ad esempio con i campi Articolo:
* Seleziona **Nuovo** dalla Barra degli Strumenti nell'elenco Articoli: Campi.

Il modulo si compone di un campo Titolo e quattro schede.

![Parametro dei campi scheda generale](../../../en/images/fields/fields-parameters-general-tab.png)


## Titolo

Il titolo viene visualizzato nell'elenco *Articoli: Campi* dove può essere selezionato per aprire il campo per la modifica. Il titolo non viene visualizzato quando crei un articolo o nel frontend. Tuttavia, l'Etichetta può essere creata dal Titolo e viene visualizzata nel modulo di inserimento dati dell'Articolo e può essere mostrata nella visualizzazione dell'Articolo.

### Scheda Generale

#### Nel pannello di sinistra:

- **Tipo** Seleziona uno dei 16 tipi di campi dall'elenco a discesa. Quando
salvi il campo, questo tipo diventa permanente. Non puoi cambiarlo in seguito.
- **Nome** Il nome verrà utilizzato per identificare il campo. Lascia questo campo vuoto e
Joomla inserirà un valore predefinito ricavato dal titolo.
- **Etichetta** Usa un'etichetta descrittiva per il campo. Questo testo non è
traducibile. Se non inserisci alcun testo per un'etichetta, il testo del titolo verrà
usato come testo dell'etichetta.
- **Descrizione** Testo che verrà mostrato come suggerimento per descrivere lo
scopo del campo durante l'inserimento dati. Questo testo non è traducibile e
non verrà visualizzato nel frontend.
- **Obbligatorio** Imposta su *Sì* se questo è un campo obbligatorio che deve
essere compilato prima di inviare un articolo.
- **Usa Solo in Submodulo** Richiesta spiegazione [Da fare]
- **Valore Predefinito** Imposta un valore predefinito se appropriato. Questo testo non è
traducibile.
- **Filtro** Scegli una delle opzioni disponibili dall'elenco a discesa. Il
campo verrà validato per la conformità con il tipo di dato selezionato.
- **Lunghezza Massima** Imposta questo valore per limitare la lunghezza dei dati di testo che possono essere
inseriti.

### Nel pannello di destra:

- **Stato** Imposta uno stato di pubblicazione selezionato tra *Pubblicato*, *Non Pubblicato*,
*Archiviato* o *Cestino*.
  - Pubblicato: Il campo è visibile durante la modifica di un articolo o un
    contatto. Ed è visibile nel Frontend.
  - Non Pubblicato: Il campo non sarà visibile agli utenti mentre modificano
    un articolo o un contatto.
  - Archiviato: Il campo non verrà più mostrato in edizione a un articolo o un
    contatto. Puoi aprirlo nel gestore dei campi quando imposti il
    filtro su archiviato.
  - Cestino: Il campo viene eliminato ma è ancora nel database. Può essere
    eliminato permanentemente dal database con la funzione Svuota Cestino
    nel Gestore Campi.
- **Gruppo di Campi** Seleziona Nessuno o un Gruppo scelto da un elenco predefinito. I gruppi
appaiono come schede separate nel modulo di inserimento dati dell'Articolo.
- **Categoria** Puoi assegnare un campo a una o più categorie di campi. Nota
  che il valore predefinito *Tutti* non include gli articoli *non categorizzati*.
- **Accesso** Il Livello di Accesso di visualizzazione per questo campo.
- **Lingua** Seleziona la lingua per questo campo personalizzato. Se non stai usando la
  funzione multilingue di Joomla, mantieni il valore predefinito di *Tutti*.
- **Nota** Un campo opzionale per fare note personali sul campo.

### Scheda Opzioni

![Parametri dei campi, scheda opzioni](../../../en/images/fields/fields-parameters-options-tab.png)

#### Opzioni del Modulo

- **Segnaposto** Un testo segnaposto che apparirà all'interno del campo personalizzato
come suggerimento per l'inserimento. Il segnaposto è attivo nel Backend mentre
crei un articolo. Non lo vedi nel Frontend.
- **Classe del Campo** Gli attributi di classe del campo quando il campo è reso.
Se sono necessarie classi diverse, elencale con spazi.
- **Classe Etichetta (Modulo)** Gli attributi di classe del campo nel modulo di modifica. Se
sono necessarie classi diverse, elencale con spazi.
- **Modificabile In** In quale parte del sito il campo dovrebbe essere mostrato: Sito,
Amministratore o Entrambi.
- **Attributo Showon** Mostra o nasconde condizionatamente il campo a seconda del
valore di altri campi. La sintassi da usare qui, per esempio:
  - `lista-di-elementi:valore1[OR]lista-di-elementi:valore2` dove
  - lista-di-elementi: Il nome di un campo già creato da cui questo campo
dipende.
  - valore1: Il valore necessario nel campo lista di elementi per mostrare questo campo.
  - [OR] Per creare una scelta tra più campi. Nell'esempio, questo campo verrà
mostrato quando il campo lista-di-elementi ha un valore di valore1 OR valore2.
  - [AND] Per combinare più campi. Questo campo verrà mostrato solo quando i
campi lista-di-elementi hanno il valore valore1 E valore2.
  - Puoi anche usare il valore 'non è uguale a' come in lista-di-elementi!:valore1. La
sintassi mostrerà questo campo solo quando lista-di-elementi non è uguale a valore1
  - Per mostrare questo campo quando il campo lista-di-elementi è stato selezionato e non ha
un valore vuoto, usa la sintassi lista-di-elementi!: (senza un valore specificato).
  - Nota: I campi submodulo gestiscono il nome lista-di-elementi in modo diverso.
Se crei un campo Submodulo e aggiungi questo campo condizionale per un campo
che stai creando lì, devi usare field[ID] invece di lista-di-elementi,
dove ID è l'id del campo lista-di-elementi. Pertanto, l'attributo showon
per questo campo condizionale che stai creando deve essere:
field36:valore1[OR]field36:valore2 dove 36 è l'ID del campo 'Lista di elementi'.
Questa spiegazione necessita di chiarimenti!

#### Opzioni di Visualizzazione

- **Classe di Visualizzazione**  La classe del contenitore del campo nell'output.
- **Classe del Valore**  La classe del valore del campo nell'output.
- **Etichetta** Mostra o Nascondi l'etichetta.
- **Classe Etichetta (Output)** La classe dell'etichetta nell'output se l'etichetta è visualizzata.
- **Visualizzazione Automatica** Joomla offre alcuni eventi di contentuto che vengono attivati
durante il processo di creazione del contenuto. Questo è il luogo in cui definire come i campi personalizzati
dovrebbero essere integrati nel contenuto. Puoi scegliere *Dopo il Titolo*,
*Prima del Contenuto Display*, *Dopo il Contenuto Display* o *Non visualizzare automaticamentente*.
- **Prefisso** Testo fisso da visualizzare prima di un campo, ad esempio £.
- **Suffisso** Testo fisso da visualizzare dopo un campo, ad esempio EUR.
- **Layout** Seleziona un layout tra i modelli disponibili e le esecuzioni alternative.
- **Visualizza Quando Sola Lettura** Seleziona tra *Ereditare*, *Sì* o *No*. Se il campo è
solo lettura (forse l'utente non ha il livello di accesso) il campo
dovrebbe essere visualizzato o nascosto.

#### Ricerca Intelligente

- **Indice di Ricerca** Seleziona dall'elenco delle opzioni. Avvertenza: Quando *Rendere ricercabile*
è selezionato, il contenuto del campo viene indicizzato con le autorizzazioni
di visualizzazione dell'elemento di contenuto. Questo potrebbe portare alla divulgazione di informazioni inaspettate.

### Scheda Pubblicazione

![Parametri dei campi, scheda pubblicazione](../../../en/images/fields/fields-parameters-publishing-tab.png)

### Scheda Permessi

Le autorizzazioni per ciascun gruppo di utenti sono autoesplicative per le azioni *Elimina*, *Modifica* e *Modifica stato*. Le autorizzazioni indicano chi può fare cosa con l'intero campo, ad esempio eliminarlo, modificarlo o annullarne la pubblicazione.

![Parametri dei campi, scheda permessi](../../../en/images/fields/fields-parameters-permissions-tab.png)

L'autorizzazione *Modifica valore campo personalizzato* può creare confusione. Indica chi può modificare il contenuto del campo. Per impostazione predefinita, è configurata su **Non consentito (Ereditato)** per tutti i gruppi, tranne che per i Super User. Due esempi:

* **Dati personalizzati di registrazione utente**
  Supponiamo di creare un campo utente per il *Genere* da aggiungere a un modulo di registrazione. Potrebbe trattarsi di un elenco o di un pulsante di opzione che consente all'utente di selezionare *Maschio* o *Femmina*. In questo caso, l'autorizzazione per il gruppo Pubblico deve essere impostata su *Consentito*. Altrimenti, un utente ospite non potrà selezionare un genere. Poiché tutti gli altri gruppi ereditano dal gruppo Pubblico, un utente registrato potrà modificare la scelta del genere nel proprio profilo dopo l'accesso.
* **Commento all’articolo**
  Supponiamo di voler consentire a un Autore di aggiungere un commento a un articolo. Potrebbe essere un campo di testo a lunghezza limitata. In questo caso, l'autorizzazione per il gruppo Autore deve essere impostata su *Consentito*. I gruppi Editore e Publisher erediteranno questa impostazione al salvataggio del modulo. I gruppi Manager e Amministratore hanno il permesso di modificare gli articoli, ma non i valori dei campi personalizzati, a meno che l'autorizzazione per il gruppo Manager non sia anch’essa impostata su *Consentito*.
