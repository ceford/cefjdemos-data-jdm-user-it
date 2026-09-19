<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Joomla 5 a 6 passo dopo passo",
    "description": " ",
    "author": ""
}
-->

<div class="alert alert-warning">
<p class="h3">Avviso</p>

Questa guida presuppone che si stia iniziando con Joomla 5.4.x. Se si utilizza una versione precedente, assicurarsi di eseguire la migrazione o l'aggiornamento a Joomla 5.4.x prima di effettuare l'aggiornamento a Joomla 6.x.
</div>

## Introduzione

Buone notizie per Joomla 5.4.x a 6.x: si tratta di un aggiornamento, non di una migrazione. Perché? Due motivi principali:

- Le estensioni di Joomla 5 (J5) che hanno rimosso tutte le parti di codice deprecate, utilizzano codice Joomla aggiornato e non richiedono l’attivazione del plugin Behaviour - Compatibilità all'indietro, funzioneranno in Joomla 6 (J6)
- La maggior parte delle altre funzionerà con il nuovo plugin Behaviour - Compatibilità all'indietro 6 attivato

Questa documentazione riflette il processo più semplice, combinando la pianificazione e la procedura dettagliata in un unico documento. Tuttavia, saranno necessarie alcune competenze. Consulta [[Migration Step by Step Self Assessment|Autovalutazione]] per determinare se dovresti occuparti personalmente dell’aggiornamento oppure no.

<div class="alert alert-info">
<p class="h3">Documentazione per sviluppatori da 5.4 a 6.0 per gli sviluppatori di estensioni di terze parti.</p>

- [Rimosso e incompatibilità con le versioni precedenti](https://manual.joomla.org/60/removed-backward-incompatibility)
- [Nuove deprecazioni](https://manual.joomla.org/60/new-deprecations)

- [Informazioni sulla documentazione delle migrazioni](https://manual.joomla.org/migrations)
- [Nuove funzionalità](https://manual.joomla.org/60/new-features/)
</div>

## Pianificazione dalla versione 5.4.x alla 6.x

### Hosting/Specifiche tecniche

1. Determina se il tuo ambiente di hosting soddisfa i requisiti. Non potrai 
eseguire l'aggiornamento a Joomla 6 se l'ambiente del tuo server non soddisfa i 
[minimi requisiti tecnici](https://manual.joomla.org/docs/get-started/technical-requirements/). 
L'opzione per eseguire l'aggiornamento non apparirà nel componente Joomla Update.
    - PHP 8.3
    - MySQL 8.0.13
    - MariaDB 10.6.x
    - PostgreSQL 14.0

Puoi controllare le informazioni di sistema del sito Joomla 5 facendo clic su Sistema -> Informazioni di sistema. Contatta il tuo provider di hosting se il server non soddisfa i requisiti.

![Dashboard di sistema con il collegamento Informazioni di sistema evidenziato](../../../en/images/migration/joomla-5-to-6-steps/01-steps-5-to-6-system-dashboard.png)

Di seguito è riportato un esempio di ambiente che soddisfa i requisiti tecnici. Mostra MySQL 8.0.43, PHP 8.3, Joomla 5.4.x e il plugin di compatibilità con le versioni precedenti disabilitato.
![Informazioni di sistema che mostrano la versione di Joomla, la versione di PHP, il tipo di database, la versione del database e il plugin di compatibilità con le versioni precedenti disabilitato](../../../en/images/migration/joomla-5-to-6-steps/02-steps-5-to-6-system-information.png)

2. Verifica la compatibilità di tutte le tue estensioni con Joomla 6. Esistono diversi scenari relativi alle estensioni di terze parti per questo aggiornamento.

    1. L’estensione potrebbe essere compatibile con J5 e J6 SENZA utilizzare il plugin di compatibilità con le versioni precedenti.
    2. L’estensione potrebbe essere compatibile con J5 e J6 UTILIZZANDO il plugin di compatibilità con le versioni precedenti.
    3. L’estensione potrebbe sembrare funzionare in J6, ma quando provi a utilizzarla, non funziona.
    4. L’estensione potrebbe causare il malfunzionamento dell’intero sito.

Non preoccuparti! Non è così grave come sembra! Innanzitutto, parliamo dei plugin di compatibilità con le versioni precedenti.

<div class="alert alert-warning">
<p class="h3">Avvertenza</p>

Per effettuare l’aggiornamento da Joomla 5.4.x a 6.x, il plugin di compatibilità con le versioni precedenti per Joomla 5 DEVE essere DISABILITATO.
</div>

### I plugin per la compatibilità con le versioni precedenti

Il plugin [Behaviour - Backward Compatibility 6](https://manual.joomla.org/60/compat-plugin/) incluso in Joomla 5.4.x serve a migliorare la compatibilità con le versioni precedenti tra Joomla 5 e Joomla 6. Il plugin consente alle estensioni di terze parti di utilizzare classi non più incluse in Joomla 6. È implementato come plugin di tipo "Behaviour" per garantire che venga caricato prima di qualsiasi altro plugin.

![Pagina del plugin che mostra i plugin per la compatibilità con le versioni precedenti](../../../en/images/migration/joomla-5-to-6-steps/03-steps-5-to-6-bc-plugins.png)

L'immagine sopra mostra due plugin per la compatibilità con le versioni precedenti:

1. Behaviour - Backward Compatibility e
2. Behaviour - Backward Compatibility 6

Il plugin Behaviour - Backward Compatibility (senza un numero nel nome del plugin) viene fornito con Joomla 4.4.x per creare un livello di compatibilità con le versioni precedenti per le estensioni di Joomla 5. **Questo plugin deve essere disabilitato prima di eseguire l'aggiornamento a J6**.
Il plugin Comportamento - Compatibilità con le versioni precedenti 6 viene fornito con Joomla 5.4.x per creare un livello di compatibilità con le versioni precedenti per le estensioni di Joomla 6.

Non possono essere entrambi abilitati durante l'aggiornamento a J6.

Prima di effettuare l'aggiornamento da Joomla 5 a Joomla 6, il plugin Comportamento - Compatibilità con le versioni precedenti (senza un numero nel nome del plugin) deve essere disabilitato. Prima di poter effettuare l'aggiornamento a J6, devi assicurarti che tutte le estensioni di terze parti possano funzionare sul tuo sito web senza che il plugin Comportamento - Compatibilità con le versioni precedenti sia abilitato.

Dopo aver verificato che tutte le estensioni di terze parti siano compatibili e pienamente funzionanti in J5 senza che il plugin Comportamento - Compatibilità con le versioni precedenti sia abilitato, puoi disabilitarlo. Detto questo, ti consigliamo di procedere con cautela. Prima di disabilitare il plugin di compatibilità con le versioni precedenti, è consigliabile fare una delle due cose seguenti:

1. Esegui l’operazione su un sito di sviluppo/test. In questo modo, se dimentichi accidentalmente un’estensione che rende inaccessibile il backend, non metterai fuori uso il sito di produzione.
2. Assicurati di avere accesso al database. In questo modo, se necessario, potrai riattivare rapidamente il plugin tramite il database. Maggiori informazioni sono disponibili di seguito.

Quando esegui un aggiornamento a J5.4.x, il plugin Comportamento - Compatibilità con le versioni precedenti 6 verrà abilitato automaticamente. Nelle nuove installazioni di J6, il plugin di compatibilità con le versioni precedenti sarà disabilitato per impostazione predefinita.

Il plugin Comportamento - Compatibilità con le versioni precedenti 6, che supporta le estensioni compatibili con J5, sarà disponibile per tutto il ciclo di vita di J6. In J7, le estensioni di J5 non saranno rese compatibili con le versioni precedenti tramite il plugin. Questo offre agli sviluppatori di estensioni altri due anni per rendere le proprie estensioni compatibili con J6 senza il plugin di compatibilità con le versioni precedenti. L’intenzione è che, con ogni versione del ciclo di vita, un plugin di compatibilità con le versioni precedenti supporti il ciclo di vita precedente fino a quello successivo.
È possibile disabilitare il plugin Behaviour - Backward Compatibility 6 in J6? Ottima domanda. Dopo aver verificato che tutte le estensioni di terze parti siano compatibili e pienamente funzionanti senza il plugin di compatibilità con le versioni precedenti, è possibile disabilitare il plugin Behaviour - Backward Compatibility 6. Detto questo, consigliamo di procedere con cautela. Prima di disabilitare il plugin Behaviour - Backward Compatibility 6, si consiglia di fare una delle due cose seguenti:

1. Farlo su un sito di sviluppo/test. In questo modo, se si è accidentalmente omessa un’estensione che rende il backend inaccessibile, non si metterà fuori uso il sito di produzione.
2. Assicurarsi di avere accesso al database. In questo modo, sarà possibile riabilitare rapidamente il plugin se necessario. Maggiori informazioni di seguito.

### Controllo pre-aggiornamento o Gestisci estensioni

In teoria, il controllo pre-aggiornamento dovrebbe indicarti se le tue estensioni di terze parti sono compatibili con J6. Tuttavia, il controllo pre-aggiornamento è utile solo se tutti gli sviluppatori delle estensioni hanno indicato la compatibilità delle proprie estensioni. In un mondo perfetto, la sezione **Estensioni** del controllo pre-aggiornamento dovrebbe indicarti se un'estensione:

* Può essere aggiornata senza il plugin di compatibilità con le versioni precedenti abilitato
* Può essere aggiornata con il plugin di compatibilità con le versioni precedenti abilitato
* È necessario aggiornare l'estensione prima di eseguire l'aggiornamento da J5 a J6
* È completamente incompatibile
I test hanno evidenziato discrepanze tra le estensioni compatibili e quelle non compatibili. Questo non è un problema del componente di verifica pre-aggiornamento. Gli sviluppatori delle estensioni inviano infatti, tramite le loro estensioni, informazioni che consentono di compilare correttamente la verifica pre-aggiornamento. Se le loro estensioni non sono programmate per comunicare alla verifica pre-aggiornamento le informazioni corrette, il componente di verifica pre-aggiornamento, né il Joomla! Project, possono fare ben poco (nulla) al riguardo. Una buona fonte di informazioni è il sito web dello sviluppatore dell’estensione di terze parti, per verificare come debba essere gestita l’estensione specifica durante l’aggiornamento da J5 a J6.

L’immagine più avanti in questa sezione mostra un esempio del componente di verifica pre-aggiornamento nella sezione Estensioni di Joomla 5.4.x.

La sezione superiore mostrerà le estensioni che richiedono un aggiornamento. Vai a Sistema -> Aggiornamento -> Estensioni e aggiorna le tue estensioni.
La sezione centrale mostra le estensioni per le quali le informazioni sugli aggiornamenti non sono disponibili dallo sviluppatore dell'estensione. Non sarà possibile sapere se sono compatibili o meno senza testarle o contattare lo sviluppatore.

La sezione inferiore mostra le estensioni per le quali non è richiesto alcun aggiornamento. Ciò significa che le estensioni comunicano a Joomla di essere compatibili con Joomla 6. Non viene specificato se richiedano o meno il plugin di compatibilità con le versioni precedenti.

Si noti che queste estensioni non sono consigliate dal progetto Joomla. Sono mostrate solo come esempio. Sono state scelte casualmente dalla JED come test.

![Sezione delle estensioni del controllo preliminare all'aggiornamento](../../../en/images/migration/joomla-5-to-6-steps/04-steps-5-to-6-pre-update-check.png)

Si consiglia di utilizzare esclusivamente la sezione **Estensioni** del componente di controllo preliminare all'aggiornamento come panoramica di livello estremamente generale, ma non come fonte di verità assoluta. In altre parole, potrebbe non essere possibile fare affidamento sul componente di controllo preliminare all'aggiornamento, a seconda delle estensioni utilizzate.
*Qual è dunque la fonte di verità?* Sistemi -> Gestisci estensioni

![Dashboard di sistema con «Gestisci estensioni» evidenziato](../../../en/images/migration/joomla-5-to-6-steps/05-steps-5-to-6-system-dashboard-manage.png)

Dalla schermata Estensioni: Gestisci, sarà possibile visualizzare tutte le estensioni di terze parti utilizzate nel sito. Nello screenshot qui sotto è mostrata la schermata principale. Nella colonna Autore è possibile vedere il nome di uno sviluppatore di estensioni noto in diverse righe. È inoltre possibile vedere l'autore del progetto Joomla in diverse righe.

![Pagina principale Gestisci estensioni](../../../en/images/migration/joomla-5-to-6-steps/06-steps-5-to-6-extensions-manage.png)

Verifica le estensioni di terze parti. Successivamente, dovrai determinare se sono compatibili con J6 (con o senza il plugin di compatibilità con le versioni precedenti) oppure no. Se non lo sono, l'aggiornamento non avrà successo.

### Tre modi per verificare la compatibilità delle estensioni di terze parti con J6

1. Consulta il sito web dello sviluppatore.
2. Esegui un backup/copia del tuo sito J5, ripristinalo su un sottodominio, attiva il debug e segui la procedura dettagliata (riportata di seguito) per eseguire l’aggiornamento a J6. Verifica se qualcosa si blocca. In caso affermativo, disabilita ogni estensione che genera un errore, annotando l’estensione. Dovrai contattare lo sviluppatore in merito, poiché l’estensione non è compatibile con J6.
3. Installa un pacchetto J6 pulito su un sottodominio, abilita il plugin Comportamento - Compatibilità con le versioni precedenti, installa tutte le estensioni che utilizzi e verifica se funzionano.

NOTA: la Joomla! Extensions Directory JED mostrerà i badge di compatibilità con Joomla 6 per le estensioni compatibili con o senza l’utilizzo del plugin di compatibilità con le versioni precedenti.
Potresti fare una combinazione di quanto sopra. Inizia con un’installazione pulita e prova le tue estensioni. Quando saprai quali funzionano e quali no, potrai collaborare con gli sviluppatori per verificare a che punto sono con lo sviluppo per J6. POI, una volta che tutte le tue estensioni funzioneranno in un sito pulito, saprai di poter **testare** un aggiornamento completo da J5.4.x a 6.x.

Potresti voler determinare se un’estensione funziona senza il plugin di compatibilità con le versioni precedenti abilitato. In tal caso, ti servirà l’accesso al database. Pianificalo. Assicurati di avere accesso al database.

Dopo aver installato una nuova installazione di J6, il plugin di compatibilità con le versioni precedenti sarà disabilitato. Installa ogni estensione una alla volta. Se blocca il tuo sito, abilita il plugin di compatibilità con le versioni precedenti tramite il database.
Il plugin di compatibilità con le versioni precedenti si trova nel database, nella tabella `#__extensions`. Si chiama `plg_behaviour_compat6`. Impostare il campo Enabled su 0 per disabilitare il plugin e su 1 per abilitarlo. Abilitando nuovamente il plugin di compatibilità con le versioni precedenti, potresti riuscire ad accedere di nuovo al backend di Joomla (a condizione che l’estensione funzioni con il plugin di compatibilità con le versioni precedenti).

OPPURE

Puoi disabilitare singole estensioni nel database, in modo da poter continuare a testare le altre estensioni per verificare se funzionano senza che il plugin di compatibilità sia abilitato. Queste voci si trovano nella tabella `#__extensions`. Modifica il campo Enabled impostandolo su 0 per disabilitare l’estensione.
In alcuni casi, quando installi un’estensione in J6 che non è compatibile, con o senza il plugin di compatibilità all’indietro abilitato, dovrai trovare nel database le voci relative a quell’estensione (potrebbero essere poche o molte) e disabilitarle finché non riuscirai nuovamente ad accedere al backend. Queste voci si trovano nella tabella #__extensions. Modificherai il campo Enabled impostandolo su 0 per disabilitare l’estensione. Una volta che potrai accedere nuovamente al backend di Joomla, potrai disinstallarla correttamente da Sistema -> Gestisci -> Estensioni. Quindi contatta lo sviluppatore.

### Cassiopeia e Weblinks

#### Cassiopeia

Cassiopeia rimarrà il template del frontend per Joomla 6. Le tue personalizzazioni dovrebbero funzionare correttamente; tuttavia, ti consigliamo di effettuare dei test su un sito di sviluppo per assicurartene.

#### com_weblinks

L’estensione Weblinks funziona in J6 senza il plugin di compatibilità con le versioni precedenti abilitato nella versione 5.4.0+:

- [Weblinks si evolve nel JCM](https://magazine.joomla.org/all-issues/september-2025/joomla-weblinks-evolved-insights-from-gsoc-2025). 
- [Weblinks nella JED](https://extensions.joomla.org/extension/weblinks/).

### Esecuzione di prova

Nell’ambito della pianificazione, è consigliabile testare l’aggiornamento su un sottodominio o in locale per verificare che funzioni perfettamente. Assicurati di tenere traccia di tutti i passaggi necessari affinché l’aggiornamento avvenga **perfettamente**.

Dopo aver testato l’aggiornamento su un sottodominio o su localhost, e aver verificato che funzioni **perfettamente**, puoi eseguire un backup del sito di produzione e procedere con l’aggiornamento. Di seguito sono riportate le istruzioni dettagliate.

## Aggiornamento passo dopo passo

Il sito che si desidera aggiornare deve soddisfare tutti i requisiti tecnici e deve eseguire Joomla 5.4.x per poter essere aggiornato. Se il sito non esegue ancora Joomla 5.4.x, aggiornarlo alla versione 5.4.x prima di eseguire l’aggiornamento a J6.

1. Seguire tutte le istruzioni nella sezione Pianificazione (sopra) prima di eseguire l’aggiornamento.
2. **Eseguire il backup del sito web.**
3. Aggiornare le estensioni che devono essere aggiornate.
4. Disabilitare o disinstallare le estensioni non compatibili con J6.
5. Attivare il debug (Configurazione globale -> scheda Sistema -> impostazione Debug del sistema su Sì).
6. **Eseguire nuovamente il backup del sito web.**
7. **Testare il backup per assicurarsi che possa essere ripristinato.** (Sì, farlo. Ci si sentirà meglio.)
8. Andare a Sistema -> Aggiornamento -> Joomla
![Il pannello di controllo del sistema con Joomla Aggiornamento evidenziato](../../../en/images/migration/joomla-5-to-6-steps/07-steps-5-to-6-system-dashboard-joomla.png)
9. Fare clic sul pulsante Opzioni nella barra degli strumenti superiore, sulla destra.
![La pagina di aggiornamento di Joomla con il pulsante Opzioni evidenziato](../../../en/images/migration/joomla-5-to-6-steps/08-steps-5-to-6-joomla-update.png)
10. Cambia il canale di aggiornamento in Joomla Next.
![Opzioni di aggiornamento di Joomla con il canale di aggiornamento evidenziato](../../../en/images/migration/joomla-5-to-6-steps/09-steps-5-to-6-joomla-update-options.png)
11. Fai clic su Salva e chiudi nella barra degli strumenti superiore.
12. Se il server soddisfa le specifiche tecniche, vedrai la schermata seguente, con i collegamenti nella barra laterale sinistra per Impostazioni richieste, Impostazioni consigliate ed Estensioni.
![Controllo preliminare all'aggiornamento con la barra laterale evidenziata](../../../en/images/migration/joomla-5-to-6-steps/10-steps-5-to-6-pre-update-check-for-6.png)
13. È molto probabile che le Impostazioni richieste e le Impostazioni consigliate siano corrette, poiché questa schermata non verrà visualizzata se il tuo ambiente non soddisfa i requisiti tecnici. Le Estensioni potrebbero non essere corrette. Consulta la sezione Pianificazione (sopra) relativa al controllo preliminare all'aggiornamento e al motivo per cui potrebbe non essere visualizzato un segno di spunta verde, pur avendo tutte le estensioni compatibili. Hai già eseguito i test (vero?), quindi sai già se sono compatibili o meno.
14. Il plugin Backward Compatibility 6 è abilitato in Joomla 5.4.x. Per eseguire l’aggiornamento a J6, è necessario disabilitare il plugin Comportamento - Backward Compatibility.
15. **Se non hai seguito le istruzioni in Pianificazione (sopra) per l’esecuzione di prova, fermati ora, torna alla sezione Pianificazione e segui le istruzioni. La pianificazione è la parte più importante di questo aggiornamento.**
16. Dopo esserti assicurato che tutte le estensioni siano compatibili con J6 e aver testato l’aggiornamento con esito perfetto, puoi selezionare il pulsante per confermare di aver preso atto degli avvisi relativi alle estensioni potenzialmente incompatibili e procedere con l’aggiornamento; fai clic su OK nella finestra popup, quindi fai clic sul pulsante Aggiorna.
![Avviso di conferma degli avvisi](../../../en/images/migration/joomla-5-to-6-steps/11-steps-5-to-6-pre-update-warnings.png)
17. Quindi il sito ti chiederà nuovamente di confermare di aver eseguito un backup (e lo hai fatto, verificando anche che sia possibile ripristinarlo).
![Pagina Carica e aggiorna a Joomla 6](../../../en/images/migration/joomla-5-to-6-steps/12-steps-5-to-6-upload-and-update.png)
18. Il tuo sito eseguirà l’aggiornamento a J6.  
![Pagina di avanzamento dell'aggiornamento](../../../en/images/migration/joomla-5-to-6-steps/13-steps-5-to-6-joomla-update-progress.png)
19. Un aggiornamento completato correttamente mostrerà una schermata simile a questa:  
![Pagina dello stato dell'aggiornamento che mostra il successo](../../../en/images/migration/joomla-5-to-6-steps/14-steps-5-to-6-joomla-update-success.png)
20. Nell’angolo in alto a destra dello schermo vedrai che il tuo sito è Joomla 6.  
21. Verifica il frontend del tuo sito.  
22. Verifica il backend del tuo sito.  
23. Disattiva il debug in Sistema -> Configurazione globale -> scheda Server.  
24. Sistema la tua nuova ricerca intelligente, se necessario.  
25. Goditi una bella bevanda e meravigliati di quanto sei straordinario.

## E se qualcosa va storto?

Se hai testato tutto in anticipo, non dovrebbe succedere. Tuttavia, è possibile che qualcosa nell’ambiente sia cambiato o che del codice in un’estensione sia cambiato tra il momento dei test e l’aggiornamento.

Poiché hai abilitato il debug prima di iniziare, dovresti riuscire a vedere quale estensione causa il problema e disabilitarla (potrebbe essere necessario farlo dal database se non puoi più accedere al backend per disabilitarla). In questo modo il sito sarà operativo mentre cerchi di capire cosa è andato storto e risolvi il problema.

Nel peggiore dei casi, ripristina il backup per avere il tempo di analizzare quanto accaduto in un ambiente di test.

Database Fix potrebbe risolvere alcuni dei tuoi problemi. Vai al System Dashboard e fai clic su Database.

![System Dashboard con il collegamento a Database evidenziato](../../../en/images/migration/joomla-5-to-6-steps/15-steps-5-to-6-system-dashboard-database.png)

Nella pagina Manutenzione: database verranno mostrati tutti i problemi della struttura del database che il sito potrebbe presentare. Seleziona la casella di controllo appropriata, quindi fai clic sul pulsante Aggiorna struttura nella barra degli strumenti superiore.

![Pagina del database di manutenzione che mostra un problema](../../../en/images/migration/joomla-5-to-6-steps/16-steps-5-to-6-maintenance-database.png)

## Altri luoghi in cui ricevere assistenza

- [Forum Joomla: sezione Migrazione e aggiornamento 6.x](https://forum.joomla.org/viewforum.php?f=866&sid=47959551fb677ee3690f8b61eece277b)
- [Community Joomla su Mattermost](https://joomlacommunity.cloud.mattermost.com/main/channels/town-square)

*Tradotto da openai.com*