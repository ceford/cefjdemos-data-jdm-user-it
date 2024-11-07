<!-- Filename: How_do_UNIX_file_permissions_work%3F / Display title: Permessi dei file UNIX -->

I permessi dei file Unix/Linux possono essere complicati. I permessi di base di UNIX sono di tre tipi:

    Permessi del proprietario: Controllano l'accesso ai file per il tuo account.
    Permessi del gruppo: Controllano l'accesso per te e chiunque altro nel tuo gruppo.
    Permessi per altri: Controllano l'accesso per tutti gli altri.

In Unix, quando si configurano i permessi, il server ti permette di definire permessi diversi per ciascuna di queste tre categorie di utenti. In un ambiente di server Web, i permessi vengono utilizzati per controllare quali proprietari di siti Web possono accedere a quali directory e file.
## Come appaiono i permessi Unix?

Quando visualizzi i tuoi file tramite la linea di comando usando il comando Unix `ls -l`, vedrai righe simili alle seguenti, una per ogni file e directory:
```
drwxr-xr-x@  7 username  usergroup    224 13 Feb 10:48 includes
-rw-r--r--@  1 username  usergroup   1060 13 Apr 21:00 index.php
```
Spiegazione:
* Il primo carattere della riga è d per directory o - per file, o ...
* I successivi 9 caratteri sono 3 gruppi di 3 che indicano read (r), write (w) ed execute (x) o un simbolo meno (-) che significa nessun accesso per ciascuno di Proprietario, Gruppo e Altri.
* Il simbolo @ è uno dei possibili attributi estesi,
* Il numero prima del nome utente è la profondità della directory.
* I due nomi sono il nome utente del proprietario e il gruppo utente,
* L'intero seguente è la dimensione del file in byte.
* La data successiva mostra l'ora per gli elementi recenti o l'anno per gli elementi più vecchi.
* Infine, c'è il nome del file o della directory.

In un'utility FTP l'ordine può essere diverso e ci possono essere più o meno informazioni.

### Il proprietario (Utente) è relativo al nome utente

Il Proprietario (Utente) sei normalmente tu, questi permessi saranno applicati al nome del tuo account di hosting.

### Il Gruppo è relativo al gruppo utente

I permessi del Gruppo saranno applicati ad altre persone che sono nel tuo stesso gruppo, in un ambiente di hosting, raramente ci sono altre persone nel tuo stesso gruppo. Questo protegge i tuoi file e directory dall'essere resi disponibili a chiunque altro possa avere un account di hosting sul tuo stesso server.

### Altri è relativo a tutti gli altri

I permessi degli Altri saranno applicati a chiunque altro sul server che non sei tu o non è nel tuo gruppo. Quindi, in un ambiente di web serving, ricordando che nessun altro è normalmente nel tuo gruppo, sono tutti gli altri che accedono al server tranne te. Ciascuno dei tre set di permessi è definito nel seguente modo:

    r = Permessi di Lettura
    w = Permessi di Scrittura
    x = Permessi di Esecuzione

    Proprietario Gruppo Altri
    r w x r w x r w x

Come molti di voi già sanno, i permessi sono normalmente espressi come un valore numerico, qualcosa come 755 o 644. Quindi, come si relaziona questo a quanto discusso sopra? A ciascun carattere dei permessi è assegnato un valore numerico, questo è assegnato in ciascun set di tre, quindi dobbiamo solo usare tre valori e riutilizzarli per ciascun set.

    Proprietario Gruppo Altri
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Ora che abbiamo un valore che rappresenta ciascun permesso, possiamo esprimerli in termini numerici. I valori sono semplicemente sommati nei rispettivi set di 3, il che a sua volta ci darà solo tre numeri che ci indicheranno quali permessi sono impostati. Se ci viene detto che un file ha i permessi 777, ciò significherebbe che quanto segue è vero.

    Proprietario Gruppo Altri
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Quindi...

      4+2+1 4+2+1 4+2+1
    =   7     7     7

Il proprietario del file avrebbe tutti i permessi di Lettura, Scrittura ed Esecuzione, il gruppo avrebbe anche tutti i permessi di Lettura, Scrittura ed Esecuzione, e il resto del mondo potrebbe anche Leggere, Scrivere ed Eseguire il file. I permessi standard e di default assegnati ai file e alle directory dal server sono normalmente:

    Files = 644
    Directories = 755

Questi permessi consentirebbero, per i file;

    644 = rw- r-- r--
    Il proprietario ha Lettura e Scrittura
    Il gruppo ha solo Lettura
    Altri hanno solo Lettura

e per le directory;

    755 = rwx r-x r-x
    Il proprietario ha Lettura, Scrittura ed Esecuzione
    Il gruppo ha solo Lettura ed Esecuzione
    Altri hanno solo Lettura ed Esecuzione

Ora, le cose possono diventare un po' complicate quando iniziamo a parlare di server Web condivisi, il software del server Web verrà eseguito con il proprio nome utente e nome del gruppo; la maggior parte dei server è configurata affinché usino "apache" e "apache" o "nobody" e "nobody" come nome utente e nome del gruppo. Ecco il problema. Il tuo server Web opera come il suo utente e questo utente non sei tu o nel tuo gruppo, quindi i primi due set di permessi non si applicano. Si applicano solo i permessi "Altri". Pertanto, se configuri un set di permessi simile a 640 sui file del tuo sito web, il tuo server Web non sarà in grado di eseguire i file del tuo sito web.

    640 = rw- r-- ---
    Il Proprietario ha Lettura e Scrittura
    Il Gruppo ha solo Lettura
    Altri non hanno alcun diritto

Il server web non ha assegnati nessun permesso e non può Eseguire, Scrivere o, ancora più importante, neanche Leggere il file per offrire il suo contenuto al browser del visitatore del sito web. Se a una directory venissero assegnati i permessi 750, questo avrebbe lo stesso effetto, poiché il server Web non ha nemmeno i permessi per leggere i file nella directory, anche se i file all'interno di quella directory avessero permessi favorevoli.

    750 = rw- r-x ---
    Il Proprietario ha Lettura e Scrittura
    Il Gruppo ha Lettura ed Esecuzione
    Altri non hanno alcun diritto

Le directory hanno una particolarità in più, se una directory non ha il permesso di Esecuzione impostato nel set "Altri" allora, anche se Lettura e Scrittura sono impostati, se il programma non viene eseguito come utente o gruppo, non sarà ancora in grado di accedere ai file all'interno della directory. L'impostazione di Esecuzione consente al programma di "Eseguire" i comandi nella directory, quindi senza di essa il programma (nel nostro caso un server Web) non può eseguire il comando "Leggi", e quindi non può consegnare il tuo file al browser web degli utenti.

## Come si Relaziona Questo con Joomla?

Buona domanda, bene, in primo luogo questo sarebbe importante durante il processo di installazione web. Se riesci a ricordare quando hai avviato il Web Installer di Joomla!, stavamo cercando specifiche directory da designare come scrivibili. Vediamo un numero considerevole di post che affermano che ci sono stati problemi con i permessi durante l'installazione o chiedono quali permessi siano raccomandati. Alcuni considerano persino il messaggio che chiede permessi "Scrivibili" troppo vago.

Sfortunatamente, poiché il Web Installer non sa come è configurato il tuo server, non può essere più specifico. Tuttavia, una volta che comprendi le impostazioni dei permessi e sai qualcosa sugli ambienti di hosting web, scoprirai che il termine *scrivibile* è in realtà molto specifico e una descrizione più che adeguata di ciò di cui Joomla! ha bisogno. Ripensando alle informazioni di cui sopra, potresti ricordare che ci sono tre luoghi in cui i permessi di *scrittura* potrebbero essere impostati:

    Scrivibile dall'Owner
    Scrivibile dal Group
    Scrivibile da Other

Ricordando anche che il server web generalmente non viene eseguito come il tuo utente o nello stesso gruppo. Quando esegui il Web Installer da un browser, è il server web che cerca di accedere ai file, quindi sono i permessi "Other" che si applicheranno. Se i permessi "Other" non consentono al server web di leggere, scrivere o eseguire comandi nelle directory di Joomla!, riceverai il messaggio che le directory non sono *scrivibili*.

In questo caso, sarà necessario configurare i permessi di "Other" su "7" per le directory elencate nel Web Installer. Quindi i tuoi permessi totali potrebbero essere qualcosa come 757, nel peggiore dei casi potrebbe essere necessario impostare 777. Questi permessi molto aperti possono essere reimpostati su 755 dopo che l'installer ha completato l'installazione per aiutare nella sicurezza delle tue directory e file.

    757 = rwx r-x rwx
    Owner ha Lettura, Scrittura ed Esecuzione
    Group ha Lettura ed Esecuzione
    Other ha Lettura, Scrittura ed Esecuzione

Per rendere le cose ancora più confuse, molte aziende di hosting utilizzano software chiamato phpsuExec o suExec, questi strumenti cambiano il modo in cui il server web viene eseguito, dove normalmente non verrebbe eseguito come il tuo nome utente, in questo caso lo fa. L'uso dei permessi *other* potrebbe non essere necessario, ora potrebbe essere necessario configurare le directory come *scrivibili* per il tuo nome utente e nome gruppo, questo consente di impostare i permessi delle directory su 755 o 775 anziché 757 o 777.

    755 = rwx r-x r-x
    Owner ha Lettura, Scrittura ed Esecuzione
    Group ha Lettura ed Esecuzione
    Other ha Lettura ed Esecuzione

    775 = rwx rwx r-x
    Owner ha Lettura, Scrittura ed Esecuzione
    Group ha Lettura, Scrittura ed Esecuzione
    Other ha Lettura ed Esecuzione

Il server web avrà ancora bisogno dell’Esecuzione impostata per il nome utente e della Lettura ed Esecuzione impostata per il nome gruppo in modo che possa eseguire il comando di lettura sui file all'interno della directory. Ancora una volta, questi permessi potrebbero essere ridotti a 755 dopo il completamento del Web Installer. Questo copre le basi per le directory, e riguardo ai file? Qui le cose diventano un po' più semplici. La maggior parte dei file che Joomla! utilizza sarà abbastanza contenta con i permessi predefiniti 644.

    644 = rw- r-- r--
    Owner ha Lettura, Scrittura
    Group ha Lettura
    Other ha Lettura

Questo è valido se non hai bisogno di scrivere nei file dal server web, le stesse regole si applicano come per le directory se hai questa necessità. Un file che potresti voler rendere "Scrivibile" per il server web è il tuo file configuration.php. Questo è il file di configurazione di Joomla!, se pianifichi di cambiare la configurazione attraverso l'interfaccia di amministrazione web, questo file dovrà essere Scrivibile dal server web.

Se il tuo server aveva bisogno che i permessi delle directory fossero impostati su "Other" Scrivibile per l’installazione, allora questo file avrà probabilmente bisogno anche di essere 757 o 777. Lasciare questo file come 757 o 777 è però pericoloso, poiché stai permettendo a tutti di avere accesso "Scrittura", molti exploit dei siti web sfruttano questo fatto, quindi in generale non è raccomandato lasciare questo file con questi permessi.

Se il tuo server web ha uno degli strumenti SU installati e avevi solo bisogno di configurare 755 nelle directory per l'installazione, allora probabilmente avrai anche solo bisogno di impostare 755 o 775 su questo file per consentire modifiche tramite l'interfaccia di amministrazione web, e questi permessi sono generalmente accettati come più sicuri rispetto a 757 o 777.

In conclusione, quali permessi dovrebbero essere impostati per l'installazione di Joomla!? Bene, come puoi vedere, dipende!

So che questo non è tanto utile quanto avresti voluto e sicuramente non è una risposta definitiva, ma in generale, dopo l'installazione, qualsiasi impostazione "7" non sicura può essere reimpostata su qualcosa di più sicuro. Per esempio:

    File = 644
    Directory = 755

Questi permessi consentirebbero, per i file:

    644 = rw- r-- r--
    Owner ha Lettura e Scrittura
    Group ha Lettura solo
    Other ha Lettura solo

e per le directory,

    755 = rwx r-x r-x
    Owner ha Lettura, Scrittura ed Esecuzione
    Group ha Lettura ed Esecuzione
    Other ha Lettura ed Esecuzione

Se hai accesso alla shell SSH, i seguenti comandi possono essere eseguiti dalla riga di comando per reimpostare tutti i file e le directory ai valori predefiniti del server di 755 e 644. Cambia directory alla directory superiore ("/") della tua installazione Joomla!, poi esegui:

    find . -type f -exec chmod 644 {} \;
    find . -type d -exec chmod 755 {} \;

Se hai solo accesso FTP, questo può essere un lavoro che richiede molto tempo, tuttavia, a meno che tu non abbia cambiato più directory durante l'installazione rispetto a quanto richiesto, dovresti solo avere bisogno di reimpostare circa 10 directory e il file *configuration.php*.

Tieni presente che per installare qualsiasi estensione o template dopo l'installazione effettiva di Joomla! potresti aver bisogno di aumentare di nuovo i permessi predefiniti sulle directory appropriate solo per il periodo di installazione, potrai poi ridurli di nuovo dopo che il componente aggiuntivo è installato.

Se decidi di utilizzare la *cache*, la directory della cache dovrà essere *scrivibile* dall'utente del server web per consentirle di scrivere i suoi file temporanei.

## Correggere ricorsivamente i permessi

In una finestra del terminale, a partire dalla radice del sito Joomla, utilizza i seguenti comandi per impostare i permessi di file e cartelle ai valori predefiniti di Joomla.

```bash
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

Nota: Il comando find presume di dover iniziare dalla directory corrente. Per sicurezza, vai nella tua directory public_html e specifica un percorso come primo argomento. Alcune shell, come bash su Apple OS X, richiedono che un percorso sia specificato nel comando find.

Testa tutte le estensioni di terze parti dopo aver modificato i permessi.

