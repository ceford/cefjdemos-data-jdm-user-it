<!-- Filename: Visual_Studio_Code_Primer / Display title: Introduzione a Visual Studio Code -->

## VS Code - Un Popolare IDE Gratuito

Da Wikipedia:

> Visual Studio Code, comunemente noto come VS Code, è un editor di 
> codice sorgente creato da Microsoft per Windows, Linux e macOS. 
> Le funzionalità includono supporto per il debugging, evidenziazione 
> della sintassi, completamento intelligente del codice, snippet, 
> refactoring del codice e Git integrato. Gli utenti possono cambiare 
> il tema, le scorciatoie da tastiera, le preferenze e installare estensioni 
> che aggiungono funzionalità aggiuntive.

## Installazione

La pagina predefinita del sito di VS Code ha un menu a tendina per ciascuna piattaforma supportata. È probabile che la tua piattaforma sia già selezionata. Quindi scarica e installa, e sei pronto per iniziare.

### Prime nozioni

La pagina *Prime nozioni* di VS Code ha alcuni elementi *Inizia*, un elenco di elementi *Recenti*, e un breve elenco di *Percorsi guidati*. Se sei completamente nuovo a VS Code, si consiglia di dare un'occhiata a questi contenuti. Richiedono solo pochi minuti.

La Documentazione di VS Code è disponibile dal menu *Aiuto / Documentazione*. I [Video Introduttivi](https://code.visualstudio.com/docs/getstarted/introvideos) valgono assolutamente la pena di essere visti. Ognuno dura da 2 a 6 minuti e offre un'eccellente introduzione alle funzionalità di VS Code.

La documentazione ufficiale è il posto giusto dove andare se desideri cercare informazioni specifiche.

### Estensioni VS Code

VS Code può essere utilizzato per qualsiasi tipo di testo, inclusa una vasta gamma di linguaggi di programmazione. Funziona con JavaScript senza aggiungere estensioni. Altri linguaggi vengono rilevati dal contesto, quindi se inizi a creare e salvare codice PHP è probabile che ti venga chiesto di installare un pacchetto di Supporto PHP.

Clicca sull'icona delle *Estensioni* nella *Barra delle attività* a sinistra per vedere cosa hai installato e cosa è consigliato. Avrai bisogno dell'estensione PHP Debug!

### Layout dello Schermo di VS Code

Alcuni termini utilizzati nelle istruzioni successive:

- **Barra delle attività** la barra stretta a sinistra dello schermo. Seleziona qualsiasi icona per aprire o chiudere la Barra laterale Principale.
- **Barra laterale Principale** quando è aperta mostra i dettagli dell'attività selezionata.
- **Barra di stato** nella parte inferiore dello schermo. Mostra cosa sta succedendo.
- **Pannello** un'area sotto gli editor di testo per visualizzare altre informazioni.

Seleziona un'icona di layout in alto a destra per aprire o chiudere una qualsiasi di queste sezioni.

## Creare un'estensione Joomla

Per creare un'estensione, il tuo obiettivo è creare un file zip che puoi installare in un sito Joomla funzionante. Quindi, hai bisogno di una cartella per contenere il tuo codice. Questa dovrebbe essere all'interno del tuo spazio personale sul tuo laptop o computer desktop utilizzato per lo sviluppo locale. Non dovrebbe essere nella struttura del tuo sito web. Ad esempio, potresti usare *~/jextensions* per contenere sottocartelle per diverse estensioni. Io uso *~/git* perché è breve e facile da scrivere anche se potenzialmente confuso perché ogni sottocartella utilizza un repository git separato.

### Codice di esempio

Se desideri un po' di codice di esempio su cui lavorare, c'è un'estensione disponibile su GitHub chiamata *mod_debugme*. Come suggerisce il nome, è un modulo con alcuni bug. Oltre al codice del modulo, c'è un file *build.xml* che illustra un modo per automatizzare la creazione per il test e la creazione di un file zip.

Il modulo è progettato per mostrare i prossimi (3 per impostazione predefinita) eventi (compleanni) da un elenco memorizzato in una tabella del database. Potresti immaginare che questo venga utilizzato in un sito di ufficio o di famiglia con l'aspettativa di torta.

Potrebbe essere meglio iniziare utilizzando i comandi git dalla riga di comando. Prima crea una cartella per il tuo codice e poi clona il repository remoto:
```sh
    mkdir ~/git
    cd ~/git
    git clone https://github.com/ceford/j4xdemos-mod-debugme
```
La risposta dovrebbe richiedere solo pochi secondi:
```sh
    Cloning into 'j4xdemos-mod-debugme'...
    remote: Enumerating objects: 23, done.
    remote: Counting objects: 100% (23/23), done.
    remote: Compressing objects: 100% (16/16), done.
    remote: Total 23 (delta 3), reused 23 (delta 3), pack-reused 0
    Unpacking objects: 100% (23/23), done.
```
Dovresti prendere un momento per guardare il contenuto della cartella:
```sh
    cd j4xdemos-mod-debugme
    ls -al
    total 16
    drwxr-xr-x   6 ceford  staff   192  2 Sep 17:48 .
    drwxr-xr-x   3 ceford  staff    96  2 Sep 17:48 ..
    drwxr-xr-x  12 ceford  staff   384  2 Sep 17:48 .git
    -rw-r--r--   1 ceford  staff  1402  2 Sep 17:48 README.md
    -rw-r--r--   1 ceford  staff   927  2 Sep 17:48 build.xml
    drwxr-xr-x   8 ceford  staff   256  2 Sep 17:48 mod_debugme
```
La cartella *.git* contiene informazioni sul repo. Il file *README.md* è un documento markdown che descrive questo repo. Il file *build.xml* è un file utilizzato per creare l'estensione con uno strumento esterno, Phing, descritto più avanti. La cartella *mod_debugme* contiene il codice dell'estensione.

### Installare in Joomla

Comprimi la cartella dell'estensione per creare un file zip installabile:
```sh
    zip -r mod_debugme.zip mod_debugme
```
Ora puoi installare il file zip nel sito Joomla che utilizzi per il test. Dopo l'installazione, devi creare un modulo del sito e assegnarlo a una posizione del modulo. Poiché è un modulo con errori, potresti assegnarlo a una posizione su *Tutte le pagine* mentre ci lavori; oppure potresti assegnarlo a una posizione su una singola pagina; oppure potresti posizionarlo in un articolo che ha un suo elemento di menu.

Dopo l'installazione, elimina il file zip.

### Attivare la modalità di Debug

Nella Configurazione Globale di Joomla, imposta *Debug System* su *Yes* e *Error Reporting* su *Maximum*.

Quando apri una pagina contenente il modulo difettoso vedrai un tracciamento dello stack che ti indica dove è stato attivato un errore.

![tracciamento dello stack vscode](../../../en/images/test-installations/vscode-primer-stack-trace.png)

A volte l'errore di codifica è sulla prima linea del tracciamento dello stack. Altrimenti, se l'errore è attivato nel codice della libreria, ad esempio passando dati non validi a una funzione del database, l'errore di codifica potrebbe essere più in basso nella lista delle chiamate di funzione.

## Apri la Cartella delle Estensioni in VS Code

In VS Code, usa l'elemento di menu File / Apri Cartella per individuare e aprire la cartella contenente la tua copia locale del codice dell'estensione *mod_debugme*. Dovresti vedere qualcosa di simile al seguente:

![visualizzazione cartella vscode](../../../en/images/test-installations/vscode-primer-screen.png)

Potresti essere in grado di diagnosticare il problema semplicemente leggendo il codice. Nel caso dell'errore *Classe "DebugHelper" non trovata*, vedrai che una dichiarazione *use* è stata commentata qualche riga prima. Dimenticare di inserire una dichiarazione *use* è un errore comune durante lo sviluppo iniziale!

Correggi quel problema e poi comprimi e installa di nuovo il modulo. Quel passaggio può diventare un po' noioso quando si hanno più problemi. È qui che gli strumenti di build diventano utili.

## Phing

Phing è uno strumento da riga di comando, disponibile per tutte le piattaforme, utilizzato per costruire pacchetti software utilizzando istruzioni memorizzate in un file xml, chiamato build.xml per impostazione predefinita. Per lavorare con il codice dell'estensione può essere utilizzato per fare due cose:

- copiare i file modificati dalla cartella sorgente della tua estensione ai luoghi corretti nella cartella del tuo sito web.
- generare un nuovo file zip per nuove installazioni.

Scarica e installa Phing. Altri strumenti di build sono disponibili! Puoi installare Phing nella tua cartella bin personale o in una cartella bin di sistema. Devi annotare il percorso del tuo codice Phing. In questo esempio è *~/bin/phing-latest.phar*. Puoi provarlo dalla riga di comando dopo esserti spostato nella cartella contenente il codice della tua estensione:
```sh
    cd ~/git/j4xdemos-mod-debugme
    php ~/bin/phing-latest.phar
```
Risposta:
```sh
    Buildfile: /Users/ceford/git/j4xdemos-mod-debugme/build.xml

    mod_debugme > principale:
          ... Qualsiasi file copiato verrà menzionato qui
          [zip] Creazione zip: /Users/ceford/zips/mod_debugme.zip

    COSTRUZIONE TERMINATA

    Tempo totale: 0,0863 secondi
```

## Compiti di VS Code

Per eseguire Phing all'interno di VS Code, è necessario creare un file *tasks.json* nella cartella *.vscode* nella radice della cartella *j4xdemos-mod-debugme*. Se quest'ultima non esiste, prima crearla. Quindi crea il file *tasks.json* e inserisci il seguente codice:

```json
    {
        // Vedi https://go.microsoft.com/fwlink/?LinkId=733558
        // per la documentazione sul formato del file tasks.json
        "version": "2.0.0",
        "tasks": [
          {
            "label": "Build mod_debugme",
            "type": "shell",
            "command": "php ~/bin/phing-latest.phar",
            "windows": {
              "command": "php ~/bin/phing-latest.phar"
            },
            "group": "build",
            "presentation": {
              "reveal": "always",
              "panel": "shared"
            }
          }
        ]
    }
```

Gli utenti Windows devono correggere il comando specifico per Windows. Ora puoi costruire l'estensione usando il menu *Terminale / Esegui attività di build*. Il risultato del comando dovrebbe apparire nel Pannello del Terminale sotto l'area Modifica.

```sh
      *  Esecuzione attività: php ~/bin/phing-latest.phar

    Buildfile: /Users/ceford/git/gitdemo/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:

          [zip] Niente da fare: /Users/ceford/zips/mod_debugme.zip è aggiornato.

    COSTRUZIONE TERMINATA

    Tempo totale: 0.1031 secondi

     *  Il terminale sarà riutilizzato dalle attività, premi un tasto per chiuderlo.
```

Possono esserci messaggi di errore incomprensibili. La causa più probabile è avere percorsi non validi alle cartelle nel file *build.xml* o una cartella non è stata creata. Solo un altro tipo di problema da debug!

## Debugging

Dovresti essere in grado di correggere il primo bug tramite l'ispezione del codice. Problemi più complicati richiedono di eseguire il codice con il debugger. Questo ti consente di ispezionare le variabili per vedere se contengono i valori che ti aspetti, ad esempio quando si passano argomenti a funzioni di libreria.

### Impostazioni di *php.ini*

Per configurare il debugging con Xdebug devi fare alcune modifiche nella parte superiore del tuo file *php.ini*.
```ini
    zend_extension="xdebug.so"
    xdebug.mode="debug"
    xdebug.client_port=9003
    xdebug.start_with_request = yes
```
Dopo aver salvato tutte le modifiche, riavvia il tuo server Apache.

### Aggiungi Finestra del Sito Web

La tua cartella di estensione contiene solo pochi file, le ***sorgenti*** dei file installati nel tuo sito web. Il debugging in tempo reale comporta la definizione di breakpoint nei tuoi file del ***sito***, quindi hai bisogno di accedere a quei file. Potresti usare il menu *File / Add Folder to Workspace...* per aggiungere la cartella del sito al tuo Workspace. Tuttavia, è molto probabile che finirai per apportare modifiche ai file del sito invece che ai file sorgente. Quindi è probabilmente meglio aprire una finestra separata di VS Code per il debugging.

- **Apri una nuova finestra:** Dal menu di VS Code, seleziona *File / New Window* e seleziona la cartella contenente il tuo sito web Joomla.
- **Apri cartella:** Nella finestra appena aperta, seleziona *File / Open Folder...* dal menu di VS Code. Trova la tua cartella del sito web e selezionala. Dovresti vedere un elenco di tutti i file del tuo sito web Joomla nella barra laterale principale.

### Configurazione di Avvio

Per fare in modo che il debug funzioni effettivamente in VS Code, hai bisogno di una configurazione di avvio. Nella root del tuo sito web crea una cartella chiamata *.vscode* (nota il punto di apertura) contenente un file chiamato *launch.json* con il seguente contenuto:
```json
    {
        "configurations": [
            {
                "name": "Listen for XDebug",
                "type": "php",
                "request": "launch",
                "hostname": "0.0.0.0",
                "port": 9003,
                "stopOnEntry": true,
                "pathMappings": {
                    "/Users/ceford/Sites/j421rc2": "${workspaceFolder}"
                }
            }
        ]
    }
```
Ricorda di sostituire l'elemento pathMappings in questo esempio con i pathMappings effettivi sul tuo sito. L'elemento stopOnEntry fermerà l'esecuzione alla primissima riga di codice PHP eseguito.

### Debug *mod_debugme*

Ora sei pronto a trovare e correggere i bug nel modulo installato.

- **Trova il codice del modulo:** Trova il primo bug alla riga 16 di JROOT/modules/mod_debugme/mod_debugme.php.
- **Imposta breakpoint:** Clicca nello spazio alla sinistra del numero 16. Apparirà un cerchio rosso tenue mentre ti sposti sopra e diventerà completamente rosso dopo aver cliccato per indicare che è stato impostato un breakpoint.
- **Avvia debug:** Dal menu di VS Code seleziona *Run / Start Debugging*. Nel tuo browser ricarica il sito. La tua finestra di VS Code dovrebbe riapparire con il codice fermo alla prima riga del file *index.php* del sito. In alto nella schermata ci sono alcune icone per controllare il processo di debug. Dovrebbero essere auto-esplicative. In caso contrario, cercale nella Guida / Documentazione di VS Code.
- **Continua:** Seleziona il pulsante continua - il codice continuerà fino al tuo primo breakpoint. Esamina il codice per vedere quale sia il problema.
- **Passa sopra:** Se passi con il mouse su una variabile a cui è stato assegnato un valore apparirà un piccolo Tooltip che riassume gli attributi di quella variabile. Non c'è Tooltip per le variabili a cui non sono stati assegnati valori.
- **Variabili:** La colonna di sinistra contiene ulteriori informazioni sullo stato del codice al breakpoint. Ce ne sono troppe per coprirle qui. Esplorale come necessario!
- **Ferma Debugging:** È probabilmente meglio selezionare l'icona Continua, altrimenti la pagina web viene consegnata vuota. In alternativa potresti utilizzare il pulsante Stop o il menu Run / Stop Debugging.

### Correggi un Bug

**Ricorda:** Non correggere il bug nel codice del sito web! Correggilo nel codice sorgente!

Correggi il codice sorgente e poi utilizza *Terminal / Run Build Task...*.

Riavvia il debug.

### Suggerimenti

Alcuni problemi non così ovvi:

- Correggi il primo bug ma ancora si blocca su quella linea. Guarda in mod_debugme.xml per vedere dove è definito il src delle classi con namespace. Quando corretto nel sorgente è necessario reinstallare il file zip o eliminare *administrator/cache/autoload_psr4.php*. Quando assente, Joomla ricostruisce quel file dai file manifest. Ma se ha una voce errata o mancante non viene corretto fino a quando l'estensione non viene reinstallata.
- A volte è necessario impostare un breakpoint alcune righe prima della riga in cui si verifica l'errore, soprattutto se desideri verificare i valori passati alle chiamate di funzione.
- La tabella *xxx.yyy\\debugme* non esiste. Ah sì, il codice per creare una tabella all'installazione e rimuoverla alla disinstallazione non è mai stato creato. Dovrai eseguire una query sql in phpMyAdmin utilizzando il contenuto del file *mod\\debugme.sql*. Ricorda di cambiare *\#\\* nei nomi delle tabelle con il prefisso del tuo database. E quando ancora fallisce controlla il nome della tabella nel codice.

## Screenshot

Quando tutto è risolto, ecco cosa potresti vedere:

![visualizzazione del modulo risolto in vscode](../../../en/images/test-installations/vscode-primer-debugme-fixed.png)

Giorni speciali?  

## Riferimenti

Dalla documentazione di Joomla!: [Visual Studio Code](https://docs.joomla.org/Visual_Studio_Code) include anche la configurazione di altri strumenti, ad esempio CodeSniffer e PHPUnit.

*Tradotto da openai.com*

