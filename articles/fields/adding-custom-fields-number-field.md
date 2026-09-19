<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Campo numerico",
    "description": " ",
    "author": ""
}
-->

## Scopo

Il campo numerico consente di immettere un numero reale con la possibilità di associare una valuta o un altro simbolo prima o dopo il numero. Il controllo può essere utilizzato come campo intero con frecce di incremento e decremento e un intervallo predefinito da 1 a 100. Tuttavia, nel campo è possibile immettere valori reali, positivi o negativi. Esempio: `99.99` potrebbe essere formattato per apparire all’utente finale come `£99.99`. Oppure `-273.15` potrebbe apparire all’utente finale come `-273.15C`.

## Creazione del campo

### Scheda generale

![Creazione del campo numerico](../../../en/images/fields/adding-custom-fields-number-field/01-fields-number-edit.png)

- **Tipo** Numero, che non può essere modificato dopo la selezione.
- **Nome** Il nome univoco del campo.
- **Etichetta** Un'etichetta traducibile per il campo.
- **Descrizione** Una descrizione traducibile facoltativa del campo.
- **Obbligatorio** Impostare su *Sì* se questo campo è obbligatorio?
- **Utilizza solo nel sott modulo** *Sì o *No.
- **Valore predefinito** Un valore predefinito facoltativo.
- **Minimo** Il valore minimo che può essere selezionato utilizzando le frecce su/giù; il valore predefinito è 1. Può essere un numero negativo, quindi impostarlo su un valore inferiore al numero più basso previsto, **altrimenti la selezione della freccia giù potrebbe cancellare il numero esistente**.
- **Massimo** Il valore massimo che può essere selezionato utilizzando le frecce su/giù; il valore predefinito è 100. Impostarlo su un valore superiore al numero più alto previsto, **altrimenti la selezione della freccia su potrebbe cancellare il numero esistente**.
- **Incremento del passo** La dimensione dell’incremento aggiunto o sottratto al valore del campo corrente utilizzando le frecce su/giù. Può essere un numero intero, il valore predefinito è 1, oppure un numero decimale come 0.01. **Impostarlo sull’importo minimo con cui si desidera incrementare o decrementare il valore**.
- **Formatta come valuta** Se selezionato, sono disponibili campi aggiuntivi:
    - **Simbolo della valuta** Può essere un singolo simbolo, come `£` o `$`, oppure una stringa di caratteri, come `&deg;C`, che viene visualizzata come *&deg;C*.
    - **Posizione del simbolo** Selezionare *Prima* o *Dopo* il numero.
    - **Numero di decimali** In genere 2 per le valute, ma può essere diverso in altri contesti.

### Scheda Opzioni

#### Pannello delle opzioni del modulo:

- **Segnaposto**  Testo segnaposto che verrà visualizzato all'interno del campo come suggerimento per l'utente per l'input richiesto.
- **Classe del campo** Classe opzionale aggiunta al campo del modulo di immissione dati.
- **Classe dell'etichetta** Classe opzionale aggiunta all'etichetta del modulo di immissione dati.
- **Modificabile in** Interfacce di modifica consentite: *Sito*, *Amministratore* o *Entrambi*.
- **Attributo Showon** Mostra o nasconde condizionalmente il campo in base al valore di altri campi.

#### Pannello delle opzioni di visualizzazione:

- **Classe di visualizzazione** La classe del contenitore del campo nell’output.
- **Classe del valore** La classe del valore del campo nell’output.
- **Etichetta** *Mostra* o *Nascondi* l’etichetta nell’output. Se impostata su Mostra:
    - **Classe dell’etichetta (output)** Una classe per l’etichetta nell’output.
- **Visualizzazione automatica** Se e dove visualizzare il campo:
    - **Dopo il titolo**
    - **Prima del contenuto visualizzato**
    - **Dopo il contenuto visualizzato**
    - **Non visualizzare automaticamente**
- **Prefisso** Testo che verrà visualizzato prima del valore del campo.
- **Suffisso** Testo che verrà visualizzato dopo il valore del campo.
- **Layout** Un elenco dei layout disponibili.
- **Visualizza in sola lettura** Scelta tra *Eredita*, *Sì* o *No*.

#### Pannello della ricerca intelligente

- **Indice di ricerca** Scelta se effettuare o meno la ricerca e del metodo di ricerca.

### Schede Pubblicazione e autorizzazioni

Il contenuto di queste schede è autoesplicativo e trattato altrove.

## Inserimento dei dati

Inserimento dei dati: è sufficiente digitare il valore desiderato. Questo esempio mostra il punto di ebollizione dell'Argon:

![Inserimento di dati in un campo numerico](../../../en/images/fields/adding-custom-fields-number-field/02-fields-number-data-entry.png)

**Attenzione:** se il numero inserito non rientra nell'intervallo minimo e massimo impostato nelle opzioni di creazione del campo, un'etichetta al passaggio del mouse del browser lo segnalerà, ma le informazioni fornite non vengono applicate. È possibile inserire un numero al di fuori dell'intervallo e questo verrà accettato.

## Visualizzazione dei dati

L'immagine seguente mostra la visualizzazione di un elemento con un valore negativo:

![Visualizzazione di un campo numerico nel sito](../../../en/images/fields/adding-custom-fields-number-field/03-fields-number-site.png)

*Tradotto da openai.com*