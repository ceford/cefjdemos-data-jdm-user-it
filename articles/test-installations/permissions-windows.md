<!-- Filename: How_do_Windows_file_permissions_work? / Display title: Autorizzazioni dei file: Windows  -->

## Introduzione

Per coloro che stanno sviluppando o distribuendo i propri siti Joomla! in un ambiente Windows, è talvolta difficile ottenere informazioni pertinenti riguardo alle autorizzazioni. Sfortunatamente, è un dato di fatto che la maggior parte del servizio Web è offerto sotto Unix e che Unix è abbastanza ben documentato in questo ambiente. Speriamo che le seguenti informazioni aiutino a chiarire eventuali confusioni e forniscano anche una piccola guida.

## Panoramica sui server web Windows

Innanzitutto, discutiamo delle differenze tra i server. In generale, sembra che la maggior parte degli utenti di Windows utilizzi Apache (Win32) o Microsoft IIS. Questi due server web funzionano in modo molto diverso e utilizzano modelli di distribuzione leggermente diversi. Apache (Win32) generalmente viene eseguito sul computer host come l'Utente sotto il quale è stato installato, mentre IIS si installa sotto un utente specifico ma verrà eseguito sotto un nuovo utente installato *IUSR_*.

## Impostazioni predefinite dei permessi

Per impostazione predefinita, Unix tende a concedere pieno accesso solo all'utente *proprietario* di file e directory. Al contrario, Windows assegnerà per impostazione predefinita al gruppo *Everyone* (Tutti) tutte le autorizzazioni. La prima cosa che farà un buon amministratore di sistema Windows sarà rimuovere i diritti del gruppo *Everyone* per migliorare la sicurezza. Per i test su PC locali, probabilmente non è necessario, ma spiega perché, se *Everyone* non viene rimosso e si esegue uno script di verifica dei permessi o il controllo pre-installazione di Joomla!, si avranno pieno permesso di *Lettura, Scrittura ed Esecuzione*. Stai acquisendo i diritti del gruppo *Everyone*. 

## Microsoft Internet Information Server (IIS)

IIS è disponibile in due varianti principali, PWS (Personal WebServer) e IIS (Internet Information Server). Fondamentalmente, sono la stessa applicazione. PWS è semplicemente una versione ridotta di IIS progettata per ambienti desktop, mentre IIS è progettato per ambienti server. PWS ti limita a un singolo sito web principale, quindi le installazioni delle tue applicazioni generalmente saranno in sottodirectory del sito principale. IIS, invece, fornisce la funzionalità per eseguire Host Virtuali da queste directory, offrendo capacità multi-sito.

A causa delle diverse limitazioni funzionali, PWS non ha il *Permission Wizard* in quanto ritenuto non necessario. Solo un utente utilizzerà il server PWS. In IIS, molti utenti utilizzeranno il server, quindi sono necessarie assegnazioni di permessi diversi.

Una volta rimosso l'account *Everyone*, Windows IIS rimanendo con l'account *IUSR_** che ha diritti di alto livello per le directory del Web Server. Ora, un controllo dei permessi dovrebbe fornire risultati diversi. Solo l'account *IUSR_** ha pieni permessi e gli altri utenti dovrebbero ottenere solo *Sola Lettura* o nessun diritto. I diritti sono determinati da quali altri utenti sono stati assegnati manualmente ai diversi permessi per le directory IIS.

### Assegnazione dei Permessi

Assegnare i permessi in Windows è relativamente semplice, ma può risultare un po’ confusionario a volte. Clique destro sulla cartella o sul file appropriato. Selezionando *Proprietà* o *Condivisione e sicurezza* si entra nel pannello di gestione della sicurezza di Windows. Selezionando (cliccando una volta) qualsiasi nome utente elencato verranno visualizzati i diritti che quell'utente ha nella metà inferiore del pannello. Alcuni diritti potrebbero essere *grigiati*. Questi non sono disponibili, sia perché l'utente attuale (con cui sei loggato) non ha permessi sufficientemente alti per modificarli, sia perché sono ereditati dalla directory superiore e sono stati impostati per utilizzare i permessi del livello superiore della directory. (Questo è generalmente il meccanismo predefinito.)

Come puoi vedere, Windows utilizza lo schema di Permessi/Diritti seguente:

| # | Controllo | Consente #     |
| :---:        |:----   | :--- |
| 1.|  Controllo Totale | Consente: 1, 2, 3, 4, 5, 6, 7 |
| 2.| Modifica | Consente: 2, 3, 4, 5, 6 |- |
| 3.| Leggi ed Esegui | Consente: 3, 4  |- | 
| 4.| Lista Contenuti Cartella | Consente: 4 (ma non può eseguire programmi)  |- |
| 5.| Lettura | Consente: 5 (Implicito: 4) |- |
| 6.| Scrittura | Consente: 6 (Implicito:4 ) |- |
| 7.| Permessi Speciali | Consente: Combinazioni |

### Proprietà dei permessi file di Windows

I permessi dei file di Windows possono essere visti come aventi proprietà simili ai permessi dei file (Modalità) di UNIX o Linux. Sono solo rappresentati in modo diverso. Per esempio, se sei principalmente un utente Unix/Linux, probabilmente sei abituato ad avere i permessi rappresentati come 644/666 755/777, invece che essere descritti nei termini sopra. Quindi, quando usi 644, significa:

- Il proprietario di questo file può leggere e scrivere su di esso.
- Il gruppo del proprietario può leggere il file.
- Tutti gli altri possono leggere il file.

**Nota:** I permessi di Windows e Unix (Elenco di Controllo Accessi) non sono esattamente uguali; Windows non utilizza il meccanismo dei *Gruppi* allo stesso modo. Per questa discussione e in merito all'ambiente di hosting web, possono essere equiparati. Ah, ma in Windows i *Gruppi* non sono usati e *Everyone* dovrebbe essere stato rimosso. Qui Windows e Unix non sono esattamente uguali, ma quello che si può fare è *correlare* o *associare* significati equivalenti.

Questo schema non ti fornirà realmente una guida specifica su permessi per Windows o NTFS ma più una comprensione di come i permessi in stile UNIX/Linux comunemente citati si correlano su una macchina con un file system NTFS. I file che sono posizionati nella cartella radice `www` o `public_html`, o qualsiasi directory a cui puntano il tuo sito (`www.dominio.com` o `localhost`) sul tuo disco rigido dovrebbero appartenere al tuo account utente, ma solo se quell'utente non è considerato un utente privilegiato come *Administrator* su Windows o *root* su UNIX/Linux. Questi account permettono un accesso eccessivo e non dovrebbero mai essere usati per l'uso quotidiano.

### Migliori Pratiche

Le pratiche comuni di sicurezza suggeriscono che tutti i **file** dovrebbero avere i seguenti permessi.

- **Proprietario** Lettura & Scrittura
- **Gruppo** Sola Lettura
- **Altri** Sola Lettura

Tutte le **directory/cartelle** dovrebbero avere i seguenti permessi.

- **Proprietario** Lettura, Scrittura & Esecuzione
- **Gruppo** Lettura & Esecuzione
- **Altri** Lettura & Esecuzione

Si può discutere che questa non sia necessariamente la massima sicurezza, ma deve essere trovato un equilibrio tra sicurezza, funzionalità e manutenibilità.

Windows, a differenza di Unix, non mantiene un singolo ACL per *Esecuzione*, ma semplicemente fornisce l'ACL combinato *Lettura & Esecuzione*, che non implica *Scrittura*. L'ACL *Lettura & Esecuzione* implica però *Lista Contenuti Directory*. Quindi, se hai solo permessi *Lettura & Scrittura* su una directory ma non *Esecuzione* non sarai in grado di vedere i contenuti della directory e potresti anche avere problemi quando tenterai di eseguire il file tramite un browser web. Una piccola comprensione dei permessi UNIX/Linux è necessaria per correlare/associarli pienamente ai permessi Windows. La tabella seguente dovrebbe aiutare:

| Modalità Unix   | ACL Windows | Commenti|
|:-----------:| :----   | :--- |
| 7 | Modifica| Lettura, Scrittura & Esecuzione, dovresti essere il proprietario di questo file | 
| 6 | Lettura & Scrittura | | 
| 5 | Lettura & Esecuzione| usato per la maggior parte delle applicazioni | 
| 4 | Sola Lettura | la sicurezza tramite l’oscuramento non è una buona pratica | 
| 3 | Scrittura & Esecuzione | non disponibile tramite Windows, a meno che non siano usati Permessi *Speciali*, non comunemente usato | 
| 2 | Sola Scrittura | non disponibile tramite Windows, a meno che non siano usati Permessi *Speciali*, non comunemente usato | 
| 1 | Solo Esecuzione | (non disponibile tramite Windows, a meno che non siano usati Permessi *Speciali*, non comunemente usato) |

In confronto alle modalità Unix, quando vedi qualcosa come 644, dividi quello in tre elementi:

Il primo numero rappresenta i permessi del Proprietario, il secondo rappresenta i permessi del Gruppo e il terzo, i permessi degli Altri. L'equivalente in Windows sarebbe:

- **Proprietario** (6) Lettura & Scrittura
- **Gruppo** (4) Sola Lettura
- **Altri** (4) Sola Lettura

Si spera che questo esempio fornisca qualche intuizione su come correlare le Modalità/Permessi Unix nei Permessi/ACL di Windows. Questo documento non include argomenti più complessi come permessi *Effettivi*, *Ereditati*, o *Speciali*. Nonostante la facilità d'uso di Windows, i meccanismi di Permessi e ACL di Microsoft sono in realtà ragionevolmente complessi e molto estesi, ma questo potrebbe semplicemente darti un rapido riferimento per cercare di alleviare parte della confusione che circonda le traduzioni dei Permessi di Unix e Windows.

*Tradotto da openai.com*

