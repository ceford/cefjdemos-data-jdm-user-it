<!-- Filename: Smart_Search_Frequently_Asked_Questions / Display title: Domande frequenti sulla ricerca intelligente -->

## Perché dovrei usare la ricerca intelligente?

La tecnologia di ricerca è migliorata notevolmente nel corso degli anni da quando Joomla è stato lanciato per la prima volta, eppure il componente di ricerca standard e di base non è cambiato molto in quel periodo. È ancora molto rudimentale e manca del tipo di funzionalità di ricerca a cui gli utenti del web si sono abituati, specialmente data la diffusione di motori di ricerca avanzati come Google. La ricerca intelligente ti consente di incorporare alcune di quelle funzionalità di ricerca più avanzate nel tuo sito web.

## Perché Creare un Plugin di Ricerca Intelligente?

Generalmente, se hai un tipo di contenuto che non è gestito dai componenti principali di Joomla e vuoi offrire ai visitatori del tuo sito la possibilità di cercare quel contenuto, avrai bisogno di scrivere un Plugin di Ricerca Intelligente per supportarlo. Ad esempio, supponi di avere un componente che memorizza informazioni su diverse specie animali. Il componente mantiene una tabella nel database contenente campi come nome scientifico, nome volgare, classificazione e una descrizione. In questo caso, dovrai creare un Plugin che dica all'indicizzatore di Ricerca Intelligente come indicizzare i dati in quella tabella. Oltre a indicizzare singole parole e frasi, puoi anche fare in modo che il Plugin aggiunga ogni record a una mappa dei contenuti, che in questo caso potrebbe includere le <a href="https://en.wikipedia.org/wiki/Taxonomy_(biology)" rel="nofollow noreferrer noopener">classificazioni biologiche di regno, phylum, classe, ordine e famiglia</a>. Le mappe dei contenuti possono quindi essere utilizzate per filtrare i risultati di ricerca.

## È possibile selezionare più nodi dai menu a tendina del filtro?

Sì, questo è pienamente supportato da Smart Search stesso. Infatti, puoi utilizzare qualsiasi interfaccia utente tu voglia creare per i filtri. Dai un'occhiata al codice fornito nel modulo e nel componente standard del Frontend e vedrai come farlo.

## Ho un sito grande. Posso usare Smart Search?

I siti di grandi dimensioni potrebbero ottenere risultati migliori con un motore di ricerca dedicato e autonomo, come Solr, piuttosto che con l'implementazione completamente PHP utilizzata in Smart Search. In questa prima iterazione della ricerca avanzata in Joomla, è probabile che vengano evidenziati problemi relativi alla scalabilità e alle prestazioni. C'è anche il potenziale per condizioni di concorrenza nel momento in cui l'indice viene aggiornato a seguito di frequenti modifiche al contenuto. Si prevede che questi problemi saranno affrontati in modo più completo in una futura versione di Joomla.

## Perché Smart Search Ha Così Tanti Table?

Smart Search aggiunge un bel po’ di nuove tabelle a un'installazione Joomla,
incluse 16 "tabelle di mappatura". Queste tabelle di mappatura risolvono la
relazione molti-a-molti tra i termini di ricerca e i contenuti che li contengono.
In teoria, quelle 16 tabelle potrebbero essere unite in una singola tabella e farlo
avrebbe un impatto trascurabile su siti piccoli. Tuttavia, su siti più grandi
ci sarebbe un impatto sostanziale sulle prestazioni perché la tabella di
mappatura avrebbe un numero molto elevato di dati e l'aggiornamento di una tale
grande tabella può richiedere molto tempo.

## Perché la Ricerca Intelligente Utilizza Così Tanto Spazio su Disco?

Mantenere un indice di termini di ricerca richiede una quantità considerevole di spazio su disco,
che aumenta con il numero di termini contenuti negli elementi di contenuto. Poiché anche le frasi
sono indicizzate, più lunghe sono le frasi, maggiore è lo spazio su disco richiesto.
Per la Ricerca Intelligente in Joomla 2.5, la lunghezza massima di una frase è stata
fissata a 3 termini come compromesso ragionevole tra l'usabilità della ricerca e
l'uso dello spazio su disco. È probabile che questo sarà un parametro che potrà essere
regolato in una versione futura della Ricerca Intelligente.

## Perché le voci nelle tabelle di mapping non sono distribuite in modo uniforme?

È forse sorprendente che il numero di voci in ciascuna delle tabelle di mapping non sia nemmeno approssimativamente lo stesso. Sicuramente le prestazioni migliorerebbero con una distribuzione uniforme? In realtà no, c'è un compromesso tra le prestazioni di inserimento e quelle di ricerca, con una distribuzione uniforme che è buona per le prime ma scarsa per le seconde. Questo è un campo di ricerca continua, con il numero di tabelle e l'algoritmo di distribuzione soggetti a cambiamenti alla luce dell'esperienza.  

## Perché esiste un plugin di Contenuto di Ricerca Intelligente separato?

Questo è semplicemente un pratico strumento che facilita l'attivazione o la disattivazione di tutti i plugin di Ricerca Intelligente con un'unica operazione. Ciò è stato ritenuto desiderabile perché la Ricerca Intelligente non è abilitata di default in Joomla 2.5.

## Perché i Plugin di Ricerca Intelligente Usano Eventi Separati come *onFinderContentAfterSave*?

La Ricerca Intelligente utilizza i propri eventi, come onFinderContentAfterSave, invece dell'equivalente generico onContentAfterSave, esclusivamente per comodità al fine di rendere facile abilitare o disabilitare l'indicizzazione della Ricerca Intelligente attivando/disattivando un singolo Plugin.

## Perché la Smart Search non è abilitata di default in Joomla 2.5 e Joomla 3.x?

Poiché Joomla 2.5 è l'ultima della serie 1.x/2.x, deve mantenere un alto grado di compatibilità retroattiva con la versione precedente della serie. Siccome la Smart Search è qualcosa di completamente nuovo e non presenta alcuna somiglianza con il componente di ricerca regolare di questa o delle versioni precedenti, è stato considerato importante che gli utenti che aggiornano da quelle versioni non siano costretti a cambiare il modo in cui la ricerca funziona sui loro siti. Infatti, l'attivazione della Smart Search è qualcosa che dovrebbe essere fatto in modo attentamente considerato.

## Perché non esiste un'API di ricerca?

L'obiettivo della versione attuale di Smart Search era trasferire il codice dal vecchio componente JXtended Finder all'ultima versione di Joomla. Poiché quel codice era già considerato stabile e c'era solo una breve finestra di opportunità per portare il codice, si è ritenuto che un'importante ristrutturazione di Finder fosse fuori portata per il rilascio di Joomla 2.5. Di conseguenza, il codice utilizza i plugin per evitare modifiche al codice principale del CMS, invece di sviluppare una vera e propria API di ricerca. Ci proponiamo di creare tale API per una futura iterazione di Joomla.

## La Ricerca Intelligente Può Eseguire la Ricerca a Facce?

Sì. La ricerca avanzata disponibile dalla pagina dei risultati di ricerca e il modulo di ricerca intelligente forniscono un esempio di come è possibile filtrare i risultati di ricerca per produrre una ricerca a facce. Non c'è nulla che ti impedisca di creare le tue variazioni su queste idee di base. Ad esempio, potresti modificare i menu a discesa semplici per accettare selezioni multiple, oppure potresti sostituire i menu a discesa con una serie di caselle di controllo.

## Perché le ricerche con caratteri jolly non sono supportate?

La vecchia ricerca di Joomla utilizzava un metodo di ricerca molto primitivo che si basava sulla ricerca FULLTEXT fornita dal database. Questo metodo era molto inefficiente, ma offriva un modo semplice per gestire le query di ricerca con caratteri jolly. La Smart Search fornisce una funzione di completamento automatico che è in pratica una ricerca con caratteri jolly dei termini nell'indice, ma la ricerca completa con caratteri jolly non è supportata a causa del potenziale rischio di sovraccaricare il server in caso di abuso della funzione. Nella maggior parte dei casi, le ricerche con caratteri jolly vengono utilizzate per gestire variazioni di un termine di ricerca. Ad esempio, cercare *giocol\** per includere i riferimenti a *giocoleria* e *giocoliere*. La Smart Search cerca di evitare la necessità di usare caratteri jolly supportando invece la derivazione delle parole, dove le parole che hanno lo stesso tema sono considerate equivalenti, in modo che cercare *giocoliere* recuperi anche le istanze di *giocoleria* senza dover usare i caratteri jolly.

## La ricerca intelligente può essere utilizzata su siti multilingue?

Sì, ma ci sono ancora alcuni problemi da risolvere, in particolare riguardo al supporto per le lingue asiatiche.

- Per essere indicizzato correttamente, è necessario assicurarsi che tutto il contenuto sia in UTF-8 valido.
- La funzione *Forse cercavi?* utilizza la funzione Soundex per trovare frasi di ricerca foneticamente simili. Tuttavia, Soundex non funziona bene per le lingue diverse dall'inglese e per molte lingue non funziona affatto. Attualmente stiamo ricercando metodi alternativi per fornire questa funzionalità.

Se utilizzi la ricerca intelligente su un sito multilingue e incontri problemi, ti preghiamo di segnalarli nel tracker in modo che possiamo comprendere meglio i problemi da risolvere.

## I plugin Finder *jXTended* funzioneranno con Smart Search?

No. Sarà necessario aggiornare i plugin Finder affinché funzionino con Smart Search. Tuttavia, le modifiche non dovrebbero essere difficili da implementare e, nella maggior parte dei casi, porteranno a una quantità di codice significativamente ridotta. Se dai un'occhiata agli attuali plugin Smart Search, dovresti vedere che l'aggiornamento di un plugin Finder è piuttosto semplice.

*Tradotto da openai.com*

