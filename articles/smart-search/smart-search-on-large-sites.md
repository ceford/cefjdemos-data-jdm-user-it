<!-- Filename: Smart_Search_on_large_sites / Display title: Ricerca Intelligente su Siti di Grandi Dimensioni  -->

## Indicizzazione del Sito

La Ricerca Intelligente funziona creando e mantenendo un indice indipendente di termini di ricerca in numerose tabelle del database. Il problema per i siti di grandi dimensioni è che il processo di indicizzazione può essere piuttosto pesante in termini di utilizzo della CPU, della memoria e del disco. Anche dopo la costruzione iniziale dell'indice, gli aggiornamenti incrementali possono essere pesanti. La buona notizia è che l'interrogazione dell'indice è un'operazione relativamente rapida e leggera.

La Ricerca Intelligente è adatta per la maggior parte dei siti Joomla. Tuttavia, la ricerca presenta sfide particolari per i siti di grandi dimensioni. È importante ricordare che la Ricerca Intelligente è un'implementazione PHP pura di un motore di ricerca e i siti particolarmente grandi potrebbero essere meglio serviti utilizzando un motore di ricerca indipendente come Solr.

Per utilizzare la Ricerca Intelligente su un sito di grandi dimensioni, probabilmente sarà necessario regolare alcune impostazioni di configurazione. Quello che segue è un consiglio generale su cosa osservare e cosa provare a modificare. Ci sono diversi problemi noti in sospeso riguardo all'utilizzo della Ricerca Intelligente su siti di grandi dimensioni, che si spera saranno risolti nelle versioni future e sono descritti anche qui.

## Usa Sempre l'Indicizzatore CLI

Poiché il processo di indicizzazione iniziale può richiedere molto tempo, è meglio eseguire l'indicizzatore dalla riga di comando per evitare eventuali problemi dovuti alla scadenza delle sessioni del browser. L'indicizzatore CLI non scadrà indipendentemente dal tempo necessario per completare e può essere facilmente interrotto se si riscontrano problemi. Inoltre, i messaggi di errore sono visibili con l'indicizzatore CLI, mentre sono nascosti quando si esegue dall'amministratore.

Per utilizzare il CLI, apri un terminale, passa alla cartella cli nella radice del tuo sito ed esegui il seguente comando:

```
php joomla.php finder:index
```

## Raggruppamento

L'indicizzatore suddivide il lavoro di indicizzazione in gruppi di elementi di contenuto. Di default, la dimensione del gruppo è impostata a 30, il che significa che fino a 30 elementi di contenuto verranno indicizzati per gruppo. Aumentare la dimensione del gruppo potrebbe rendere il processo di indicizzazione più veloce, ma utilizzerà più memoria e possibilmente più spazio su disco temporaneo.

## Problemi di memoria insufficiente

Se l'indicizzatore esaurisce la memoria, prova a fare i seguenti aggiustamenti uno alla volta fino a risolvere il problema.

1. Riduci la dimensione del batch. Se hai elementi di contenuto particolarmente grandi, l'indicizzatore può esaurire la memoria anche con un singolo elemento di contenuto, quindi prova a ridurla inizialmente a 5 e, se ancora esaurisci la memoria, riducila a 1.
2. Se riesci ad allocare più memoria all'indicizzatore, fallo. Puoi aumentare la memoria allocata all'indicizzatore da riga di comando utilizzando un parametro extra sulla riga di comando. Ad esempio, per aumentare il limite di memoria a 256Mb usa il seguente comando, sostituendo *256M* con la quantità di memoria che puoi allocare in sicurezza a un processo sul tuo sistema.<br>
   *php -d memory_limit=256M finder_indexer.php*
3. Riduci il limite della tabella di memoria. Il valore predefinito è di 30000 termini, il che significa che non appena la tabella temporanea in memoria *#__finder_tokens* raggiunge questo numero di righe, l'indicizzatore passerà a utilizzare una tabella su disco anziché una tabella di memoria. Potrebbe essere che tu non abbia abbastanza memoria per gestire una tabella di memoria completa o quasi, quindi ridurre il limite indicherà all'indicizzatore di passare al disco prima e quindi utilizzare meno memoria. Prova 10000 o anche numeri molto più piccoli.
4. Cambia il motore di database utilizzato per le tabelle *__finder_tokens* e *#__finder_tokens_aggregate* da MEMORY a InnoDB. Questo potrebbe avere un impatto significativo sulle prestazioni poiché più il processo di indicizzazione utilizzerà il disco invece della memoria, ma potrebbe consentire all'indicizzatore di concludere senza esaurire la memoria. Aspettati che il processo di indicizzazione duri molto più a lungo. Tuttavia, questo non influirà sulle prestazioni della ricerca.
5. Prova a identificare quali elementi di contenuto stanno causando l'esaurimento della memoria dell'indicizzatore. Se non è ovvio, potresti provare a disabilitare tutti i plugin di Smart Search tranne uno. Eseguire l'indicizzatore con un solo plugin abilitato alla volta dovrebbe rivelare quale tipo di contenuto sta causando il problema. Come ultima risorsa, considera di suddividere pochi elementi di contenuto eccezionalmente grandi in elementi separati. Se il problema riguarda un tipo di contenuto personalizzato, guarda il codice del plugin e considera l'indicizzazione di meno contenuto disponibile per elemento.

## Problemi di Spazio su Disco

Le tabelle dell'indice Smart Search possono crescere rapidamente! Le tabelle *#__finder_links_termsX* (dove *X* è un singolo carattere esadecimale) contengono una riga per termine/frase per elemento di contenuto e un singolo articolo di Joomla contenente 1000 parole tipicamente porterà ad aggiungere circa 3000 righe a queste tabelle. Un secondo articolo di dimensioni simili aggiungerà un numero simile di righe anche se entrambi gli articoli contengono le stesse parole. Un sito con decine di migliaia di articoli, alcuni dei quali possono contenere migliaia di parole, è probabile che finisca con queste tabelle di mappatura che contengono milioni di righe. Non è insolito che le tabelle dell'indice occupino diversi gigabyte di spazio su disco in tali circostanze.

Con la versione attuale di Smart Search, non c'è molto che si possa fare riguardo a questo. Tuttavia, si spera che nella prossima versione sarete in grado di regolare il numero di parole per frase che vengono indicizzate. Al momento, questo è integrato in modo fisso a 3, il che significa che ogni parola che viene indicizzata è anche indicizzata come parte di una coppia di parole adiacenti e come parte di un trittico di parole adiacenti. Questo è utile per la funzione di completamento automatico e generalmente migliora la qualità dei risultati di ricerca. Su siti dove lo spazio su disco è un problema, sarebbe utile ridurre questo numero a 2 o addirittura 1, in modo che le tabelle di mappatura siano corrispondentemente più piccole.

## Note

1. Attualmente non c'è un blocco di concorrenza per impedire a più di un processo di eseguire l'indicizzatore contemporaneamente. Questo porterà quasi certamente a un indice corrotto. Anche qualcuno che salva modifiche a un elemento di contenuto mentre è in corso una indicizzazione completa potrebbe potenzialmente danneggiare l'indice.

*Tradotto da openai.com*

