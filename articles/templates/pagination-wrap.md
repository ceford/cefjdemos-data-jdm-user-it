<!--
{
    "source": "https://jdocmanual.org/jdocmanual?article=user/templates/pagination-wrap",
    "title": "A capo per la paginazione",
    "description": "Scopri un metodo semplice per disporre su pi\u00f9 righe l\u2019elenco della paginazione sugli schermi stretti. ",
    "author": ""
}
-->

In Joomla, gli elenchi di articoli, utenti e altri elementi possono essere molto lunghi, quindi vengono visualizzati in gruppi, 20 per impostazione predefinita. 

## La normale barra di paginazione

Per spostarsi tra i gruppi è presente una barra di paginazione sotto l’elenco degli elementi, che consente all’utente di selezionare il gruppo successivo di elementi, come illustrato in questa immagine:

![la normale barra di paginazione dell’elenco](../../../en/images/templates/pagination-wrap/01-pagination-wide-screen.png)

## Paginazione su schermi stretti

La barra di paginazione funziona bene sugli schermi larghi. Tuttavia, sugli schermi stretti la barra di paginazione potrebbe essere più larga dello schermo. Ciò comporta la necessità di scorrere verso destra per trovare altri elementi nella pagina, come le icone dei menu hamburger.

![la barra di paginazione su uno schermo stretto](../../../en/images/templates/pagination-wrap/02-pagination-narrow-screen.png)

Nell'illustrazione sopra, tutti gli elementi nell'area grigia a destra sono inizialmente *fuori dallo schermo* e probabilmente verranno ignorati. L'utente deve scorrere verso destra per visualizzarli. In questo caso, gli elementi fuori dallo schermo sono l'icona della barra degli strumenti in alto a destra e l'icona del menu in basso a destra.

## Correzione con override di un template

Questa correzione aggiunge una classe *flex-wrap* al codice che genera la barra di paginazione.

- Nel backend, vai a Sistema > Template amministratore > Dettagli e file di Atum
- Facoltativamente, seleziona html > layouts per vedere cosa contiene
- Seleziona la scheda **Crea override**
- Nel riquadro Layouts seleziona **joomla** e poi **pagination**
- Nella scheda Editor seleziona html > layouts > joomla > pagination > **links.php**
- Trova la riga 70 contenente `<ul class="pagination ms-auto me-0">`
- Aggiungi `flex-wrap` all’elenco delle classi: `<ul class="pagination ms-auto me-0 flex-wrap">`
- **Salva e chiudi**
- Facoltativo: puoi eliminare /html/layouts/joomla/pagination/link.php e /html/layouts/joomla/pagination/links.php

Osserva il risultato sia su schermi larghi sia su schermi stretti. Ora lo schermo stretto mostra l’icona della barra degli strumenti e l’icona del menu nella larghezza normale dello schermo:

![la barra di paginazione modificata su uno schermo stretto](../../../en/images/templates/pagination-wrap/02-modified-pagination-narrow-screen.png)

Per il modello del sito, segui queste istruzioni ma crea un override nel modello Cassiopeia.

*Tradotto da openai.com*