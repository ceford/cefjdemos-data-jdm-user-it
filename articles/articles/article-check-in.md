<!-- Filename: J4.x:Article_Check-out_and_Check-in / Display title: Articolo: Check-in   -->

## Introduzione

Molti siti Joomla hanno più utenti che hanno il permesso di modificare gli articoli. Per evitare che due utenti provino a modificare lo stesso articolo nello stesso momento, ogni articolo ha un campo nel database chiamato **checked_out** per indicare se è in uso o meno. Questo campo viene impostato quando un articolo viene aperto per la modifica e viene disattivato quando il modulo di modifica viene chiuso utilizzando i pulsanti *Salva & Chiudi* o *Chiudi*.

A volte un modulo di modifica di un articolo non viene chiuso correttamente, ad esempio, utilizzando il pulsante indietro del browser o se la sessione utente scade. In questo caso, il campo checked_out rimane impostato. Questo viene indicato nelle liste degli articoli con una piccola icona a forma di lucchetto. L'icona del lucchetto è visibile anche dove dovrebbe esserci un link di modifica quando si è effettuato l'accesso al frontend del sito.

Per ripristinare il normale funzionamento, gli articoli bloccati devono essere sbloccati.

## Registrazione Articolo

Esistono diversi metodi per registrare un articolo.

- Se sei stata l'ultima persona a modificare l'articolo, puoi modificarlo dal backend o frontend senza bisogno di registrarlo.
- Contatta l'ultima persona che ha modificato l'articolo per vedere se ha finito. Puoi passare il cursore sopra il lucchetto e il suggerimento popup visualizzerà il nome dell'utente che ha bloccato l'articolo.
- Se sei un Super User o un Amministratore, puoi selezionare l'icona del lucchetto per registrare questo elemento.
- Puoi anche selezionare diversi articoli e utilizzare l'opzione *Check-in* dal pulsante *Azioni* nella Barra degli Strumenti.
- Se non puoi registrare l'elemento tu stesso, chiedi a un Super User o a un Amministratore di farlo.

## Check-in Globale

Se sei un Super Utente o Amministratore, puoi utilizzare l'utilità di Check-in Globale per selezionare gli elementi da registrare.

Questa utilità deve essere utilizzata con molta cautela, specialmente in ambienti multi-utente. Registra tutti gli elementi precedentemente estratti, indipendentemente da chi li ha estratti. Potrebbero verificarsi effetti collaterali indesiderati, come il fatto che più editori finiscano per lavorare sullo stesso documento. In questo caso, chiunque clicchi per ultimo sul pulsante di salvataggio avrà la propria versione salvata come copia finale.

Devi anche essere consapevole che molte altre estensioni hanno campi **checked_out**. Ad esempio, i moduli e le categorie possono essere estratti per la modifica e lasciati accidentalmente in quello stato.

Dal menu Amministratore:

- Seleziona **Cruscotto Home → Check-in Globale** o
  **Sistema → Pannello di Manutenzione → Check-in Globale**.
- L'elenco mostra il numero di elementi estratti.

![Pagina di check-in globale](../../../en/images/articles/global-checkin.png)

- Dall'elenco delle tabelle del database seleziona la casella di controllo per il tipo di elemento da registrare.
- Seleziona *Check-in* dalla Toolbar.

Tutti gli elementi estratti in quella tabella verranno registrati.

## Tabelle con campo checked_out

Puoi scoprire quali tabelle hanno una colonna checked_out con questa query utilizzata in phpMyAdmin:

```sql
SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('checked_out') AND TABLE_SCHEMA='j423sd';
```

E il risultato dovrebbe essere simile a questo:

```
TABLE_NAME
bi2hb_banner_clients
bi2hb_banners
bi2hb_categories
bi2hb_contact_details
bi2hb_content
bi2hb_extensions
bi2hb_fields
bi2hb_fields_groups
bi2hb_finder_filters
bi2hb_menu
bi2hb_modules
bi2hb_newsfeeds
bi2hb_scheduler_tasks
bi2hb_tags
bi2hb_update_sites
bi2hb_user_notes
bi2hb_workflow_stages
bi2hb_workflow_transitions
bi2hb_workflows
```

*Tradotto da openai.com*

