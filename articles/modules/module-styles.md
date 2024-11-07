<!-- Filename: jdocmanual?manual=user&heading=modules&filename=module-styles.md / Display title: Stili dei Moduli -->

## Concetti di Stile

Un modulo di inserimento dati ha una scheda **Avanzate**. I suoi campi variano in base al tipo di modulo, e puoi verificarlo di persona selezionando un modulo Menu e confrontandolo con un modulo Login o un modulo Breadcrumbs. Vedrai i seguenti tre campi del modulo relativi allo stile:

* **Classe Modulo** è un campo di testo che ti consente di aggiungere la tua classe CSS al tag del contenitore del modulo, di solito un `<div>`.
* **Classe Intestazione** è un campo di testo che ti consente di aggiungere la tua classe CSS al tag Intestazione, di default un tag `<h3>`.
* **Stile Modulo** è un elenco che ti consente di selezionare uno tra diversi stili standard. L'elenco contiene nessuno, html5, outline, table, card e noCard. Il predefinito è card dagli stili del template Cassiopeia.

Puoi provare le opzioni *Stile Modulo* modificando un modulo e cambiando il valore per vedere cosa fa alla visualizzazione del sito.

* **html5** restituisce `<div class="moduletable ">`
* **nessuno** rimuove completamente il `<div>` esterno e anche il tag `<h3>` del modulo.
* **outline** restituisce `<div class="mod_preview_info">`, con informazioni di posizione e stile che sostituiscono il tag `<h3>` del modulo.
* **table** fornisce un layout di tabella a partire da `<table class="moduletable ">` con l'ex tag h3 ora un tag `<th>`.
* **card** restituisce `<div class="sidebar-right card ">`, il predefinito.
* **noCard** restituisce `<div class="sidebar-right no-card ">`

## La Classe del Modulo

A questo punto, è necessario avere qualche conoscenza dei Fogli di Stile a Cascata o CSS. Se inserisci una singola parola nel campo Classe Modulo, ad esempio **green** poiché per convenzione le classi CSS sono tutte in minuscolo, e con lo Stile del Modulo impostato su **ereditato**, l'output contiene `<div class="sidebar-right card green">`.

Non c'è alcun cambiamento visibile nell'aspetto del sito perché la classe green non è definita. Per definirla, fai un'entrata nel file user.css del template.

Dal menu Amministratore:
* Seleziona **Sistema / Modelli del Sito / Modelli Cassiopeia e File**.
* Seleziona **Nuovo File** dalla *Barra degli strumenti*.
* Seleziona **css** nella colonna di sinistra, la destinazione per il nuovo file.
* Digita **user** nel campo Nome del File.
* Seleziona **css** dalla lista Tipo di File.
* Seleziona il pulsante **Crea**.

Ora puoi aprire la cartella css per trovare e aprire il file user.css per la modifica. Inserisci queste dichiarazioni di stile e nota la grafia americana di *color*:
```
.sidebar-right.card.green {
    background-color: #ddffdd;
}
.sidebar-right.card.green .card-body {
    background-color: #eeffee;
}
```
Lo stile avrebbe potuto utilizzare solo `.green`, ma ciò potrebbe aver influenzato altri tag con quello stile su altre pagine.

## La Classe Header

Torna al modulo di modifica e aggiungi **blu** nel campo della Classe Header. Il modulo non presenta alcuna modifica visibile sul sito, ma l'intestazione ora appare come `<h3 class="card-header blue">`. Torna a modificare il file user.css per aggiungere un'entrata per lo stile dell'intestazione:

```
.card-header.blue {
    color: navy;
}
```

Ora l'intestazione del modulo è in blu scuro. Ci sono diversi modi per specificare il colore in CSS. I più comuni sono il codice esadecimale e i nomi standard dei colori. Scopri tutto di più altrove!

## Sfida CSS

* Cambia il colore del bordo del modulo in blu navy!
* Cambia anche il bordo inferiore dell'intestazione.
* Applica questo stile a diversi moduli invece che uno alla volta.

![Esempio di Modulo Articoli Archiviati](../../../en/images/modules/modules-archived-articles.png)

*Tradotto da openai.com*

