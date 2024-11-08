<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Campo di colore -->

## Scopo

Il campo Colore offre un selettore per la scelta visiva di un colore. Il campo mostra il valore esadecimale risultante.

## Creazione del Campo

Opzioni speciali per questo campo:

- **Classe del Campo** Imposta su *w-auto* per rendere il campo abbastanza largo
per la selezione e il valore.

![Creazione del campo colore](../../../en/images/fields/fields-colour-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo a scopo dimostrativo. Escludilo nei tuoi titoli di campo.

## Inserimento Dati

Puoi digitare un valore colore esadecimale se sai che i numeri esadecimali vanno da 0 a 9 e poi da a a f, e le coppie di numeri rappresentano rosso, verde e blu. Quindi #00ff00 è niente rosso, massimo verde e niente blu. Oppure puoi usare un cursore per selezionare un colore visivamente.

![Inserimento dati del campo colore](../../../en/images/fields/fields-colour-data-entry.png)

## Visualizzazione dei Dati

Lo screenshot del sito qui sotto mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile per la posizione del campo e il tuo template è responsabile per il design del campo.

La visualizzazione predefinita dei dati è il valore colore esadecimale, che non è di grande utilità. La soluzione semplice è creare un override del template per i campi / plugin colore. Basta sostituire questa riga:
```
echo htmlentities($value);
```
con queste righe:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
E il valore esadecimale sarà preceduto da un campione con il colore di sfondo del valore.

Cerca l'elemento **Colore del Fiore**.

![visualizzazione del campo colore nel sito](../../../en/images/fields/fields-colour-site.png)

