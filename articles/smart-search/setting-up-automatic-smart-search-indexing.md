<!-- Filename: Setting_up_automatic_Smart_Search_indexing / Display title: Indicizzazione di Ricerca Intelligente -->

## Indicizzazione Automatica

Anche se l'indice di Smart Search viene mantenuto automaticamente aggiornato ogni volta che gli elementi di contenuto vengono modificati, ci sono alcune circostanze in cui è necessario eseguire nuovamente l'indicizzatore. Puoi farlo manualmente utilizzando il pulsante della toolbar "Indice" nella pagina Smart Search: Contenuto Indicizzato. Tuttavia, se hai bisogno di reindicizzare il contenuto automaticamente, è anche possibile eseguire l'indicizzatore dalla riga di comando. Questo è particolarmente conveniente per eseguire l'indicizzatore da un lavoro *cron*.

Dalla directory cli, la linea di comando è:

```
php joomla.php finder:index
```

L'output tipico dall'indicizzatore della riga di comando appare così:

    INDICIZZATORE Smart Search
    ============================

    Avvio dell'Indicizzatore
    Impostazione dei plugin di Finder
    Impostati 154 elementi in 0.094 secondi.
     * Batch 1 processato in 0.213 secondi.
     * Batch 2 processato in 0.182 secondi.
     * Batch 3 processato in 0.177 secondi.
     * Batch 4 processato in 0.009 secondi.
    Tempo totale di elaborazione: 0.676 secondi.

## Pulizia Prima dell'Indicizzazione

Normalmente, eseguire l'indicizzatore comporterà un aggiornamento incrementale dell'indice. Vale a dire, aggiornerà solo l'indice per quegli elementi di contenuto che sono cambiati dall'ultimo aggiornamento dell'indice. Tuttavia, se hai bisogno di cancellare completamente tutte le voci attuali dell'indice prima di ricostruirlo completamente, devi eseguire un'operazione di "pulizia e poi indicizzazione". Per farlo, puoi aggiungere l'argomento `--purge` alla riga di comando, in questo modo:

    php joomla.php finder:index -- purge

Nota che questo cercherà di preservare eventuali filtri statici che potresti aver configurato, mentre cliccando sul pulsante "Purge" nella barra degli strumenti dell'Amministratore **non** preserverà i tuoi filtri statici. 

## Configurare un Job *cron*

Sebbene i dettagli specifici vadano oltre lo scopo di questo articolo, in generale
dovrai semplicemente inserire il comando sopra nel gestore di job *cron*
e specificare l'ora o le ore in cui il job deve essere eseguito. Probabilmente
dovrai includere il percorso completo all'indicizzatore. Per esempio,
in questo modo:

    php /var/www/myjoomla/cli/joomla.php finder:index -- purge

E possibilmente il percorso completo al file php come `/usr/local/opt/php@8.2/bin/php`.

## Problemi di Memoria Insufficiente

Se il tuo sito ha requisiti di indicizzazione particolarmente complessi, è possibile che l'allocazione standard di memoria non sia sufficiente affinché l'indicizzatore completi l'operazione. Puoi aumentare la memoria allocata all'indicizzatore da riga di comando utilizzando un parametro aggiuntivo, in questo modo:

    php -d memory_limit=256M joomla.php finder:index

Sostituisci `256M` con quello che è appropriato per le tue circostanze.

L'indicizzatore da riga di comando utilizza gli stessi parametri dell'indicizzatore sulla pagina di Ricerca Intelligente: Contenuto Indicizzato. Puoi modificare i parametri utilizzando il pulsante della barra degli strumenti Opzioni su quella pagina. Nota che sia il campo **Dimensione Batch Indicizzatore** sia il campo **Limite Tabella Memoria** influenzano la quantità di memoria utilizzata dall'indicizzatore.

*Tradotto da openai.com*

