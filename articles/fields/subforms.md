<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Campo del Sottomodulo  -->

## Scopo

Il campo Sottoscheda consente di raggruppare una selezione di campi in un elenco ripetibile.

## Creazione del Campo

Per prima cosa, crea i campi necessari nel submodulo. Nell'esempio descritto qui ci sono un campo Calendario (Data di Acquisizione), un campo Testo (Prezzo) e un campo Colore (Colore del Fiore) da utilizzare per un elenco di diversi esemplari.

**Errore:** C'è un bug nel codice del campo Calendario che porta a un errore fatale quando si salva un articolo una seconda volta. Per evitare questo problema, imposta il valore *Mostra Ora* del campo Calendario su *Sì*.

Opzioni speciali per questo campo:

- **Titolo** e **Etichetta** In questo esempio sono impostati su *Esemplari*.
- **Campi** Aggiungi i campi richiesti nel submodulo uno per uno. Ogni riga ha un elenco a discesa dei campi disponibili e un interruttore Sì/No per i Valori di Render. L'ordine degli elementi può essere modificato con l'icona di trascinamento.

![Creazione submodulo](../../../en/images/fields/fields-subform-edit.png)

**Nota:** In questo esempio, l'inclusione del tipo di campo nel Titolo è solo per scopi dimostrativi. Omettilo nei titoli dei tuoi campi.

## Inserimento Dati

Nel modulo di inserimento dati è necessario aggiungere righe per ogni campione. Ogni riga contiene un campo Calendario, un campo Testo e un campo Colore.

![Inserimento dati sottosezione](../../../en/images/fields/fields-subform-data-entry.png)

## Visualizzazione dei Dati

Nell'articolo, il sottoform denominato Campioni ha una riga per ciascun campione.
Cerca l'elemento **Campioni** in questo screenshot:

![visualizzazione sottoform sito](../../../en/images/fields/fields-subform-site.png)

*Tradotto da openai.com*

