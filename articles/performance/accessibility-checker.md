<!-- Filename: jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md / Display title: Verifica dell'accessibilità   -->

## Sistema - Verificatore di Accessibilità Joomla

Questo è un plugin di base che può essere utilizzato per verificare l'accessibilità durante la creazione di contenuti degli articoli. Il seguente screenshot mostra alcune impostazioni del plugin:

![Impostazioni del modulo del plugin](../../../en/images/performance/performance-jooa11y-plugin-form.png "Impostazioni del Plugin")

Con l'opzione **Mostra Sempre** impostata su *On*, l'icona del report appare su ogni pagina del sito. Questo è utile per lo sviluppo, ma non dovrebbe mai essere lasciato attivo per un sito pubblico. Impostalo su **Off**!

Con l'opzione *Mostra Sempre* impostata su *On*, ogni pagina del sito ha un'icona in basso a destra con un conteggio del numero di problemi. Il seguente screenshot mostra l'icona selezionata per visualizzare un pannello di informazioni. Include una Struttura della Pagina, commenti di Leggibilità e Avvertimenti, che possono essere selezionati uno per uno. È stato selezionato il primo problema.

![Verifica dell'accessibilità del sito](../../../en/images/performance/performance-jooa11y-site-display.png "Verifica dell'accessibilità del sito")

Il modulo *Articoli: Modifica* dispone di un pulsante **Verifica Accessibilità** nella Barra degli Strumenti. Mostra la verifica per un singolo articolo in una finestra popup:

![Verifica dell'accessibilità dell'editor](../../../en/images/performance/performance-jooa11y-admin-display.png "Verifica dell'accessibilità dell'editor")

## Risoluzione dei problemi

Il Accessibility Checker è uno strumento per identificare i problemi. Non corregge i problemi. Questo spetta a te. Il checker ha alcune impostazioni che puoi attivare/disattivare secondo necessità. Queste includono Contrasto, Etichette dei Moduli, Link (Avanzato) AAA, Leggibilità AAA, Modalità Scura e Filtro Colore con simulazione di quattro tipi di visione dei colori difettosa.

Per maggiori informazioni, vedi la Panoramica di Sa11y

Ad esempio, sulla Leggibilità, dice:

> Sa11y può stimare il punteggio di leggibilità di tutti i paragrafi e contenuti delle liste. Un buon punteggio di leggibilità è un'indicazione che il tuo testo è comprensibile e facile da digerire. Si basa sulla lunghezza media delle frasi e delle parole nella tua pagina, utilizzando una formula nota come test di facilità di lettura di Flesch (Wikipedia). Un "buon" punteggio di lettura è tra 60 e 100. A volte può essere difficile ottenere un buon punteggio di leggibilità. La maggior parte delle tue pagine potrebbe indicare "difficile". Ricorda che questa funzione è utilizzata solo per stimare la leggibilità del tuo contenuto. Deve essere utilizzata solo come riferimento e non come indicazione di conformità. Sa11y calcola il punteggio di leggibilità basandosi su tutti i contenuti dei paragrafi (tag `<p>`) e delle liste (tag `<li>`). Un punteggio basso non influisce sullo stato di passaggio o fallimento di Sa11y.

