<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Campo di Colore  -->
## Scopo

Il campo Colore offre uno strumento per la selezione visiva di un colore. Il campo mostra il valore esadecimale risultante.


## Creazione del Campo

Opzioni speciali per questo campo:

- **Classe del Campo** Imposta su *w-auto* per rendere il campo sufficientemente largo per il campione e il valore.

## Inserimento Dati

Puoi digitare un valore colore esadecimale se sai che i numeri esadecimali vanno da 0 a 9
e poi da a ad f e le coppie di numeri rappresentano rosso, verde e blu. Quindi #00ff00 è
niente rosso, massimo verde e niente blu. Oppure puoi usare un cursore per selezionare un colore
visivamente.

![Selettore di colori](../../../en/images/fields/fields-colour-entry.png "Selettore di colori")


## Visualizzazione dei Dati

Lo screenshot del sito seguente mostra il campo visualizzato in un articolo. L'opzione *Visualizzazione automatica* è responsabile della posizione del campo e il tuo template è responsabile del design del campo.

La visualizzazione predefinita dei dati è il valore colore esadecimale, che non è molto utile. La soluzione semplice è creare un override del template per i plugin dei campi/colori. Basta sostituire questa linea:
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

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei Campi")

