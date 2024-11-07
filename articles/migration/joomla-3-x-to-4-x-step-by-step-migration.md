<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Joomla 3 a 4 Passo dopo Passo -->

## Introduzione

**Avvertimento:** Questa guida presume che tu stia iniziando su Joomla 3.10.x. Se ti trovi su una versione precedente, assicurati di aggiornare prima a Joomla 3.10 prima di passare a Joomla 4. Non c'è fretta. Assicurati che tutte le tue estensioni siano pronte per Joomla 4.x. Joomla 3.10.x è supportato fino al 16 agosto 2023.

Di seguito sono riportate istruzioni passo passo per migrare un sito 3.10.x a Joomla! 4.x. Sebbene ci siano centinaia di scenari diversi, questo ti fornirà la procedura di base da seguire. Migrazioni molto complesse saranno probabilmente il risultato di estensioni di terze parti installate. Ti invitiamo a contattare gli sviluppatori delle estensioni di terze parti installate sul tuo sito Joomla per il loro percorso suggerito per migrare le loro estensioni.

## Passo per Passo

### Configura un'Area di Sviluppo

1. Assicurati di utilizzare l'ultima versione di Joomla 3.10.x prima di procedere.
2. Fai un backup del tuo sito live 3.10.x. Puoi usare uno strumento suggerito (vedi *Strumenti Suggeriti* in fondo alla pagina) o puoi farlo manualmente.
    - [Nozioni di base sul backup per un sito web Joomla!](https://docs.joomla.org/Special:MyLanguage/Backup_Basics_for_a_Joomla!_Web_Site)
    - [Quali sono le migliori pratiche per i backup dei siti?](https://docs.joomla.org/Special:MyLanguage/What_are_the_best_practices_for_site_backups%3F)
3. Assicurati che il tuo ambiente soddisfi i [requisiti tecnici per Joomla 4](https://downloads.joomla.org/technical-requirements) prima di procedere.
4. Crea un nuovo database e un nuovo utente per ripristinare il tuo sito 3.10.x.
5. Crea un sito di test o un'area di lavoro e ripristina la copia di backup del tuo sito 3.10.x in uno dei seguenti luoghi:
    - Un sottodominio.
    - Una sottocartella.
    - Un dispositivo locale. Joomla ha un tutorial dettagliato sull'installazione di XAMPP. Tuttavia, [WAMP](https://www.wampserver.com/en/), [MAMP](https://www.mamp.info/en/windows/) e [LAMP](https://sourceforge.net/projects/lampas/) sono tutte valide alternative.
    - Un nuovo account di hosting su un dominio temporaneo nella root. (Se desideri cambiare host nel processo di migrazione.)
      - Ripristinare un sito su un dispositivo locale.
        Vedi [Installare Joomla localmente](https://docs.joomla.org/Special:MyLanguage/Installing_Joomla_locally)
        e [Impostare la propria workstation per lo sviluppo Joomla](https://docs.joomla.org/Special:MyLanguage/Setting_up_your_workstation_for_Joomla_development).
      - Ripristinare un sito con uno strumento elencato in fondo alla pagina.
        (Leggi la documentazione per sviluppatori.)
6. Nel tuo luogo di test, aggiorna la tua istanza Joomla! 3.10.x all'ultima release di manutenzione.
7. Assicurati di avere lo schema del database più recente aggiornato all'ultima versione 3.10.x andando al menu **Gestore Estensioni → Database**. Se il tuo schema non è aggiornato come nell'immagine seguente, fai clic sul pulsante **Correggi**:<br>
    ![database delle estensioni joomla 3](../../../en/images/migration/admin-extension-database-fix.png)
8. Svuota il cestino: hai articoli nel cestino? Se sì, eliminali (e qualsiasi media applicabile che potrebbe essere associato se non utilizzato altrove sul sito). Gli articoli (categorie e voci di menu) lasciati nel cestino possono causare problemi nella migrazione, non consentendo di completarla senza errori.
9. Testa.
10. Backup di nuovo.

### Valuta Ogni Estensione

Durante la pianificazione, hai determinato quali estensioni di terze parti sarebbero rimaste o sarebbero andate via e come migrarle. Per questa parte del Passo per Passo, utilizzerai ampiamente due sezioni diverse del sito: il *Controllo Pre-aggiornamento* in **Componenti → Aggiornamento di Joomla** e **Estensioni → Gestisci → Gestisci**. Esaminerai ogni singola estensione installata sul tuo sito. Determinerai se debbano essere aggiornate all'ultima versione o disinstallate. Maggiori dettagli in [Controllo Pre-aggiornamento](https://docs.joomla.org/Special:MyLanguage/:Pre-Update_Check).

1. Utilizzando il **Controllo Pre-aggiornamento** per utilizzare il Controllo Pre-aggiornamento, sarà necessario impostare il modulo di Aggiornamento di Joomla su Joomla 4. Per farlo, segui:
2. Vai a **Componenti → Aggiornamento di Joomla**. Dovrebbe dire che non sono stati trovati aggiornamenti. Se non lo è, aggiorna Joomla all'ultima versione (deve essere 3.10.x) e testa. Quindi fai un altro backup. Clicca sul pulsante Opzioni in alto a destra.
3. Seleziona *Joomla Next* dal menu a discesa per il Canale di Aggiornamento.<br>
    ![selezione del canale delle opzioni di aggiornamento](../../../en/images/migration/update-options-channel.png)
4. Clicca su **Salva & Chiudi**.
5. Vedrai quindi la tua Versione Joomla Installata, l'ultima versione di Joomla! e l'URL per il pacchetto di aggiornamento. Joomla ti mostrerà di nuovo i requisiti per Joomla 4. Se segnala che hai un sistema o delle estensioni incompatibili, te lo dirà qui. Prenditi un momento per rivedere questa pagina.<br>
    ![aggiornamento a 4 controllo pre aggiornamento](../../../en/images/migration/update-to-4-pre-update-check.png)
    <div class="alert alert-warning"><strong>Avviso:</strong> Non aggiornare a Joomla! 4 
    subito. Questo serve solo a preparare le estensioni di terze parti e rendere il 
    sito compatibile con Joomla! 4.</div>
6. Guarda il Controllo Pre-aggiornamento e il Controllo Pre-aggiornamento delle Estensioni nel tab del Controllo Pre-aggiornamento del modulo Aggiornamento di Joomla. Se ci sono estensioni non incluse nella tua pianificazione, aggiungile alla tua lista di estensioni da investigare.
7. Se hai migrato da Joomla! 2.5 a 3.x in passato, potrebbero esserci delle estensioni residue che devono essere pulite. Le seguenti sono estensioni 2.5 o 3.x più vecchie che devono essere disinstallate prima di aggiornare a Joomla 4:
    - plg_content_geshi
    - Modello Amministratore Bluestork
    - Beez_20
    - Beez5
    - Atomic
    1. Per quanto riguarda i modelli, disinstalla tutti i modelli frontend o backend di base, tranne Protostar e Beez3 (modelli frontend) e Isis o Hathor (modelli amministratore). **NOTA: Protostar non è compatibile con Joomla 4**. Al momento della migrazione, scomparirà. Dovrai selezionare un modello come *default* e puoi usare Protostar o Beez3. Protostar scomparirà al momento della migrazione a Joomla 4.x.
    2. Se incontri altri file che devono essere disinstallati, aggiungili a questa pagina. Questo è un wiki, quindi chiunque può aggiungere contenuti alla pagina. Ti ringraziamo in anticipo per il tuo contributo.
8. Noterai le etichette che indicano se un'estensione è compatibile o meno. Queste etichette generalmente indicano correttamente se dicono No o Sì. Se dicono *Etichetta Compatibilità Mancante* significa che lo sviluppatore dell'estensione non ha utilizzato un'etichetta nella loro estensione, quindi non sappiamo se è o meno compatibile con Joomla 4. Parla con lo sviluppatore per verificare.
9. **Aggiorna Estensioni:** aggiorna tutte le estensioni che manterrai nel tuo sito web. In Joomla! 3.10.x puoi andare a 
    **Gestore Estensioni → Tab Aggiornamento** e cliccare su **Trova Aggiornamenti**, il che aggiungerà un tooltip nella colonna Versione, sotto la tab Gestione, fornendo alcune informazioni di compatibilità dal backend. Questa funzionalità supporta solo le estensioni che si aggiornano tramite la tab Update del Gestore Estensioni. Se hai estensioni installate che non utilizzano l'aggiornamento delle estensioni di Joomla, devono essere valutate manualmente come dettagliato di seguito. Lo stesso discorso vale per quelle estensioni che hanno un tooltip. Dovrai comunque controllare il tipo di pacchetto e il percorso di migrazione con lo sviluppatore dell'estensione per verificare come aggiornare/migrare.
10. Indaga e Disinstalla Estensioni: vai a 
    **Gestore Estensioni → Gestisci**
11. Clicca sul pulsante *Strumenti di Ricerca* per mostrare le opzioni di filtro
12. Seleziona Pacchetto dal menu a discesa *Seleziona Tipo*.<br>
    ![pagina gestione estensioni](../../../en/images/migration/extensions-manage.png)
    <div class="alert alert-info">La selezione iniziale del Pacchetto è raccomandata perché se c'è qualcosa che devi disinstallare in un pacchetto, disinstallerà automaticamente i Moduli associati, i Plugin o qualsiasi altra cosa nel pacchetto contemporaneamente.</div>
13. Disinstalla qualsiasi Pacchetto che non è più necessario o che non verrà migrato a Joomla 4.
14. Ripeti questo processo passando attraverso la tab Gestione per tutti i Tipi nel menu a discesa: Componente, File, Lingua, Libreria, Modulo, Plugin e Modello. Se l'Autore dichiara Joomla! Project, lascia quelle estensioni invariate. Per tutte le altre, assicurati di disinstallare quelle non in uso o non compatibili con Joomla! 4.x. 
    <div class="alert alert-danger"><strong>NOTA!</strong> Non sarai in grado di disinstallare nessun template impostato come predefinito. Dovrai selezionare un template Core supportato come Beez3 o Protostar e poi disinstallare il template se necessario. <em>Un altro promemoria:</em> <strong>Protostar non è compatibile con 
    Joomla 4</strong>. Al momento della migrazione, scomparirà. Selezionarlo come default semplicemente ti porta a Joomla 4.x.</div>
15. Prendi nota di eventuali versioni di Pacchetti e Componenti correntemente in esecuzione che manterrai sul tuo sito. Puoi copiarli/incollarli in un documento di riferimento.
16. Per eventuali estensioni che stai mantenendo ma non usano il Gestore Estensioni per un aggiornamento con un clic (**Estensioni → Gestisci → Aggiorna**) aggiorna tutte le estensioni alle ultime versioni.
17. Prima e mentre aggiorni, nota se le estensioni hanno versioni sia 3.10.x che 4.x nello stesso pacchetto. Se sì, saranno pronte per *un aggiornamento con un clic*. Se no, e le versioni 3.10 e 4.x hanno pacchetti diversi, devi esaminarle caso per caso. Generalmente cadono in uno dei seguenti scenari:
    - L'estensione ha pacchetti separati ma al momento dell'upgrade a 4.x, rilevano automaticamente questo e continuano a funzionare. Assicurati che lo sviluppatore confermi questo.
    - L'estensione ha pacchetti separati che devono essere disinstallati in 3.10.x e poi installati con la versione Joomla 4.x una volta migrato il sito. Un esempio di ciò potrebbe essere un plugin di contenuto. È molto semplice disinstallarlo in 3.10.x e poi reinstallarlo in 4.x.
    - Vedi [Considerazioni sui Modelli](https://docs.joomla.org/Special:MyLanguage/Template_Considerations_During_Migration) per informazioni più specifiche sui modelli e la [Conversione di un modello di versione precedente di Joomla!](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template).

#### Note sul Ricerca (com_search)

Ricerca (com_search) sarà disaccoppiata in Joomla 4.x. Ricerca (com_search) verrà migrata a Joomla 4. Dopo la migrazione, dovrai aggiornarla alla versione Joomla 4.x tramite com_installer. Continuerà ad essere mantenuta, ma più come un'estensione di terze parti ricevendo aggiornamenti tramite com_installer. Si raccomanda di usare Ricerca Intelligente (com_finder) in futuro. La ricerca è ancora disponibile dalla [Directory delle Estensioni Joomla](https://extensions.joomla.org/category/official-extensions/).

#### Note su Collegamenti Web

Collegamenti Web è stato disaccoppiato in Joomla 3.4. Se era in uso su un sito 2.5, il processo di migrazione lo avrebbe notato e avrebbe migrato il componente Collegamenti Web e i dati. Per la migrazione da 3.10.x a 4.x, sarà lo stesso. È ancora disponibile e mantenuto sulla JED a [Estensioni Ufficiali](https://extensions.joomla.org/category/official-extensions).

#### Note sul Routing Legacy

Il routing legacy non sarà disponibile in Joomla 4.x. Sarà disponibile solo Modern. Quando fai la migrazione, se stai usando il routing legacy, il sistema li cambierà automaticamente al routing modern. Vorrai eseguire un controllo sui link interrotti nel tuo sito dopo la migrazione a Joomla 4.x e *prima di andare online*.

### Passare a Joomla! 4.x

Una volta che hai aggiornato o disinstallato le tue estensioni di terze parti in modo che rimangano solo quelle compatibili con Joomla! 4 nella tua installazione, continua con i seguenti passaggi:

1. Vai a **Sistema → Configurazione Globale → Tab Server** e imposta la Segnalazione degli Errori da Predefinito di Sistema a Massima. Assicurati di Salvare & Chiudere. <br>
    ![sistema configurazione globale tab server](../../../en/images/migration/system-global-configuration-server-tab.png)
2. Fai un altro backup.
3. Vai a **Componenti → Aggiornamento di Joomla**. (Dovrebbe dire che non sono stati trovati aggiornamenti. Se non lo è, aggiorna Joomla all'ultima versione e testa. Quindi fai un altro backup.) Clicca sul pulsante Opzioni in alto a destra.
4. Seleziona *Joomla Next* dal menu a discesa per il Canale di Aggiornamento.<br>
    ![componente aggiornamento di joomla seleziona canale di aggiornamento](../../../en/images/migration/update-select-channel.png)
5. Clicca su **Salva & Chiudi**.
6. Vedrai quindi la tua Versione di Joomla Installata, l'ultima versione di Joomla! e l'URL per il pacchetto di aggiornamento. Joomla ti mostrerà di nuovo i requisiti per Joomla 4. Se segnala che hai un sistema o delle estensioni incompatibili, te lo dirà qui. Prenditi un momento per rivedere questa pagina.<br>
    ![controllo aggiornamenti per joomla 4](../../../en/images/migration/update-check.png)
7. Se l'aggiornamento non viene visualizzato, vai a **Gestore Estensioni → Aggiorna** e premi Purge Cache dalla barra degli strumenti. Ora l'aggiornamento a Joomla! 4 dovrebbe apparire.
8. Incrocia le dita e assicurati di avere quel backup disponibile nel caso.
9. Clicca sul pulsante Installa l'Aggiornamento.
10. Prepara il tè mentre la barra di stato si carica fino a diventare completamente verde. Il tempo che ci vuole dipende dal tuo sito, conessione Internet e velocità del server. Il processo richiede circa due minuti. Una volta completato l'aggiornamento, probabilmente sarai disconnesso dall'Amministratore. Accedi nuovamente. Due volte.
11. Se tutto va bene, vedrai un look completamente nuovo nel pannello amministratore di backend.<br>
    ![joomla 4 o 5 home dashboard](../../../en/images/migration/j4-home-dashboard.png)
12. Vai a **Sistema → Manutenzione → Database** e clicca su *Correggi* se compaiono errori.
13. In **Sistema → Installa → Scopri** verifica se ci sono estensioni da installare. (Non dovrebbero esserci!)
14. Vai al frontend del sito e verifica se appare anche se non è il modello giusto. In tal caso, continua. Altrimenti, vedi errori comuni durante la migrazione.
15. Fai un backup.
16. Installa il tuo nuovo template o altre estensioni se le hai da installare. Fai backup frequentemente.
17. Configurali. Fai backup frequentemente.
18. Esegui un controllo sui link interrotti e correggi eventuali link rotti.
19. Testa tutto. Fai backup frequentemente.
20. Se tutto funziona come previsto, torna la Segnalazione degli Errori a Predefinita di Sistema (**Sistema → Configurazione Globale → Tab Server**). Assicurati di **Salva&Chiudi**.

### Andare Online con il Tuo Sito Joomla! 4.x

1. Quando sei pronto per andare online, fai il backup del tuo sito 3.10 per l'ultima volta. Ripristinalo in una sottodirectory o sottodominio se lo desideri.
2. Fai il backup del tuo sito Joomla! 4.x e spostalo o ripristinalo nella root (o cambia i nameserver se stavi costruendo su un dominio temporaneo presso l'account di hosting root).
3. Testa di nuovo.
4. Se in passato hai apportato modifiche di sicurezza al file .htaccess, potresti dover cambiare una riga (o righe) per aggiornare alla versione successiva di Joomla 4. Per favore vai a [Modifiche Htaccess dopo Joomla 4](https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4) per determinare se devi cambiare il tuo file o meno.
5. Rimuovi il sito Joomla! 3.10 dal server entro un paio di giorni a meno che tu non abbia modificato il file *robots.txt* per bloccare i motori di ricerca.
6. Rimuovi tutti i siti di sviluppo su cui hai lavorato o mantienili aggiornati se stanno eseguendo una versione corrente per evitare tentativi di attacco al tuo server.

Se i dati sono cambiati nel sito 3.10 mentre stavi migrando a 4.x, dovrai spostare tali dati sul sito 4.x prima di andare online. Puoi farlo manualmente (assicurati di mantenere gli stessi ID utente - procedi in ordine) o utilizza un [estensione di terze parti](https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export%20transfer%20tool/third-party%20extension/).

## Strumenti suggeriti

- [Akeeba Backup](http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606)
  è molto popolare per il backup e il ripristino.
- Altri [strumenti di backup](https://extensions.joomla.org/tags/backup/).

*Tradotto da openai.com*

