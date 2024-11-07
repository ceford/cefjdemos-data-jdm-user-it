<!-- Filename: jdocmanual?manual=user&heading=performance&filename=page-analysis.md / Display title: Analisi della Pagina -->

## Faro

> Faro è uno strumento open-source e automatizzato per migliorare la qualità delle pagine web. Puoi eseguirlo su qualsiasi pagina web, sia pubblica che richiede autenticazione. Offre audit per le prestazioni, l'accessibilità, le applicazioni web progressive, la SEO e altro ancora.

È disponibile come strumento aggiuntivo per Google Chrome e Firefox e può essere eseguito dalla riga di comando. Questo è utile per testare su un ambiente di sviluppo locale.

Ulteriori informazioni sono disponibili sul sito web di Chrome for Developers: Faro.

Puoi utilizzare lo strumento online da questo sito di PageSpeed Insights.

Lo screenshot seguente mostra la prima parte del report di PageSpeed Insights:

![Report di PageSpeed Insights](../../../en/images/performance/performance-pagespeed-insights.png "Report di PageSpeed Insights")

## Miglioramenti delle Prestazioni

La seconda parte del rapporto suggerisce metodi per migliorare le prestazioni:

* **Eliminare le risorse che bloccano il rendering** - Risparmio potenziale di 540 ms. Francamente, è troppo lavoro per troppo poco guadagno.
* **Abilitare la compressione del testo** - Risparmio potenziale di 11 KiB. Nella Configurazione Globale, pannello Server, impostare Compressione Pagina GZip su *Sì*. Restano ancora piccoli file JavaScript e CSS da minimizzare e comprimere.
* **Ridurre CSS non utilizzato** - Risparmio potenziale di 62 KiB. I responsabili sono template.min.css e joomla-fontawesome.min.css, ma ciò implica adattare il CSS per ogni pagina del sito, il che è un lavoro soggetto a errori eccessivo per un guadagno troppo limitato.
* **Servire asset statici con una politica di caching efficiente** - Trovate 21 risorse. Sono fornite referenze, incluse quelle specifiche di Joomla.

Il messaggio complessivo è che alcune proposte valgono la pena di essere affrontate, mentre altre no.

## Rapporto Mobile vs Desktop

Il rapporto Desktop di solito differisce dal rapporto Mobile. Alcuni problemi aggiuntivi identificati in questo caso:

* **Dimensiona correttamente le immagini** - Risparmio potenziale di 48 KiB. Il tag dell'immagine è effettivamente ottimizzato con immagini webp di larghezza 768 e 1200 pixel. Sembra che sia necessario qualcosa di intermedio.

## Accessibilità

* **I link non hanno un nome distinguibile** Questo si riferisce alle frecce Sinistra e Destra nella parte inferiore della pagina che navigano avanti o indietro. Il testo è stato omesso per evitare problemi di traduzione. Bisogna rifletterci di nuovo!
* **I bersagli touch non hanno dimensioni o spaziatura sufficienti** Questo si riferisce alle dimensioni degli elementi del menu nelle colonne sinistra e destra. Hanno bisogno di più spazio verticale - è necessario un aggiustamento CSS.

## Best Practice e SEO

Anche se entrambi hanno ottenuto 100 per Mobile e Desktop, devono essere ricontrollati dopo ogni modifica del design.

## Sommario

Tutti i problemi in questo sito sono stati risolti, tranne lo smantellamento dei file CSS e la minificazione dei piccoli file Javascript e CSS componenti.
*Tradotto da openai.com*

