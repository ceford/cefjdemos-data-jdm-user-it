<!-- Filename: J4.x:Article_Headings / Display title: Articolo: Modifica - Intestazioni -->

## Semantica dei Titoli

I titoli definiscono una struttura semantica per una pagina. Possono essere utilizzati per creare un sommario automatico e come aiuto per la navigazione per utenti con disabilità. I livelli di titolazione vanno da h1 a h6. Una singola pagina dovrebbe contenere solo un'intestazione h1, che di solito è il titolo della pagina. Un'intestazione h1 non dovrebbe essere usata in un articolo. All'interno di un articolo, i titoli devono essere annidati per creare una struttura in cui ogni livello di intestazione introduce una sezione ben definita. Esempio, dove il titolo della pagina h1 è Animali:

```
    ... testo sugli animali in generale ...
    <h2>Anfibi</h2>
    ... testo sugli anfibi in generale ...
    <h3>Rane</h3>
    ... testo sulle rane ...
    <h3>Tritoni</h3>
    ... testo sui tritoni ...
    <h2>Rettili</h2>
    ... testo sui rettili in generale ...
    <h3>Coccodrilli</h3>
    ... testo sui coccodrilli ...
    <h3>Tartarughe</h3>
    ... testo sulle tartarughe ...
```
I titoli facilitano la lettura. Grandi blocchi di testo nelle pagine web sono scoraggianti! Conservateli per i romanzi.

I titoli dovrebbero essere brevi, più corti sono meglio è. Una parola va bene. Frasi intere non costituiscono titoli adatti! I titoli non dovrebbero terminare con un punto.

I titoli semantici non dovrebbero saltare livelli, ad esempio includendo un h4 in un blocco h2 solo per ottenere un aspetto specifico.

## Inserisci un Titolo all'Articolo

Apri l'articolo che desideri modificare. Nota che il contenitore di testo predefinito è un paragrafo, indicato da una lettera `P` in una barra delle informazioni sotto l'area di testo, nella parte inferiore della finestra di modifica. Il contenitore predefinito può essere modificato nelle Opzioni dell'Editor, ma questo argomento è trattato altrove. Quando digiti un carattere di nuova linea seguito da del testo, quel testo è contenuto in un paragrafo. Per creare un titolo:

- Posiziona il cursore all'inizio di un paragrafo esistente o nella parte inferiore del testo se stai creando una nuova sezione.
- Digita il titolo seguito da una nuova linea.
- Seleziona la riga da trasformare in titolo.
- Dai pulsanti di formattazione dell'editor, dove *Paragrafo* è mostrato come selezionato:
  - Seleziona **Titoli → Titolo X** dove X è il valore appropriato per la tua gerarchia.
- Il paragrafo selezionato diventerà un titolo e apparirà in grassetto.
- Nella parte inferiore dello schermo l'indicatore del contenitore mostrerà HX.
- Puoi fare doppio clic su qualsiasi testo selezionato per apportare una modifica rapida, ad esempio da P a H2 (toggle) o da H2 a H3 utilizzando una barra popup come nello screenshot seguente:

![modulo di modifica dell'articolo con h3 selezionato](../../../en/images/articles/articles-edit-headings.png)

Nota: per convenzione, tutti i tag HTML usano lettere minuscole. Se selezioni il pulsante *Toggle Editor* per guardare il codice sorgente, vedrai i paragrafi e i titoli racchiusi in tag con lettere minuscole.

## Suggerimenti

- Fai doppio clic su qualsiasi testo selezionato per visualizzare un popup con un elenco di opzioni di formattazione. Le selezioni di *Intestazione* e *Blocco citazione* vengono applicate all'intero paragrafo. *Grassetto*, *Corsivo* e *Sottolineato* vengono applicati ai caratteri selezionati.
*Tradotto da openai.com*

