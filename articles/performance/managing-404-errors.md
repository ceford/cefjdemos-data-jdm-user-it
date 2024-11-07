<!-- Filename: Managing_404_Errors / Display title: Gestione degli errori 404 -->

## Perché i 404 Not Found Sono Importanti

Il problema più comune per i siti web che faticano nei posizionamenti sui motori di ricerca è il numero di errori 'non trovati', comunemente chiamati errori *404* perché questo è il codice di stato restituito se la pagina non può essere trovata.

In primo luogo, ci sono motivi legittimi per avere errori 404 – se hai una pagina per un evento che è passato, o un servizio che non fornisci più. In questi casi, alla fine la pagina verrà rimossa dall'indice dei motori di ricerca e non sarà più associata al tuo sito.

Il problema si verifica se hai molti errori 404 – ad esempio se annulli la pubblicazione di una categoria che conteneva centinaia di articoli. Dal punto di vista del motore di ricerca, questa non è una grande esperienza per i loro visitatori, perché approdano sul tuo sito e l'informazione che il motore di ricerca aveva detto loro fosse presente, non lo è. Questo è il motivo per cui non è una grande idea avere troppi errori 404 sul tuo sito.

## Google Search Central

Il primo passo è scoprire quanti ne hai – cosa che può essere fatta utilizzando [Search Central di Google](https://developers.google.com/search). Si tratta di un insieme gratuito di strumenti che ti consente di analizzare il tuo sito web e individuare rapidamente problemi, errori e questioni. È consigliabile registrare ogni sito che gestisci su Search Central per assicurarti di essere notificato in caso di problemi.

Quando visiti Search Central, c'è una sezione che ti mostra gli errori URL nell'elenco di ricerca – questa sezione ti mostrerà un elenco degli errori 404 che Google ha trovato sul tuo sito e un grafico che mostra come è cambiato nel tempo. Se il grafico inizia a salire, cerca di capire perché ci sono pagine che erano presenti sul tuo sito e ora non possono essere trovate.

Se c'era un problema temporaneo sul tuo sito, puoi contrassegnare gli errori come risolti.

![strumenti per webmaster](../../../en/images/performance/404-discovery.png)

## Risoluzione dei Problemi

La scoperta è solo una parte del processo. Una volta scoperti gli URL problematici, fai qualcosa al riguardo (se hanno bisogno di essere corretti!) reindirizzando la pagina a un'altra sul sito, ripristinando la pagina originale o esaminando cosa ha causato l'errore 404.

Se hai bisogno di reindirizzare una pagina, puoi utilizzare il plugin System - Redirect per raccogliere le pagine mancanti e il componente System / Redirects per reindirizzare le pagine mancanti a pagine esistenti.

## Problemi di Monitoraggio

Se desideri monitorare il tuo traffico 404, il modo migliore per farlo in Analytics è osservare cosa accade quando si verifica un errore 404. Nella maggior parte dei casi, il titolo della pagina cambia in 404 – quindi possiamo creare un segmento personalizzato che filtrerà il traffico con un titolo 404 e ti indicherà quale sia la pagina di destinazione. Ciò dovrebbe consentirti di monitorare e gestire proattivamente i tuoi errori 404 assicurandoti che i visitatori del tuo sito non finiscano su link non funzionanti.

![Avvisi Analytics per traffico 404](../../../en/images/performance/404-analytics-alerts.png)

![Panoramica del pubblico degli avvisi Analytics](../../../en/images/performance/404-analytics-alerts-2.png)

Google offre anche la possibilità, in Analytics, di impostare avvisi. Gli avvisi ti permettono di ricevere un'email quando si verificano determinati eventi. In questo caso, possiamo impostare un avviso per essere notificati se c'è un aumento di oltre il 5% nel numero di errori 404 in un periodo settimanale – il che potrebbe significare che ci sia un problema con il sito web che necessita di essere investigato.

Questo è un ottimo modo per restare aggiornato anche se non hai effettuato l'accesso per controllare la tua dashboard!

![Email degli avvisi Analytics](../../../en/images/performance/404-analytics-alerts-email.png)

## Monitoraggio degli Errori con una Dashboard

Esiste anche una dashboard che puoi installare chiamata *Data Integrity Dashboard* che ti mostra informazioni sugli errori 404, insieme ad alcune altre metriche che potrebbero essere di interesse. Basta cercare nella Google Analytics Gallery il *Data Integrity Dashboard* e selezionare sotto quale profilo installarlo.

![Integrità dei dati](../../../en/images/performance/404-data-integrity.png)

*Tradotto da openai.com*

