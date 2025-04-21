<!-- Filename: Smart_Search_on_large_sites / Display title: Ricerca Intelligente su Siti Grandi -->

## Indicizzazione del sito

La Ricerca Intelligente funziona creando e mantenendo un indice indipendente di termini di ricerca in diversi tabelle del database. Il problema per i grandi siti è che il processo di indicizzazione può essere piuttosto pesante in termini di utilizzo della CPU, della memoria e del disco. Anche dopo la costruzione iniziale dell'indice, gli aggiornamenti incrementali possono essere altrettanto pesanti. La buona notizia è che interrogare l'indice è un'operazione relativamente veloce e leggera.

Smart Search è adatto per la maggior parte dei siti Joomla. Tuttavia, la ricerca presenta sfide particolari per i siti grandi. Si dovrebbe ricordare che Smart Search è una pura implementazione PHP di un motore di ricerca e i siti particolarmente grandi potrebbero trarre beneficio dall'utilizzo di un motore di ricerca indipendente come Solr.

Per utilizzare Smart Search su un sito di grandi dimensioni, probabilmente sarà necessario regolare alcune delle impostazioni di configurazione. Quanto segue è un consiglio generale su cosa considerare e su cosa provare a modificare.

## Utilizzare sempre l'indicizzatore CLI

Poiché il processo di indicizzazione iniziale può richiedere molto tempo, è meglio eseguire l'indicizzatore dalla riga di comando per evitare eventuali problemi causati dalla scadenza delle sessioni del browser. L'indicizzatore CLI non andrà in timeout indipendentemente da quanto tempo impiega per completare il processo e può essere facilmente interrotto in caso di problemi. Inoltre, i messaggi di errore sono visibili con l'indicizzatore CLI, mentre potrebbero essere nascosti quando si esegue dall'Amministratore.

Per utilizzare la CLI, apri un terminale, passa alla cartella cli nella radice del tuo sito ed emetti il seguente comando:

```
php joomla.php finder:index
```

## Batchificazione

L'indicizzatore suddivide il lavoro di indicizzazione in gruppi di elementi di contenuto. Per impostazione predefinita, la dimensione del gruppo è impostata su 50, il che significa che fino a 50 elementi di contenuto verranno indicizzati per gruppo. Aumentare la dimensione del gruppo potenzialmente renderà più veloce il processo di indicizzazione, ma utilizzerà più memoria e possibilmente più spazio su disco temporaneo.

## Problemi di Esaurimento della Memoria

Se l'indicizzatore sta esaurendo la memoria, prova a fare i seguenti aggiustamenti uno alla volta finché il problema non è risolto.

1. Riduci la dimensione del batch. Se hai contenuti particolarmente grandi, l'indicizzatore può esaurire la memoria anche con un singolo elemento di contenuto, quindi prova inizialmente a portarlo a 5 e, se la memoria si esaurisce ancora, riducilo a 1.  
   
2. Se sei in grado di allocare più memoria all'indicizzatore, fallo. Puoi aumentare la memoria allocata all'indicizzatore da linea di comando utilizzando un parametro extra sulla linea di comando. Ad esempio, per aumentare il limite di memoria a 256 Mb usa il seguente comando, sostituendo *256M* con quanta più memoria puoi allocare in sicurezza a un processo sul tuo sistema.<br>  
   *php -d memory_limit=256M finder_indexer.php*  
   
5. Cerca di identificare quali elementi di contenuto stanno causando l'esaurimento della memoria dell'indicizzatore. Se non è evidente, potresti provare a disabilitare tutti i plugin di Smart Search tranne uno. Eseguire l'indicizzatore con un solo plugin abilitato alla volta dovrebbe rivelare quale o quali tipi di contenuto stanno causando il problema. Come ultima risorsa, considera di suddividere alcuni elementi di contenuto eccezionalmente grandi in elementi separati. Se il problema riguarda un tipo di contenuto personalizzato, esamina il codice del plugin e considera l'opzione di indicizzare meno del contenuto disponibile per elemento.

## Problemi di Spazio su Disco Esaurito

Le tabelle dell'indice Ricerca Smart possono crescere rapidamente! La tabella *#__finder_links_termsX* contiene una riga per termine/frase per elemento di contenuto e un singolo articolo di Joomla contenente 1000 parole comporterà tipicamente l'aggiunta di circa 3000 righe a queste tabelle. Un secondo articolo di dimensioni simili aggiungerà un numero simile di righe, anche se entrambi gli articoli contengono le stesse parole. Un sito con decine di migliaia di articoli, alcuni dei quali possono contenere migliaia di parole, è probabile che finisca con questa tabella di mappatura contenente milioni di righe. Non è insolito che le tabelle dell'indice occupino diversi gigabyte di spazio su disco in tali circostanze.

L'indice ha un'opzione per decidere tra la precisione della ricerca e la dimensione dell'indice. Quando hai "Cerca per frasi" abilitato nelle opzioni globali del componente, il tuo indice sarà più grande, ma permetterà anche risultati di ricerca più precisi. Se è disabilitato, l'indice sarà molto più piccolo, ma non ci sarà la possibilità di cercare intere frasi.

## Note

1. Attualmente non esiste un meccanismo di blocco della concorrenza per impedire che più di un processo esegua l'indicizzatore contemporaneamente. Questo comporterà quasi certamente un indice corrotto. Anche qualcuno che salva le modifiche a un elemento di contenuto mentre viene eseguito un'indicizzazione completa potrebbe potenzialmente danneggiare l'indice.

*Tradotto da openai.com*

