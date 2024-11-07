<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Campo del Sottoformulario -->

## Scopo

Il Campo Sottoforma consente di raggruppare una selezione di campi in un elenco ripetibile.

## Creazione del Campo

Prima crea i campi necessari nel sottoforma. Nell'esempio descritto qui c'è un campo Calendario (Data di Acquisizione), un campo Testo (Prezzo) e un campo Colore (Colore del Fiore) da utilizzare per un elenco di diversi esemplari.

**Bug:** C'è un bug nel codice del campo Calendario che porta a un errore fatale quando si salva un articolo una seconda volta. Per evitare questo problema, imposta il valore *Mostra Ora* del campo Calendario su *Sì*.

Opzioni speciali per questo campo:

- **Titolo** e **Etichetta** In questo esempio sono impostati su *Esemplari*.
- **Campi** Aggiungi uno per uno i campi richiesti nel sottoform. Ogni riga ha una lista a discesa dei campi disponibili e un toggle Sì/No per i Valori di Rendering. L'ordine degli elementi può essere cambiato con l'icona di trascinamento.

![Creazione del sottoforma](../../../en/images/fields/fields-subform.png "Creazione del sottoforma")

## Inserimento Dati

Nel modulo di inserimento dati è necessario aggiungere righe per ciascun campione. Ogni riga contiene un campo Calendario, un campo Testo e un campo Colore.

![Inserimento dati nel sottomodulo](../../../en/images/fields/fields-subform-entry.png "Inserimento dati nel sottomodulo")

## Visualizzazione dei Dati

Nell'Articolo, il sottormulario intitolato Campioni ha una riga per ciascun campione. Cerca l'elemento **Campioni** in questo screenshot:

![Visualizzazione di tutti i campi](../../../en/images/fields/fields-display.png "Visualizzazione dei campi")

*Tradotto da openai.com*

