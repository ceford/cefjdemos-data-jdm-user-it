<!-- Filename: J4.x:Article_Lists / Display title: Articolo: Modifica - Elenchi  -->

## Tipi di Elenchi

HTML ha tre tipi di elenchi:

- Gli elenchi non ordinati sono spesso stilizzati con un rientro e un punto,
  come questo elenco.
- Gli elenchi ordinati sono simili ma contrassegnati con numeri.
- Gli elenchi di definizione consistono in Titoli e Definizioni.

I punti elenco e i numeri vengono applicati dal browser da una
selezione di stili. L'utente non deve inserire alcun testo di punti o numeri
poiché verrà trattato come parte dell'elenco. L'editor TinyMCE ha
icone per applicare stili di punti comuni e tipi di numeri. Gli elenchi di
definizione sono più complicati e devono essere realizzati a mano.

Gli elenchi possono contenere altri elenchi a qualsiasi livello, sebbene gli elenchi profondamente
rientrati diventino difficili da leggere, quindi è meglio limitarsi a uno o due livelli.

## Screenshot

Lo screenshot seguente mostra un elenco non ordinato con due livelli di indentazione. Mostra anche l'intero set di strumenti, aperto selezionando il pulsante con i tre puntini (...) alla fine della prima riga di icone degli strumenti.

![Elenchi nidificati non ordinati](../../../en/images/articles/articles-edit-lists.png)

Questo screenshot verrà utilizzato per spiegare come è stato creato l'elenco puntato utilizzando gli strumenti *Elenco puntato* e *Aumenta indentazione* o *Riduci indentazione*:

## Stili di elenco

### Elenchi puntati

Sono disponibili tre stili:

- Un cerchio pieno è il predefinito.
- Un cerchio vuoto.
- Un quadrato pieno.

Il chevron verso il basso a destra dell'icona dell'elenco puntato apre un piccolo pannello che consente di selezionare lo stile preferito per un elemento dell'elenco selezionato:

![Strumenti di manipolazione degli elenchi puntati](../../../en/images/articles/articles-edit-list-bullets.png)

L'icona dell'elenco funziona come un interruttore. Se il cursore si trova in un paragrafo e viene selezionata una pallottola, il paragrafo diventa un elemento dell'elenco. Se la pallottola viene selezionata di nuovo, l'elemento dell'elenco torna a essere un paragrafo.

Se vengono selezionati due o più paragrafi e viene selezionata un'icona di elenco, ciascuno dei paragrafi diventa un elemento dell'elenco. Per creare un elenco rientrato, selezionare lo strumento *Aumenta rientro* a destra degli strumenti di Elenco. Per impostazione predefinita, l'elemento dell'elenco rientrato adotterà lo stile di elenco successivo.

Quindi, per spiegare come creare elenchi rientrati nello screenshot:

- Digitare ciascuno dei termini come paragrafi di una sola parola.
- Selezionare tutti i paragrafi da trasformare in un elenco puntato.
- Selezionare l'icona *Elenco puntato*.
- Selezionare il primo gruppo di termini da rientrare.
- Selezionare l'icona *Aumenta rientro*.
- Selezionare il secondo gruppo di termini da rientrare.
- Selezionare l'icona *Aumenta rientro*.

### Elenchi numerati

Sono disponibili sei stili:

- Numeri: 1, 2, 3 ...
- Lettere: a, b, c ...
- Caratteri greci: &alpha;, &beta;, &gamma; ...
- Numeri romani minuscoli: i, ii, iii ...
- Lettere maiuscole: A, B, C ...
- Numeri romani maiuscoli: I, II, III ...

![Strumenti di manipolazione degli elenchi numerati](../../../en/images/articles/articles-edit-list-numbers.png)

Gli elenchi numerati funzionano in modo leggermente diverso. Quando un elemento dell'elenco è rientrato, assume il primo valore numerico e i numeri nel resto dell'elenco salgono in modo che l'elenco sia sempre in ordine numerico corretto.

### Elenchi misti

Il sistema di numerazione può essere modificato a ciascun livello. Ad esempio, potresti impostare il primo livello per utilizzare valori numerici e il secondo livello per utilizzare pallottole, caratteri greci o qualsiasi altra cosa.

Probabilmente è meglio sperimentare con gli elenchi per vedere come possono essere manipolati.

## Elenchi di definizioni

Gli elenchi di definizioni consistono in un *Titolo di definizione* e una o più *Descrizioni di definizione* seguite dal successivo *Titolo di definizione* e dalla sua *Descrizione*. Sono utili per un *Glossario* o per qualsiasi tipo di insieme di coppie Chiave/Valore. Per creare un elenco di definizioni:

- Seleziona il pulsante *Toggle Editor* per visualizzare il markup dell'articolo HTML.
- Digita il markup dell'elenco di definizioni. Ecco un esempio:
```html
<dl>
<dt>Anfibio</dt>
<dd>Vertebrato a sangue freddo che depone le uova in acqua e ha una fase larvale acquatica.</dd>
<dt>Rettilo</dt>
<dd>Vertebrato a sangue freddo che depone le uova sulla terraferma.</dd>
</dl>
```
Salva e visualizza il risultato nell'Anteprima.

*Tradotto da openai.com*

