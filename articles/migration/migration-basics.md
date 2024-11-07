<!-- Filename: jdocmanual?manual=user&heading=migration&filename=migration-basics.md / Display title: Fondamenti della Migrazione -->

## Terminologia

I documenti di Joomla! utilizzano una varietà di termini per indicare il passaggio da una versione precedente a una più recente:

* **Migrazione o mini-migrazione** è un termine solitamente applicato al cambiamento da una versione *Maggiore* più vecchia a una più nuova, talvolta attraverso diverse versioni *Maggiori* intermedie.
* **Aggiornamento** è un termine generalmente usato per indicare il cambiamento da una versione recente a quella successiva in una sequenza di versioni *Minori*.
* **Update** è un termine solitamente usato per il processo di aggiornamento utilizzando il componente Joomla Update. È la parola visibile nell'interfaccia amministrativa in Joomla! 3, 4 e 5. D'ora in poi, in questo articolo verrà usato il termine *Update*.

È anche utile sapere che Joomla segue lo standard di Versionamento Semantico. In breve, dato un numero di versione MAJOR.MINOR.PATCH, come 5.1.0:

* La versione **MAGGIORE** consente interruzioni della compatibilità retroattiva.
* La versione **MINORE** consente funzionalità aggiuntive in modo compatibile all'indietro all'interno della versione Maggiore.
* La versione **PATCH** consente la correzione di bug in modo compatibile all'indietro.

Ci possono essere suffissi aggiuntivi come *alpha*, *beta* o *rc*, ma non nelle versioni stabili destinate ai siti di produzione.

## Ragioni per Aggiornare

Le ragioni per aggiornare sono molteplici e diverse:

* **Sicurezza** Sebbene Joomla! sia riconosciuto come un CMS molto sicuro, occasionalmente vengono scoperte e corrette vulnerabilità nelle versioni minori o di patch.
* **Cambiamenti nell'hosting** Joomla utilizza il linguaggio di scripting *PHP* e un server di database come *MySQL*, *MariaDB* o *PostGreSQL*. Questi avanzano attraverso cambiamenti e i servizi di hosting devono mantenersi aggiornati. Quindi potresti scoprire che una versione più vecchia di Joomla non funziona più o smette di funzionare se cambi servizio di hosting.
* **Cambiamenti nel design** Potresti desiderare che il tuo sito appaia meglio, funzioni meglio con i dispositivi mobili e ottenga un punteggio più alto nei motori di ricerca. Potresti dover soddisfare requisiti legali di *Accessibilità*.
* **Funzionalità** Potresti voler utilizzare un'estensione di Joomla che fornisce qualche funzionalità non offerta dalle estensioni principali di Joomla. Le scelte potrebbero essere limitate dalla tua attuale versione principale.

## Backup prima dell'aggiornamento

**Questo è davvero importante!** Anche se hai completato diversi aggiornamenti intermedi, è possibile che qualcosa possa andare storto durante il processo di aggiornamento. Questo potrebbe lasciare il tuo sito non funzionante. Il consiglio standard offerto nei forum è di tornare all'ultimo backup, scoprire perché il backup è fallito, risolvere il problema e poi riprovare.

**Akeeba Backup** è uno strumento gratuito disponibile nella Joomla Extensions Directory (JED) al quale hai accesso diretto tramite Sistema / Installa Estensioni / Installa dal Web. Ci vuole solo un minuto o due per scaricarlo e installarlo. Analizza il tuo sistema per configurare un profilo utilizzando una procedura guidata di configurazione. Poi crea un backup che puoi scaricare per tenerlo al sicuro.

## Autovalutazione

Prima di eseguire un aggiornamento della versione *Maggiore* o *Minore*, è necessario valutare il proprio sistema e le estensioni di terze parti esistenti per verificarne la compatibilità con la versione target di Joomla. È una buona idea fare un elenco delle estensioni di terze parti che hai installato. In Joomla 4 e 5, la lista *Sistema / Estensioni / Gestisci* ha un filtro per selezionare **Estensioni non-core**. Questo non è presente in Joomla 3.

Potresti anche utilizzare il **Forum Post Assistant**. Questo è uno strumento progettato per analizzare un sito e creare un rapporto adatto per essere pubblicato nei Forum di Joomla per aiutare gli esperti del Forum a diagnosticare i problemi del tuo sito. Tuttavia, ha un'interfaccia utente privata che ti informa su tutto il tuo sito. Le sue liste di estensioni (Componenti, ecc.) indicano quali sono *di terze parti*.

I problemi che sorgono durante gli aggiornamenti sono solitamente associati a estensioni di terze parti che non sono compatibili dal punto di vista del codice con la versione target di Joomla. Dovresti controllare la compatibilità di ciascuna estensione e **disinstallare** quelle che sono notoriamente incompatibili. Potresti essere in grado di installare versioni compatibili in seguito.

Dovresti impostare uno dei modelli predefiniti del sito come tuo **modello predefinito**:

* I modelli predefiniti di Joomla! 1.5 sono Rhuk_milkyway, JA Purity, Beez.
* I modelli predefiniti di Joomla! 2.5 sono Atomic, Beez3 e Beez25.
* I modelli predefiniti di Joomla! 3 sono Protostar e Beez3.
* Il modello predefinito di Joomla! 4 è solo Cassiopeia.

## Test Locale

Se possibile, è meglio configurare un ambiente di test locale sul tuo laptop o sulla tua stazione di lavoro domestica per testare la tua procedura di aggiornamento. Puoi utilizzare il backup del tuo sito online per popolare il tuo sito di test. Il tuo sito domestico deve essere in grado di eseguire una copia del tuo sito live e avere specifiche adeguate per PHP e Database per eseguire il sito aggiornato. C'è un articolo separato che descrive come configurare un ambiente di test domestico.

## Informazioni Aggiuntive

Ci sono numerosi articoli che descrivono scenari di aggiornamento specifici che non sono inclusi in questo manuale perché sono vecchi o ripetitivi.

* https://docs.joomla.org/Why_Migrate
* https://docs.joomla.org/Migration_Step_by_Step_Self_Assessment
* https://docs.joomla.org/J3.x:Updating_Joomla_(Install_Method
* https://docs.joomla.org/J3.x:Updating_Joomla_(Update_Method)
* https://docs.joomla.org/Planning_Migration_-_Joomla_1.5_to_4
* https://docs.joomla.org/Planning_for_Migration
* https://docs.joomla.org/Pre-Update_Check
* https://docs.joomla.org/Template_Considerations_During_Migration
* https://docs.joomla.org/J3.x:Update_fails_with_an_error_message
* https://docs.joomla.org/Converting_an_existing_website_to_a_Joomla!_website
* https://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_4

*Tradotto da openai.com*

