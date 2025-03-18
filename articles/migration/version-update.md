<!-- Filename: J4.x:Updating_from_an_existing_version / Display title: Aggiornamento della Versione  -->

## Introduzione

**Ricorda: esegui sempre un backup del tuo sito prima di effettuare aggiornamenti.**

Il metodo consigliato per aggiornare le installazioni di Joomla! è utilizzare il *Componente Aggiornamento Joomla*.

Un'installazione standard di Joomla 4 e successivi include un utile pannello di notifiche nella Dashboard principale dopo il login. Puoi vedere a colpo d'occhio se è disponibile un aggiornamento e il numero di versione.

Il messaggio di aggiornamento che appare nel pannello delle Notifiche dipende dal *Canale di Aggiornamento* impostato nella pagina *Opzioni di Aggiornamento Joomla* e dalla versione *Minore* corrente. Con il **Canale di Aggiornamento** impostato su **Predefinito**, vengono notificati gli aggiornamenti all'interno della versione *Maggiore* corrente. Con il parametro impostato su *Joomla Next*, puoi aggiornare all'ultima versione corrente e quindi selezionare il pulsante **Controlla aggiornamenti** per vedere se è disponibile la prossima versione *Maggiore*.

Sebbene Joomla ti notificherà quando un aggiornamento è disponibile, richiede che tu esegua l'aggiornamento. È un processo semplice che dovrebbe essere eseguito quanto prima per mantenere il sito aggiornato.

## Accesso al Componente di Aggiornamento

Se il pannello delle notifiche è visualizzato nella Dashboard principale, seleziona il pulsante **x.y.z Disponibile - Aggiorna ora!** per accedere al Componente di Aggiornamento.

![notifica di aggiornamento joomla nella home dashboard](../../../en/images/migration/version-update-notification-home-dashboard.png)

In alternativa, per accedere al Componente di Aggiornamento dal menu Amministratore, seleziona **Sistema** per andare tramite la **Dashboard di Sistema**.

![notifica di aggiornamento joomla nella dashboard di sistema](../../../en/images/migration/version-update-notification-system-dashboard.png)

La Dashboard di Sistema ha un *Pannello di Aggiornamento* che include un link a Joomla che mostrerà il numero di versione dell'aggiornamento disponibile. Seleziona il link **Joomla** per andare al Componente di Aggiornamento.

## Esecuzione dell'Aggiornamento

Joomla! 4 e 5 forniscono un Controllo Pre-Aggiornamento per gli Aggiornamenti a Versioni Minori. Questa visualizzazione del componente Aggiornamento di Joomla mostra le specifiche tecniche del server su cui si trova il sito e le estensioni core e di terze parti che utilizzano il Server di Aggiornamento sotto forma di elenco.

**Nota:** La schermata del *Controllo Pre-Aggiornamento* non viene visualizzata se il sito si trova sulla versione **Minore** corrente.

![controllo pre aggiornamento joomla](../../../en/images/migration/version-update-pre-update-check.png)

Presta molta attenzione ai risultati del controllo e agisci per risolvere eventuali problemi evidenziati prima di aggiornare. Potrebbe essere necessario aggiornare, disabilitare o disinstallare le estensioni incompatibili prima di aggiornare Joomla.

Non è raro vedere avvisi per le *Impostazioni Consigliate* poiché queste sono spesso specifiche del server e relative all'hosting. È probabile che esistessero quando hai installato Joomla e molto probabilmente non impediranno il completamento dell'aggiornamento.

*Nota il promemoria che ti consiglia vivamente di fare un backup se non l'hai già fatto!*

C'è un link sotto il pulsante di aggiornamento. Nella maggior parte dei casi puoi ignorare questo link. Fornisce un'opzione per caricare manualmente i file di aggiornamento se il tuo server è dietro un firewall o non è in grado di contattare i server di aggiornamento di Joomla.

Quando hai esaminato il Controllo Pre-Aggiornamento e sei soddisfatto, seleziona **Aggiorna**.

### Conferma dell'Aggiornamento

![pagina inizio aggiornamento](../../../en/images/migration/version-update-start-update.png)

Fai clic sulla casella di controllo per confermare di aver effettuato un backup e di aver verificato che le estensioni siano compatibili, dopodiché clicca su **Inizia Aggiornamento**.

### Avanzamento dell'Aggiornamento

![pagina avanzamento aggiornamento](../../../en/images/migration/version-update-progress.png)

Una volta iniziato l'aggiornamento, apparirà una barra di avanzamento mentre i file di Joomla vengono aggiornati.

### Completamento

![pagina completamento aggiornamento](../../../en/images/migration/version-update-completion.png)

Quando la barra di avanzamento raggiunge il 100%, un messaggio di sistema confermerà che il tuo sito è stato aggiornato e indicherà il numero di versione. Il numero di versione verrà aggiornato anche nella barra degli strumenti in alto, accanto al nome del sito.

Clicca sul pulsante **Indietro** e verrai reindirizzato al Componente di Aggiornamento di Joomla dove è possibile controllare nuovamente gli aggiornamenti.

## Controlli Post-Aggiornamento

Una volta completato l'aggiornamento, dovresti eseguire alcuni controlli per assicurarti che tutto sia andato come previsto, che non siano presenti errori e che non ci siano cambiamenti che richiedono ulteriori azioni.

### Controllo Frontend

Accedi al frontend del sito web e verifica che funzioni e si visualizzi come faceva prima dell'aggiornamento. Utilizza la combinazione *Shift + Ricarica* per forzare il browser a ricaricare eventuali modifiche ai fogli di stile e agli script.

### Controlli del Sistema

Dal menu laterale seleziona **Sistema** per accedere alla Dashboard di Sistema. Questa ti offre una panoramica dello stato attuale del tuo sito Joomla.

![dashboard di sistema post-aggiornamento](../../../en/images/migration/version-update-after-update.png)

In questo esempio, possiamo vedere che dall'aggiornamento ci sono due elementi che richiedono attenzione. Sono contrassegnati con un'etichetta che include un numero. Il numero si riferisce a quanti elementi richiedono attenzione. Facendo clic su ciascuno di essi, potrai risolverli.

**Nota**: La Dashboard di Sistema effettua un controllo ogni volta che la pagina viene caricata. Tieni presente che le impostazioni di caching del browser potrebbero influire su questo. È buona prassi cancellare la cache del browser quando si controlla usando *Shift + Ricarica*.

### Controllo del Database

Naviga su **Sistema → Manutenzione → Database**. Se il tuo database è aggiornato, dovresti vedere una schermata simile a quella qui sotto:

![controllo del database post-aggiornamento senza problemi](../../../en/images/migration/version-update-after-update-database-check-no-problems.png)

Se il tuo database non è aggiornato, vedrai una schermata che elenca i problemi trovati, simile a quella qui sotto:

![controllo del database post-aggiornamento con problemi](../../../en/images/migration/version-update-after-update-database-check-problems.png)

In questo caso, seleziona il *Nome* dell'estensione con problema e poi il pulsante "Aggiorna Struttura" nella Barra degli Strumenti. Joomla aggiornerà il tuo database per correggere i problemi elencati e poi ripresenterà la schermata. Se la correzione è stata eseguita con successo, la visualizzazione indicherà che il database è aggiornato.

**Nota:** Se persistono errori, assicurati che tutte le tabelle del database siano selezionate.

## Scoperta del Sistema

In alcuni casi, quando si aggiorna a una nuova versione di Joomla, vengono aggiunte nuove estensioni core. Se ci sono stati problemi con l'aggiornamento del database, queste estensioni potrebbero non essere state installate correttamente. Per verificare ciò, naviga su **Sistema → Scopri**. Quindi seleziona l'icona Scopri nella barra degli strumenti. Lo schermo dovrebbe apparire come segue:

![Schermata Scoprire Senza Estensioni Da Installare](../../../en/images/migration/version-update-after-update-discover.png)

Se è così, sai che tutte le nuove estensioni aggiunte durante l'aggiornamento sono state installate correttamente nel database.

Se ci sono estensioni non installate, appariranno simili alla seguente schermata:

![Schermata Scoprire Con Estensioni Trovate Da Installare](../../../en/images/migration/version-update-after-update-discover-found.png)

In questo caso, seleziona le caselle e clicca sull'icona Installa nella barra degli strumenti. Joomla installerà l'estensione/le estensioni e mostrerà successivamente la schermata in cui non vengono scoperte estensioni. A questo punto, le nuove estensioni sono state installate nel database.

## Risoluzione dei problemi

Se hai domande, problemi o errori prima, durante o dopo
l'aggiornamento, ti invitiamo a porli sul
[Forum "Migrating and Upgrading to Joomla! 4.x"](https://forum.joomla.org/viewforum.php?f=812).

Se riscontri problemi o errori durante il processo di aggiornamento, ecco alcuni
consigli.

- Cancella la cache del tuo browser. Potrebbero esserci state modifiche al CSS o
  al JavaScript che dovranno essere ricaricate dal tuo browser Web dopo un
  aggiornamento.
- Se compaiono messaggi di errore del database dopo l'aggiornamento, assicurati di controllare
  il link **Sistema → Pannello di manutenzione → Database**. In alcuni
  casi, se si verifica un errore nel database, impedirà l'esecuzione di tutti gli aggiornamenti
  del database. In questo caso, puoi eseguirli dal link del Database
  e poi utilizzare il metodo **Sistema → Installa → Scopri**
  per verificare e installare eventuali nuove estensioni.
- Il processo di aggiornamento crea o aggiunge un file di log denominato
administrator/logs/joomla_update.php che puoi aprire con un editor di testo per
vedere i passi registrati nel log. Mostrerà i passi principali (download del zip,
installazione, esecuzione delle istruzioni SQL, pulizia), qualcosa di simile a questo:

```
2024-04-17T09:13:16+00:00    INFO 127.0.0.1    update    Aggiornamento avviato dall'utente Jimmy (139). La versione precedente è 5.0.3.
2024-04-17T09:13:18+00:00    INFO 127.0.0.1    update    Download del file di aggiornamento da ...
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    File Joomla_5.1.0-Stable-Update_Package.zip scaricato.
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Inizio installazione della nuova versione.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Concludendo l'installazione.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Inizio degli aggiornamenti SQL.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    La versione attuale del database (schema) è 5.0.0-2023-09-11.
... Molte query SQL individuali
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Fine degli aggiornamenti SQL.
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Disinstallazione delle estensioni
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Cancellazione di file e cartelle rimossi.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Pulizia dopo l'installazione.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Aggiornamento alla versione 5.1.0 completato.
```

*Tradotto da openai.com*
