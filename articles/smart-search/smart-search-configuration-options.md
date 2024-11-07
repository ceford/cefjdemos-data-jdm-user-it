<!-- Filename: Smart_Search_configuration_options / Display title: Opzioni di Ricerca Intelligente  -->

## Informazioni sulle Opzioni

Le opzioni ti permettono di gestire le impostazioni globali della Ricerca Intelligente. Le impostazioni delle Opzioni vengono ereditate dalle visualizzazioni, ma le impostazioni in un Elemento di Menu sovrascrivono le impostazioni Globali.

Il pannello delle Opzioni è diviso in due parti. Quando hai finito di apportare modifiche, seleziona il pulsante Salva, altrimenti seleziona il pulsante Annulla per abbandonare eventuali modifiche.

## Opzioni di Ricerca

Le opzioni di ricerca controllano il comportamento dei moduli di ricerca e dei risultati della ricerca per l'interfaccia del Finder.

- **Descrizione dei Risultati** - Questa opzione controlla se i risultati della ricerca
  devono essere mostrati con descrizioni. Predefinito: Mostra.
- **Lunghezza della Descrizione** - Questa opzione controlla la lunghezza massima, in caratteri,
  delle descrizioni dei risultati della ricerca. Le descrizioni sono
  troncate alla lunghezza massima, ma il troncamento avviene sempre all'ultima
  spazio in modo da non troncare nel mezzo di una
  parola. Efficace solo quando l'opzione Descrizione dei Risultati è impostata su
  Mostra. Predefinito: 255 caratteri.
- **URL dei Risultati** - Questa opzione controlla se i risultati della ricerca devono essere
  mostrati con URL sotto la descrizione (se attiva). Predefinito: Mostra.
- **Ricerca Avanzata** - Questa opzione controlla se devono essere mostrate le opzioni di
  ricerca avanzata. Predefinito: Mostra.
- **Espandi Ricerca Avanzata** - Le opzioni di ricerca avanzata sono contenute
  in un contenitore espandibile. Questa opzione controlla se il contenitore delle opzioni
  di ricerca avanzata deve essere espanso per impostazione predefinita. Predefinito: No.
- **Filtri per Data** - Questa opzione controlla se i filtri di data
  devono essere mostrati nelle opzioni di ricerca avanzata. Predefinito: Nascondi.
- **Etichette dei Risultati** - Questa opzione controlla se i risultati della ricerca devono
  essere mostrati con Etichette. Richiede che JXtended Labels sia installato.
  Predefinito: Mostra.
- **Evidenzia Termini di Ricerca** - Questa opzione controlla se i termini di ricerca
  devono essere evidenziati nei risultati della ricerca. Predefinito: Sì.

## Opzioni dell'Indice

Le opzioni dell'indice controllano il comportamento dell'indicizzatore utilizzato per elaborare e analizzare il contenuto per la ricerca. La maggior parte delle impostazioni, come il moltiplicatore di peso e le opzioni del stemmer, non produrranno cambiamenti immediati poiché vengono utilizzate durante l'indicizzazione e gli effetti di tali modifiche saranno visibili solo dopo che l'indice è stato eliminato e rieseguito.

- **Dimensione Batch Indicizzatore** - Questa opzione controlla la dimensione del batch dell'indicizzatore. L'indicizzatore di Ricerca Intelligente suddivide l'intero processo di indicizzazione in un numero di batch per ridurre il carico sul server ed evitare i limiti di memoria ed esecuzione di PHP. Se gli elementi di contenuto indicizzati sono particolarmente brevi e/o il server è particolarmente veloce, l'indicizzatore può elaborare più elementi per batch. Tuttavia, se gli elementi di contenuto indicizzati sono particolarmente lunghi e/o il server è particolarmente lento, l'indicizzatore deve elaborare meno elementi per batch. Predefinito a 50.
- **Limite Tabella di Memoria** - Questa opzione controlla il limite della tabella di memoria. L'indicizzatore di Ricerca Intelligente utilizza tabelle di memoria MySQL per memorizzare temporaneamente i dati del contenuto invece di memorizzare i dati nei buffer di memoria di PHP poiché elementi di contenuto di grandi dimensioni esauriranno rapidamente le impostazioni predefinite del limite di memoria di PHP. Tuttavia, le tabelle di memoria MySQL hanno anche limiti di dimensione regolabili e il loro riaggiustamento non è affidabile. Questa impostazione è fornita per gestire tabelle di memoria con limiti di dimensione inferiori al solito e dovrebbe essere regolata solo quando si verificano errori di "Tabella piena" durante l'indicizzazione. Predefinito a 30.000. Se si incontrano errori di "tabella piena", provare a **ridurre** questo parametro. Il valore ottimale dovrebbe risultare in tabelle di memoria che sono un po' più piccole del parametro <a href="http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_max_heap_table_size" rel="nofollow noreferrer noopener"><em>max_heap_table_size</em></a> in MySQL, che predefinito è di 16 megabyte.
- **Moltiplicatore di Peso del Testo del Titolo** - Questa opzione controlla quanto influisce il testo del titolo sul punteggio complessivo di rilevanza di un risultato di ricerca. Predefinito a 1.7.
- **Moltiplicatore di Peso del Testo del Corpo** - Questa opzione controlla quanto influisce il testo del corpo sul punteggio complessivo di rilevanza di un risultato di ricerca. Predefinito a 0.7.
- **Moltiplicatore di Peso dei Meta Dati** - Questa opzione controlla quanto influiscono i meta-dati sul punteggio complessivo di rilevanza di un risultato di ricerca. Predefinito a 1.2.
- **Moltiplicatore di Peso del Testo del Percorso** - Questa opzione controlla quanto influisce il testo del percorso/URL sul punteggio complessivo di rilevanza di un risultato di ricerca. Predefinito a 2.0.
- **Moltiplicatore di Peso del Testo Varie** - Questa opzione controlla quanto influisce il testo vario sul punteggio complessivo di rilevanza di un risultato di ricerca. Predefinito a 0.3.
- **Stemmer** - Questa opzione controlla quale stemmer linguistico dovrebbe essere utilizzato durante l'indicizzazione. Lo stemmer solo inglese è un'implementazione pura in PHP che non ha dipendenze. Lo stemmer Snowball richiede l'estensione PHP Stem ma fornisce supporto per 14 lingue tra cui danese, tedesco, inglese, spagnolo, finlandese, francese, ungherese, italiano, norvegese, olandese, portoghese, rumeno, russo e turco. Predefinito a Solo Inglese.
- **Abilita Registrazione** - crea un file di registro durante il processo di indicizzazione. Predefinito a no.

*Tradotto da openai.com*

