<!-- Filename: J4.x:Article_Preview / Display title: Articolo: Anteprima   -->

## Introduzione

Può essere utile visualizzare un'anteprima di un articolo prima di pubblicarlo. A tal fine, c'è un pulsante di *Anteprima* nella barra degli strumenti del modulo *Articolo: Modifica* nel backend. Tuttavia, questa funzione utilizza l'articolo salvato e non il contenuto del modulo dell'editor. La funzione di anteprima non è disponibile nel modulo di modifica degli articoli nel frontend.

Potresti non voler rendere visibile un articolo finché non è completato. A tal fine, sono necessarie strategie diverse per gli editor nel frontend e nel backend.

## Anteprima Frontend

L'unico modo per mantenere un articolo semi-privato dal frontend è impostare
il suo Accesso su *Registrato*, in modo che solo gli utenti connessi possano vederlo.

- Accedi al frontend del sito web.
- Seleziona il link *Modifica* per un articolo da aggiornare. Oppure...
- Seleziona il pulsante *Nuovo Articolo* sotto i layout del blog.
  - Imposta il livello di Accesso dell'articolo su *Registrato* fino a quando non è pronto per la pubblicazione.
  - Puoi aggiungere un avviso *Alert* che indica che l'articolo è in costruzione: `<div class="alert alert-warning">In Costruzione</div>`.
- *Salva & Chiudi* per vedere l'articolo.

## Anteprima del Backend

Dopo aver effettuato l'accesso all'interfaccia Amministratore:

- Seleziona un articolo da modificare o crea e salva uno nuovo.
- Per mantenere privato un nuovo articolo per ora, imposta lo Stato su *Non pubblicato* oppure lascialo su *Pubblicato* e regola la data di *Inizio pubblicazione*.
- Apporta modifiche e *Salva* l'articolo.
- Seleziona il pulsante *Anteprima* nella Barra degli Strumenti. Dovrebbe apparire una finestra di Anteprima popup.
- Se ricevi il messaggio *La pagina richiesta non può essere trovata*, accedi al Frontend e riprova.
- Per chiudere la finestra di Anteprima, seleziona il pulsante *X* nell'angolo in alto a destra.

![La finestra di anteprima](../../../en/images/getting-started/article-edit-preview.png)

*Tradotto da openai.com*

