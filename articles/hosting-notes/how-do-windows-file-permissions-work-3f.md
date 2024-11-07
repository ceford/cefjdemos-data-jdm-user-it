<!-- Filename: How_do_Windows_file_permissions_work%3F / Display title: Autorizzazioni dei File di Windows -->

## Introduzione

Per coloro che stanno sviluppando o distribuendo i propri siti web Joomla! da un ambiente Windows, a volte è difficile ottenere informazioni pertinenti riguardo i permessi. Sfortunatamente, è un dato di fatto che la maggior parte dei server web viene offerta sotto Unix e che Unix è ben documentato in questo ambiente. Si spera che le informazioni seguenti possano chiarire eventuali confusioni e fornire una piccola guida anche a questo proposito.

### Panoramica sul server web Windows

Innanzitutto, discutiamo delle differenze tra i server. In generale, la maggior parte degli utenti Windows sembra utilizzare Apache(Win32) o Microsoft IIS. Questi due server web operano in modo molto diverso e utilizzano modelli di distribuzione leggermente diversi. Apache(Win32) generalmente gira sul computer host come l'utente sotto il quale è stato installato, mentre IIS si installa sotto un utente specifico ma funzionerà sotto un nuovo utente installato *IUSR_*.

### Impostazioni predefinite dei permessi

Di default, Unix tende a concedere l'accesso completo solo all'utente *proprietario* dei file e delle directory, in opposizione a questo approccio Windows assegna di default anche al Gruppo *Everyone* i permessi completi. La prima cosa che qualsiasi buon amministratore Windows farà è rimuovere i diritti del gruppo *Everyone*, per migliorare la sicurezza. Per i test su PC locale, probabilmente non è necessario, ma spiega il motivo per cui, se *Everyone* non è rimosso e esegui qualche tipo di script di controllo dei permessi o il controllo pre-installazione di Joomla!, in generale avrai permessi completi di *Lettura, Scrittura ed Esecuzione* perché stai acquisendo i diritti del gruppo *Everyone*.

### Server di informazione Internet di Microsoft (IIS)

IIS esiste in due versioni principali, PWS (Personal WebServer) e IIS (Internet Information Server). Essenzialmente, si tratta della stessa applicazione. PWS è solo una versione ridotta di IIS progettata per ambienti desktop, mentre IIS è progettato per ambienti server. PWS ti limita a un sito web principale, quindi le tue installazioni di applicazioni saranno generalmente in sottodirectory del sito web principale. IIS, d'altra parte, fornisce la funzionalità per eseguire Host Virtuali da queste directory, offrendo la possibilità multi-sito.

Dato i limiti di funzionalità differenti, PWS non ha il *Wizard delle autorizzazioni* poiché si ritiene che non sia necessario. Solo un utente utilizzerà il server PWS. In IIS, molti utenti utilizzeranno il server, pertanto sono necessarie assegnazioni di permessi differenti.

Una volta rimosso l'account *Everyone*, Windows IIS resta con l'account *IUSR_* avente diritti di livello superiore alle directory del server Web. Un controllo dei permessi ora dovrebbe dare risultati differenti. Solo l'account *IUSR_* ha permessi completi e altri utenti dovrebbe acquisire solo permessi *Solo Lettura* o nessun diritto. I diritti sono determinati da quali altri utenti sono stati assegnati manualmente diritti alle directory IIS.

### Assegnazione dei permessi

Assegnare i permessi in Windows è abbastanza semplice, ma a volte può risultare un po' confuso. Fai clic con il pulsante destro del mouse sulla cartella o file appropriato. Selezionando *Proprietà* o *Condivisione e sicurezza* si accede al pannello Gestione sicurezza di Windows. Selezionando (cliccando una volta) qualsiasi nome utente elencato si visualizzano i diritti che quel utente ha nella metà inferiore del pannello. Alcuni diritti potrebbero essere *in grigio*. Questi non sono disponibili, o perché l'utente corrente (con cui sei loggato) non ha permessi sufficientemente alti per modificarli, o perché sono ereditati dalla directory superiore e sono stati impostati per utilizzare i permessi di quella directory di livello superiore (questo è generalmente il meccanismo predefinito).

Come puoi vedere, Windows utilizza il seguente schema di Permessi/Diritti:

| # | Permessi | Diritti |
|:-----:|:----------|:---------|
| 1 | Controllo completo | Consente: 1, 2, 3, 4, 5, 6, 7 |
| 2 | Modifica | Consente: 2, 3, 4, 5, 6 |
| 3 | Lettura ed Esecuzione | Consente: 3, 4 |
| 4 | Visualizza contenuto cartella | Consente: 4 (ma non può eseguire programmi) |
| 5 | Lettura | Consente: 5 (Implica: 4) |
| 6 | Scrittura | Consente: 6 (Implica:4) |
| 7 | Permessi speciali | Consente: Combinazioni |

### Proprietà dei permessi dei file in Windows

I permessi dei file in Windows possono essere considerati come aventi proprietà **simili** ai permessi dei file (Modalità) UNIX o Linux, sono solo rappresentati in modo diverso. Ad esempio, se sei principalmente un utente Unix/Linux, probabilmente sei abituato ad avere i permessi rappresentati come 644/666 755/777, invece di essere descritti nei termini sopra. Quindi, quando ti viene detto di utilizzare 644 questo equivale a:

* Il proprietario di questo file può leggere e scrivere su di esso.
* Il gruppo del proprietario può leggere il file.
* Tutti gli altri possono leggere il file.

**Nota:** I permessi Windows e Unix (Liste di Controllo Accessi) non equivalgono esattamente, dato che Windows non utilizza il meccanismo dei *Gruppi* nello stesso modo. Tuttavia, per questa discussione e riguardo l'ambiente Hosting Web possono essere sommariamente equiparati. Ah, ma in Windows i ***Gruppi*** non sono usati e ***Everyone*** dovrebbe essere stato rimosso. Qui è dove Windows e Unix non equivarrebbero del tutto, ma ciò che si può fare è *corrispondere* o *correlare* significati equivalenti.

Questo schema non fornirà realmente una guida specifica sui permessi Windows o NTFS ma piuttosto una comprensione di come i permessi stile Unix/Linux numerati comunemente citati si correlano su una macchina con un sistema di file NTFS. I file che sono posizionati nella radice www o public_html, oppure qualunque directory a cui il tuo sito (www.domain.com.au o localhost) punta sul tuo disco rigido dovrebbero essere di proprietà del tuo account utente, ma solo se quell'utente non è considerato un utente privilegiato come *Amministratore* su Windows o *root* su UNIX/Linux. Questi account permettono troppa accesso e non dovrebbero mai essere usati per l'uso quotidiano.

### Migliori pratiche

Le pratiche di sicurezza comunemente utilizzate suggeriscono che tutti i **file** dovrebbero avere i seguenti permessi.

* **Proprietario:** Lettura & Scrittura
* **Gruppo:** Solo Lettura
* **Altri:** Solo Lettura

Tutte le **directory/cartelle** dovrebbero avere i seguenti permessi:

* **Proprietario:** Lettura, Scrittura & Esecuzione
* **Gruppo:** Lettura & Esecuzione
* **Altri:** Lettura & Esecuzione

Probabilmente, questo non è necessariamente il massimo della sicurezza, ma si deve trovare un equilibrio tra sicurezza, funzionalità e manutenibilità. Windows, a differenza di Unix, non mantiene un singolo ACL per *Esecuzione*, ma semplicemente fornisce *Lettura & Esecuzione* combinati, il che non implica *Scrittura*. L'ACL *Lettura & Esecuzione* implica tuttavia *Visualizza contenuto cartella*. Pertanto, se hai solo permessi di *Lettura & Scrittura* su una directory ma non hai *Esecuzione*, non sarai in grado di vedere il contenuto della directory e potresti anche avere problemi nell'eseguire il file attraverso un browser web. È necessaria una piccola comprensione dei permessi UNIX/Linux per equivarli/correlati completamente ai permessi Windows. La tabella seguente dovrebbe aiutare;

| Modalità Unix | ACL Windows | Commenti |
|:-----:|:----------|:---------|
| 7 | Modifica | Lettura, Scrittura & Esecuzione, dovresti essere il proprietario di questo file |
| 6 | Lettura & Scrittura |  |
| 5 | Lettura & Esecuzione | usato per la maggior parte delle applicazioni |
| 4 | Solo Lettura | sicurezza tramite oscurità non è una buona pratica |
| 3 | Scrittura & Esecuzione | non disponibile tramite windows, a meno che non si usino "Permessi Speciali", non comunemente usato |
| 2 | Solo Scrittura | non disponibile tramite windows, a meno che non si usino "Permessi Speciali", non comunemente usato |
| 1 | Solo Esecuzione | non disponibile tramite windows, a meno che non si usino "Permessi Speciali", non comunemente usato |

In confronto alle Modalità Unix, quando vedi qualcosa come 644, dovresti dividere in tre elementi:

**6**  :  **4**  : **4**

Il primo numero rappresenta i permessi del **Proprietario**, il secondo rappresenta i permessi del ***Gruppo*** e il terzo, i permessi degli ***Altri***. L'equivalente Windows sarebbe;

* **Proprietario** (6) : **Lettura & Scrittura**
* **Gruppo** (4) : **Solo Lettura**
* **Altri** (4) : **Solo Lettura**

Si spera che questo esempio fornisca qualche intuizione su come correlare Modalità/Permessi Unix in Permessi/ACL di Windows. Questo documento non include soggetti più complessi come permessi *Efficace*, *Ereditato*, o *Speciali*. Nonostante la facilità d'uso di Windows, i meccanismi di Permessi e ACL di Microsoft sono in realtà ragionevolmente complessi e molto estesi, ma forse questo fornirà un riferimento rapido per cercare di alleviare alcune delle confusioni riguardanti le traduzioni di Permessi Unix e Windows.

