<!-- Filename: J4.x:Article_Tables / Display title: Articolo: Modifica - Tabelle  -->

## A proposito delle tabelle

In HTML, le tabelle sono costituite da righe e colonne di celle. Ad esempio, una tabella semplice può essere composta da 4 righe e 4 colonne, per un totale di 16 celle. Tuttavia, le celle possono essere combinate sia orizzontalmente che verticalmente per creare strutture di tabelle piuttosto complesse. Le tabelle hanno anche caratteristiche meno ovvie, come un'intestazione, un corpo, un piè di pagina e didascalie. Le tabelle possono essere annidate!

Per impostazione predefinita, le celle delle tabelle si espandono per ospitare il loro contenuto. L'unico stile deriva dal markup della tabella: per impostazione predefinita, le celle di intestazione (`<th>`) hanno testo in grassetto, centrato, mentre le celle di dati (`<td>`) hanno testo normale, allineato a sinistra.

L'uso delle tabelle dovrebbe essere riservato a dati strettamente tabulari, come un orario o un calendario, dove è importante mantenere la struttura di righe e colonne. Le tabelle non dovrebbero essere utilizzate per layout, come il posizionamento di immagini o testo uno accanto all'altro.

Ci sono ulteriori informazioni nei seguenti articoli:

- [Fondamenti delle tabelle](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Funzionalità avanzate e accessibilità](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Stilizzazione delle tabelle](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Le tabelle sono un dilemma! Se inserisci una tabella utilizzando gli strumenti per tabelle di TinyMCE, la tabella avrà un aspetto gradevole nella schermata di modifica e nel sito, ma il layout viene ottenuto con stili CSS in linea, che possono essere voluminosi e difficili da modificare. Se la tabella è inserita come puro HTML, il risultato non appare bene nell'editor di testo TinyMCE, ma può sfruttare le classi di Bootstrap e avere un aspetto migliore sul sito. Entrambi i metodi sono trattati di seguito.

## Inserire una Tabella con gli Strumenti di TinyMCE

Per iniziare con una tabella:

- Apri l'articolo che desideri modificare.
- Posiziona il cursore su una riga vuota dove vuoi che appaia la tabella.
- Seleziona il pulsante *Table* nella prima riga degli strumenti di TinyMCE.
- Nel menu a tendina seleziona Tabella e quindi sposta il cursore per definire 
  il numero di righe e colonne. Anche le frecce della tastiera funzionano per questo.
- Seleziona l'ultima cella nella matrice 4x4.
- Riempire le celle della tabella.

Opzioni di modifica:

- Puoi inserire una riga sopra o sotto una cella selezionata.
- Puoi inserire una colonna prima o dopo una cella selezionata.
- Puoi eliminare una riga o una colonna.
- Puoi trascinare i bordi delle colonne per cambiare le larghezze o le altezze delle colonne.
- Puoi unire celle - trascina sulle celle per selezionarle e poi
  usa Tabella -> Celle -> Unisci celle.
- Puoi selezionare le Proprietà della Tabella, inclusi larghezza, stile e colore del bordo e
  colore di sfondo.

Se utilizzi il pulsante Toggle Editor vedrai che il layout viene realizzato con
dichiarazioni di stile inline su ogni riga e ogni cella. Ecco un breve esempio:

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">Giorno</td>
<td style="height: 24px;">Mattina</td>
<td style="height: 24px;">Pomeriggio</td>
<td style="height: 24px;">Sera</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Martedì</td>
<td style="height: 24px;">Benvenuto</td>
<td style="height: 24px;">Presentazioni</td>
<td style="height: 24px;">Barbecue</td>
</tr>
...
</tbody>
</table>
```

## Inserire una Tabella come HTML

Se preferisci, puoi evitare di usare stili inline e utilizzare le classi di Bootstrap. Dovresti modificare la tabella creata dagli strumenti di Tabelle di TinyMCE o scriverla tu stesso. Apparirebbe così:

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>Giorno</th>
<th>Mattina</th>
<th>Pomeriggio</th>
<th>Sera</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Martedì</th>
<td>Benvenuto</td>
<td>Presentazioni</td>
<td>BBQ</td>
</tr>
...
</tbody>
</table>
</div>
```

Qui, le classi di Bootstrap hanno i seguenti effetti:

- `table` - applica diversi stili per dare una bella disposizione standard alla tabella.
- `table-striped` - le righe alternate sono scure e chiare.
- `table-bordered` - applica bordi alle celle.
- `table-group-divider` - applica una linea in grassetto sopra un elemento.
- `table-responsive` - consente a una tabella ampia di essere scorsa da destra a sinistra.

Il seguente screenshot del sito mostra una tabella per un programma di conferenze con gli stili inline predefiniti di TinyMCE e una tabella simile con gli stili di Bootstrap:

![Tabelle di esempio](../../../en/images/articles/articles-site-tables.png)

Consulta la documentazione di Bootstrap su [Tabelle](https://getbootstrap.com/docs/5.3/content/tables/) per maggiori opzioni.

## Ripensamento

Potresti inserire l'HTML per una tabella in un modulo personalizzato e includere quel modulo nell'articolo. Nell'articolo apparirà come `{loadmoduleid xx}` dove xx è l'Id del modulo.

*Tradotto da openai.com*

