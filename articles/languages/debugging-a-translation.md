<!-- Filename: Debugging_a_translation / Display title: Debugging di una Traduzione  -->

## File di Lingua di Joomla

Ogni volta che del testo deve essere visualizzato sullo schermo, i programmatori di Joomla inseriscono una costante di lingua come JYES o JNO. Durante il processo di rendering, vengono caricati i file di lingua con traduzioni nella lingua appropriata. I file di lingua terminano tutti con `.ini`. Puoi guardare in languages/en-GB/joomla.ini per alcuni esempi di base. Le righe che iniziano con un punto e virgola sono ignorate e possono essere utilizzate per i commenti. Le righe rimanenti consistono in coppie chiave="valore". Ogni lingua ha lo stesso set di chiavi, ma i valori sono le traduzioni appropriate.

Ogni estensione di Joomla ha i propri file di lingua, quindi ce ne sono centinaia in totale. A volte, ci sono problemi come costanti di lingua mancanti, costanti di lingua scritte male o errori di sintassi nelle stringhe di traduzione che possono rendere non valido un intero file di lingua.

## Modalità di Debug

Joomla offre alcuni utili meccanismi di debug che possono facilitare l'individuazione di stringhe non tradotte e la diagnosi di problemi con traduzioni linguistiche nelle estensioni installate. Per provarli:

Dal Dashboard Principale:

* Seleziona il pulsante **Configurazione Globale** nel pannello *Sistema*.
* Seleziona il pannello *Sistema* e imposta **Debug Lingua** su **Sì**.
* **Visualizzazione della lingua** è normalmente impostata su **Valore**. Se impostata su **Costante**, il layout viene disturbato da lunghe costanti che non si adattano.

Con la Modalità di Debug Lingua attiva, tutti i valori traducibili vengono mostrati circondati da caratteri speciali che indicano il loro stato:

* `**Joomla CMS**` Il testo circondato da due asterischi indica che è stata trovata una corrispondenza in un file di lingua e la costante è stata tradotta.
* `??Joomla CMS??` Il testo circondato da coppie di punti interrogativi indica che la costante è traducibile, ma non è stata trovata alcuna corrispondenza in un file di lingua.
* `Joomla CMS` Il testo senza caratteri circostanti indica che il valore non è traducibile.

## Debug Sistema

Informazioni aggiuntive sul debug della lingua possono essere ottenute attivando il debug del sistema.

Dal cruscotto principale:

* Seleziona **Plugin** e poi trova e attiva il plugin **Sistema - Debug**.
* Seleziona di nuovo il cruscotto principale e poi...
* Seleziona il pulsante **Configurazione Globale**.
* Seleziona il pannello *Sistema* e imposta **Debug Sistema** su **Sì**.

Con **Debug Sistema** attivo, tutte le schermate presentano informazioni di debug aggiuntive nella parte inferiore di ogni pagina. Possono essere espanse da un'icona Joomla e il bordo superiore può essere trascinato verticalmente per mostrare più righe.

Le informazioni di debug sono suddivise in diverse intestazioni:

* **J! Info** Informazioni di base sull'installazione.
* **Richiesta** Campi di richiesta del server.
* **Sessione** Informazioni sulla sessione.
* **Profilo** Il tempo impiegato per eseguire il codice fino a vari punti di riferimento nel codice.
* **Query** Le query SQL eseguite nel processo di costruzione della pagina.
* **Caricate.** Un elenco di tutti i file di lingua caricati nel processo di costruzione della pagina, inclusa l'informazione completa sul percorso. Questo può essere utile per verificare che i file previsti siano stati caricati.
* **Non tradotte** Un elenco di tutte le costanti non tradotte trovate e la probabile posizione del file dato il punto in cui è stata fatta la chiamata di traduzione.
* **Errori**

## Sistema - Plugin di Debug

Questo plugin di sistema controlla cosa viene visualizzato quando il debug è attivato nella **Configurazione Globale**. Ci sono tre impostazioni di interesse per i traduttori.

Nella scheda **Lingua**:

![plugin sistema debug](../../../en/images/languages/languages-debug-plugin.png)

* **Errori nel Parsing dei File di Lingua** Visualizza un errore se un file di lingua non viene caricato correttamente.

- **File di Lingua**. Se impostato su *Mostra*, allora ...
- **Stringhe di Lingua** Se impostato su *Mostra*, allora ...
- **Rimuovi Prima Parola**.
- **Rimuovi Dall'Inizio**.
- **Rimuovi Dalla Fine**.

**La seguente spiegazione necessita di revisione!**

Nota che le stringhe non tradotte mostreranno solo il valore passato al metodo **Text** appropriato. Per esempio, con il seguente codice:

    echo Text::_( 'Reports Import Configuration' );

Se non tradotto verrà visualizzato come:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Se il prefisso della chiave da rimuovere è impostato su "Reports", allora la visualizzazione cambierebbe leggermente in:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Nota che il percorso mostrato è solo una stima basata su una chiamata alla funzione PHP *debug_backtrace*. A volte è preciso, altre volte non lo è e ci sono anche casi in cui non è stato possibile determinare alcun file. In quei casi devi usare il tuo miglior giudizio.

*Tradotto da openai.com*  

