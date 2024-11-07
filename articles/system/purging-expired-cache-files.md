<!-- Filename: Purging_expired_cache_files / Display title: Purgare la cache scaduta  -->

## File di Cache

I file di cache sono file temporanei creati per migliorare le prestazioni del tuo sito. È necessario assicurarsi che i file di cache scaduti, che quindi non sono più necessari, vengano rimossi dal sistema. Altrimenti, alla fine esaurirai lo spazio su disco.

I file di cache scaduti possono essere eliminati dall'interfaccia dell'Amministratore o dall'interfaccia della Linea di Comando (CLI).

## Purge - Metodo dell'Amministratore

Dalla *Dashboard Principale*
* Seleziona l'opzione **Cache** nel pannello *Sistema*.
* Nella pagina *Manutenzione: Cancella Cache* seleziona il pulsante **Cancella Cache Scaduta** nella Barra degli Strumenti.

## Purge - Metodo da Linea di Comando

Apri una finestra del terminale e naviga nella directory cli nella radice del tuo sito.
Se non sai quali comandi CLI sono disponibili, esegui il seguente comando:
```bash
php joomla.php
```
Vedrai un elenco dei comandi disponibili. Il comando `cache` è:
```bash
php joomla.php cache:clean
```
Dovrebbe apparire un messaggio di conferma verde o forse un messaggio di errore color marrone scuro.

## Pulizia Automatica dei File di Cache Scaduti

Puoi pulire automaticamente i file di cache scaduti utilizzando un cron job. I servizi di hosting rendono questo facile fornendo un modulo per selezionare con quale frequenza eseguire un job e il comando da utilizzare. Quindi potresti scegliere di impostare il cron per girare alle 05:00 ogni giorno con il seguente comando:
```
 /usr/local/bin/ea-php82 /home/username/public_html/cli/joomla.php cache:clean
```
La maggior parte dei gestori di job *cron* ti permette di inserire un indirizzo email a cui verrà inviato l'output del cron. Se non vuoi ricevere un messaggio, aggiungi ` > /dev/null 2>&1` al comando.

La versione di PHP utilizzata nella riga di comando è spesso diversa da quella usata per la consegna di un sito web. Potrebbe non essere compatibile con Joomla. Quindi utilizza il percorso completo alla versione di PHP che desideri usare anziché `php` da solo.

*Tradotto da openai.com*

