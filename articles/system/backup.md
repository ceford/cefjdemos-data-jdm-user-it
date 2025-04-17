<!-- Filename: jdocmanual?manual=user&heading=system&filename=backup.md / Display title: Backup -->

## Gli incidenti accadono!

La creazione e la manutenzione di un sito web richiedono molto tempo, impegno e denaro. Sarebbe un peccato perdere tutto a causa di un incidente inaspettato. Il backup è semplice per i siti nella media. I siti grandi o specializzati probabilmente necessitano di consulenze specialistiche.

## Strategia di Backup

I siti web Joomla! sono composti da due parti:

* I **file** posizionati nell'albero della directory root di Joomla. Tra un aggiornamento e l'altro, i file potrebbero non cambiare molto poiché sono principalmente legati al codice. Possono essere aggiunte nuove immagini e documenti e forse degli override di template.
* Il **database** situato da qualche altra parte sul server host. Il database contiene la maggior parte del contenuto del sito e può cambiare molto poiché gli utenti aggiungono o modificano contenuti.

Ogni proprietario di un sito ha bisogno di una strategia per il recupero del sito in caso di disastro. Un consiglio comune nei forum è quello di **ripristinare l'ultimo backup**. Quindi, è importante decidere cosa eseguire il backup e con quale frequenza farlo. 

I servizi di hosting spesso eseguono delle **istantanee** dei siti dei clienti e potrebbero essere in grado di ripristinare un sito alla condizione in cui si trovava ieri, la settimana scorsa o il mese scorso. Tuttavia, ciò potrebbe coprire tutto ciò che è presente nell'account, come email e altri pacchetti software. Non affidarti a questo per il recupero del sito Joomla.

Questo articolo descrive alcuni metodi **gratuiti** comuni per effettuare il backup di siti Joomla. Potresti scegliere di pagare per strumenti e/o servizi di backup, ma questo non è trattato qui.

## Akeeba Backup

Se usi il menu Amministratore per navigare su **Sistema / Installa Estensioni / Installa Dal Web**, il primo elemento nell'elenco è *Akeeba Backup*. È il primo nell'elenco perché ha il maggior numero di recensioni positive. Inutile dire che ha una lunga storia e una reputazione impeccabile. Esiste una versione gratuita e una versione a pagamento con alcune funzionalità extra. Questo è un modello di business comune per gli sviluppatori di Estensioni. Non temere! La versione gratuita è facile da usare, non ha distrazioni e basta per la maggior parte dei siti. Cosa fa:

* Akeeba Backup analizza la tua installazione per determinare le impostazioni ottimali per creare un file di backup.
* Crea un file di backup composito contenente tutti i file del sito web e il contenuto del database.
* Memorizza backup con timestamp per gestirli, scaricarli o cancellarli a seconda delle necessità.
* Il download è un file .jpa. Si consiglia di utilizzare FTP per eseguire il download.
* Esiste un'applicazione separata, Akeeba Kickstart, per decomprimere il file .jpa. Tutto questo è descritto nella pagina Gestisci Backup di Akeeba.
* Dopo la decompressione, il sito viene installato con un programma di installazione Akeeba in una sequenza simile a un'installazione Joomla.
* Il programma di installazione modifica la configurazione per il ripristino in un'altra posizione e richiede i nuovi dettagli del database.

L'unico problema che potrebbe verificarsi è che il file di backup potrebbe essere molto grande e potresti superare la tua quota di spazio se permetti che i backup si accumulino.

Provalo! Non costa nulla e richiede minuti piuttosto che ore.

## Strumenti dell'Host

La maggior parte dei servizi di hosting fornisce strumenti di backup. Esempio:

### cPanel

Nella pagina **Strumenti**, l'elemento *File* ha un link *Backup*. La pagina **Backup** offre tre opzioni:

* **Backup Completo:** Un backup completo crea un archivio di tutti i file e le configurazioni del tuo sito web. Puoi usare questo file per spostare il tuo account su un altro server o per mantenere una copia locale dei tuoi file.
* **Backup Parziale**
    - Scarica un Backup della Directory Principale
    - Scarica un Backup del Database (con un elenco di database)

Ci sono anche opzioni per **Ripristinare** ciascuno di questi tipi di backup. Potrebbero essere disponibili anche opzioni per produrre backup automatici.

Le singole cartelle possono essere compresse in vari formati adatti al download utilizzando il File Manager di cPanel. Un database può essere esportato utilizzando phpMyAdmin. Nessuno di questi metodi è trattato qui.

## Strumenti Locali

Ci sono occasioni in cui potrebbe essere necessario fare un backup di un sito localmente su un laptop o un computer desktop in ufficio. Ad esempio, potresti voler copiare un sito da/a un servizio di hosting verso/da il tuo computer locale. Se hai un'installazione locale di Joomla, puoi usare Akeeba Backup come descritto sopra. Altrimenti, puoi fare il backup separatamente del database e dei file di Joomla.

### mysqldump

Se stai usando MySQL, è probabile che tu abbia a disposizione lo strumento da riga di comando *mysqldump*. Prova questo comando:

```bash
/usr/local/mysql/bin/mysqldump -u root -p nomedb > ~/tmp/nomedb-dump.sql
```
dove `root` è un utente che ha accesso al database e `nomedb` è il nome
del database che desideri esportare. Potrebbe essere richiesto di inserire la password.

Puoi anche reindirizzare l'output a un comando zip o gzip:
```bash
/usr/local/mysql/bin/mysqldump -u root -p nomedb | gzip > ~/tmp/nomedb-dump.sql.gz
```

### phpMySQL

Per fare lo stesso lavoro con la tua installazione locale di phpMyAdmin, aprilo e
seleziona il database che desideri esportare. Seleziona il pulsante **Esporta** in alto allo schermo. Per impostazione predefinita, l'esportazione *Veloce* usa SQL come formato di output. Seleziona il pulsante **Esporta** per provarlo. Ti verrà chiesto di nominare un file di output.

Se selezioni l'opzione *Personalizzato* puoi scegliere un'opzione di Compressione dell'Output, nessuna, zippata o gzippata. Prova un'esportazione compressa e seleziona il pulsante **Esporta**.

È necessario **controllare** il database esportato. Crea un nuovo database, forse `unimporttest` in modo che sia vicino alla parte superiore della tua lista di database. Con il nuovo database vuoto selezionato, usa il pulsante **Importa** in alto allo schermo. Nel modulo di importazione clicca su **Sfoglia** per trovare il file che hai esportato e poi seleziona il pulsante **Importa**.

Valeva la pena fare il **controllo**. L'esportazione gzip ha esportato solo tre tabelle. L'esportazione zip ha funzionato bene. È stato evidente nelle dimensioni del file esportato. Il file zip era di 4Mb, ma il gzip era solo di 75Kb. Deve esserci un bug da qualche parte!

### Zip e Gzip

Questi strumenti da riga di comando sono abbastanza diffusi e vengono spesso utilizzati all'interno di interfacce grafiche. Ad esempio, nel Finder su Mac posso selezionare una directory contenente un sito Joomla, fare clic con il tasto destro e selezionare **Comprimi**. Ci vogliono pochi secondi per creare un archivio zip e non influenza l'originale.

## Ripristino di un Backup

Consigli comuni dai forum di Joomla:

* Non ripristinare un backup su un sito difettoso.
* Svuota il tuo database eliminando tutte le tabelle o crea un nuovo database e assegna un utente del database ad esso.
* Elimina tutte le directory e i file all'interno della tua directory principale di Joomla.

## Akeeba Quickstart

Se hai utilizzato Akeeba Backup, usa Akeeba Quickstart per ripristinare il tuo backup.
* Consulta il [Video Tutorial](http://akee.ba/abrestoreanywhere).
* Scarica gratuitamente Akeeba Quickstart (PDF 94Kb).
* Verifica che il sito ripristinato funzioni correttamente!

Akeeba Quickstart ripristina sia il database che i file di Joomla. Altri metodi
ripristinano il database e i file di Joomla separatamente.

## Ripristina il Database

Se hai un backup del database, è consigliabile utilizzare strumenti di sistema per ripristinarlo. *phpMyAdmin* può installare database di dimensioni moderate, ma potrebbe esaurire il tempo o la memoria su database di grandi dimensioni.

Se stai utilizzando cPanel su un servizio di hosting, puoi importare un database dalla pagina *Backup / Restore*. Questo non è descritto qui.

Se hai accesso alla riga di comando, sia su un servizio di hosting che sul tuo laptop o computer desktop locale, puoi utilizzare il comando `mysql` per eseguire l'importazione. Carica l'archivio del database in una posizione temporanea al di fuori del tuo albero web ed espandilo in modo da avere un nome file che termina in `.sql`. Quindi utilizza il seguente comando:
```
mysql -u nomeutente_db -p -D nome_db < nome_file_dump_db.sql
```
Sostituisci `nomeutente_db`, `nome_db` e `nome_file_dump_db.sql` con i valori reali per il tuo sito. Potrebbe esserti richiesto di inserire una password per l'utente del database. Potrebbe richiedere un po' di tempo, ma dovrebbe completarsi.

## Ripristina i File

Si tratta semplicemente di espandere il file compresso dall'ultimo backup.  
Except che non è sempre così semplice. A seconda del tuo sistema operativo  
e del metodo scelto, le directory e i file archiviati potrebbero apparire tutti nella  
directory corrente o in una nuova directory oppure potresti essere invitato a nominare una  
directory di destinazione. Fino a quando non sai cosa fa il tuo sistema, potrebbe essere meglio  
mettere l'archivio in una directory vuota, espanderlo lì e poi spostare la  
directory contenente dove deve essere.

Alcuni utenti preferiscono utilizzare SFTP per caricare i file su un servizio di hosting dai  
file d'archivio estratti localmente. Ci sono migliaia di file, quindi questo richiede abbastanza tempo.

Alla radice del tuo sito c'è un file chiamato `configuration.php`. Contiene  
il nome del database e le credenziali di accesso. Assicurati che siano corrette per il tuo  
sito ripristinato. Il file ha le autorizzazioni di accesso impostate a 444. Questo deve essere  
cambiato a 644 in modo che tu possa salvare eventuali modifiche necessarie.

Se tutto va bene, il tuo sito ripristinato dovrebbe funzionare ed essere nello stato in cui si trovava  
quando è stato fatto il backup.  

## Copiare un Sito

Ci sono diverse buone ragioni per copiare un intero sito web da un server 
a un altro. Ad esempio, gli esperti del Forum spesso raccomandano che gli utenti creino 
una versione locale di un sito su un laptop o un computer desktop per scopi di test, 
come provare nuove estensioni o design. A volte un individuo decide di trasferirsi 
a un nuovo servizio di hosting per motivi economici o di prestazione.

Qualunque sia la ragione, il processo è relativamente semplice: fare un backup 
sul sito originale e ripristinarlo sul sito di destinazione. Ci sono alcune 
questioni a cui prestare attenzione:

* Assicurarsi che l'host di destinazione soddisfi i requisiti tecnici minimi di Joomla. 
Ciò significa solitamente versioni di Server, PHP e Database
* Dopo l'installazione, potresti scoprire che alcuni moduli essenziali non sono stati abilitati. 
La maggior parte dei servizi di hosting risolverà tali problemi su richiesta.

*Tradotto da openai.com*

