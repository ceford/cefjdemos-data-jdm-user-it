<!-- Filename: J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update / Display title: Struttura della Tabella del Database   -->

## Errori Segnalati

Quando si aggiorna Joomla!, la struttura delle tabelle del database deve essere aggiornata prima che il processo possa iniziare. Il *Controllo Pre-Aggiornamento per Joomla* segnala un problema se non è così.

Tuttavia, quando si accede a **Sistema → Manutenzione → Database**, non è disponibile alcuna voce. Ciò è stato segnalato in diverse versioni di Joomla! 4.x.

## Qual è la Causa

Il problema è causato da una tabella `#__schemas` vuota nel database. Molto
probabilmente ciò accade quando l'istanza di Joomla! non è installata con
l'installatore ufficiale di Joomla!, ma tramite uno script personalizzato che
non ha inserito tutti i dati richiesti.

## Come Risolvere

Puoi risolvere questo problema aggiungendo il valore mancante alla tabella. Usando phpMyAdmin (o un altro client di database), vai alla tabella `#__extensions`. Cerca `name='files_joomla'` e annota l' `extension_id` (nel nostro caso *211*).

Successivamente, devi conoscere l'ultimo script SQL installato. Vai su `administrator/components/com_admin/sql/updates/mysql` e trova il nome del file con la versione più alta. In questo esempio, supponiamo che *4.0.3-2021-09-05.sql* sia il nome del file con la versione più alta. Ora devi aggiungerlo nella tua query di inserimento come secondo valore:

```sql
INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES (211, '4.0.3-2021-09-05');
```

o per PostgreSQL:

```sql
INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES (211, '4.0.3-2021-09-05');
```

Sostituisci `#__` con il prefisso del tuo database prima di eseguire le istruzioni.

Poi, dal menu dell'Amministratore, vai su **Sistema → Manutenzione → Database** e correggi le tabelle.

Ora l'aggiornamento dovrebbe funzionare come previsto.

