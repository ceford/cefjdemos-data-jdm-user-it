<!-- Filename: Help4.x:Components_Version_History / Display title: Articolo: Versioni  -->

## Introduzione

Nel modulo di modifica degli articoli di Joomla, ogni volta che un articolo viene salvato, viene creata automaticamente una nuova versione. Il numero di versioni da mantenere per ogni articolo può essere impostato nella pagina delle *Opzioni Articolo*, scheda *Layout di modifica*. L'impostazione predefinita è 10. Nota che questa non è la scheda *Opzioni* della pagina di *Modifica Articoli*. La versione attuale è generalmente l'ultima versione salvata.

Una o più versioni possono essere contrassegnate per *Mantenere per Sempre*. Tali versioni non verranno eliminate automaticamente, anche se viene superato il numero massimo di versioni.

La finestra di dialogo popup *Versioni* è utilizzata per gestire le versioni precedenti dell'elemento in fase di modifica. Storici delle versioni simili sono disponibili per Articoli, Banner e Clienti, Contatti, Feed di notizie, Note Utente e tutte le Categorie.

Nota: I campi personalizzati non sono memorizzati in versioni diverse.

## Come Accedere

Seleziona il pulsante **Versioni** sulla barra degli strumenti mentre modifichi l'elemento.

## Screenshot

![Finestra di dialogo delle versioni](../../../en/images/articles/articles-versions.png)

## Intestazioni di Colonna

- **Casella di Controllo** Questa casella di controllo viene utilizzata per selezionare o deselezionare tutte le versioni visibili nell'elenco. Se una qualsiasi casella di controllo è selezionata, i pulsanti della barra degli strumenti vengono attivati e possono essere usati per eseguire un'azione sugli elementi selezionati.
- **Data** L'ora e la data in cui la versione è stata salvata. Facendo clic su questo link si apre un'anteprima di quella versione in una finestra pop-up. Si noti che una delle date sarà seguita da un simbolo di stella. Questo indica che questa è la versione attualmente salvata e in fase di modifica.
- **Nota Versione** Quando modifichi un elemento, hai la possibilità di inserire una Nota Versione. Questo può essere utilizzato per aiutarti a ricordare quale versione contiene quali informazioni. Se hai inserito una Nota Versione prima di salvare l'elemento, verrà mostrata in questa colonna.
- **Conserva per Sempre** Questa colonna mostra se hai contrassegnato la versione come Conserva per Sempre. Normalmente, ogni versione verrà conservata secondo le impostazioni nella pagina delle opzioni del componente. Le impostazioni predefinite sono di mantenere un massimo di 10 versioni precedenti per un elemento. In questo caso, quando salvi un elemento che ha già 10 versioni salvate, la versione più antica viene eliminata. Se una versione è contrassegnata come Conserva per Sempre, non sarà conteggiata come una delle versioni salvate e non sarà eliminata quando si raggiunge il numero massimo. Per attivare o disattivare Conserva per Sempre, seleziona la casella di controllo della versione e poi seleziona il pulsante *Keep On/Off* nella barra degli strumenti.
- **Autore** L'utente che ha salvato questa versione.
- **Conteggio Caratteri** Il numero totale di caratteri salvati in questa versione. Questo include i nomi delle colonne del database così come i caratteri dell'elemento.

## Barra degli strumenti

In cima alla pagina, vedrai la barra degli strumenti mostrata nello screenshot sopra. Le funzioni sono:

- **Ripristina** La versione attuale dell'elemento è contrassegnata con una stella a destra della data. Se desideri ripristinare una delle altre versioni salvate, seleziona la casella di controllo per la versione desiderata e clicca sul pulsante *Ripristina*. La versione attuale dell'elemento verrà sostituita con la versione selezionata e lo schermo di modifica si ricaricherà con la versione ripristinata caricata nell'editor.
- **Anteprima** Per visualizzare in anteprima una versione, seleziona l'elemento nella colonna Data oppure spunta la casella di controllo e clicca sul pulsante Anteprima. Una finestra del browser separata si caricherà mostrando la versione selezionata dell'elemento, simile allo screenshot qui sotto. Dopo aver visualizzato la versione, chiudi la finestra del browser.
![Dialogo di anteprima delle versioni](../../../en/images/articles/articles-versions-preview.png)
- **Confronta** Per confrontare due versioni per vedere cosa è stato cambiato, seleziona le caselle di controllo per ciascuna delle versioni e clicca sul pulsante Confronta. Si aprirà una nuova finestra del browser, come mostrato nello screenshot qui sotto. La prima colonna è il nome del campo, la seconda è la versione più vecchia, la terza è la versione più recente e l'ultima colonna evidenzia le differenze tra le due versioni.
![Dialogo di confronto delle versioni](../../../en/images/articles/articles-versions-compare.png)
- **Blocco On/Off** Questo pulsante ti consente di attivare o disattivare la funzione di Conserva per Sempre per una versione. Normalmente, la versione più vecchia di un elemento verrà eliminata automaticamente quando il numero massimo di versioni (impostato nelle Opzioni per il componente) sarà stato superato. Se imposti la proprietà Conserva per Sempre per una versione, non verrà mai eliminata automaticamente.
- **Elimina** Questo pulsante ti consente di eliminare manualmente una o più versioni. Seleziona la casella di controllo per le versioni che desideri eliminare e poi clicca sul pulsante Elimina. Tieni presente che questo *non* elimina l'elemento in fase di modifica. Cancella solo la versione selezionata dell'elemento.

*Tradotto da openai.com*

