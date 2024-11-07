<!-- Filename: https://magazine.joomla.org/all-issues/april-2021/best-practices-to-secure-your-joomla-website / Display title: Migliori Pratiche  -->

## Articoli sulla Sicurezza

Esiste un numero significativo di articoli disponibili sulla sicurezza di Joomla che risalgono a molti anni fa. Purtroppo, molti di essi sono obsoleti e forse fuorvianti. Ad esempio, c'è una serie di articoli sulla Lista di Controllo della Sicurezza, non tutti realmente incentrati sulla sicurezza.

Questo articolo si basa su un articolo della rivista Joomla! Community Magazine scritto da Ahmad Moussa nell'edizione di aprile 2021.  

## Best Practice per Proteggere il tuo Sito Joomla

Il sistema di gestione dei contenuti (CMS) Joomla è diffuso su Internet grazie alla facilità d'uso e alla sua popolarità, essendo il secondo CMS più grande scaricato oltre 110 milioni di volte. Tuttavia, nonostante sia popolare, Joomla e tutti gli altri siti web, app, siti di eCommerce o altri CMS presentano rischi per la sicurezza. Non puoi evitarli, ma fortunatamente prendere le giuste precauzioni fin dall'inizio può garantire che il tuo sito sia protetto.

Abbiamo compilato per te questa guida completa e dettagliata sulla sicurezza di Joomla. Intende fornire passaggi facili da seguire per migliorare la sicurezza del tuo sito Joomla. Quindi, se mettere al sicuro il tuo sito Joomla da tutti i possibili attacchi è tra le tue priorità, ti consigliamo di leggerla. Tutti i suggerimenti menzionati in questo articolo servono a garantire che tu stia implementando le migliori pratiche di sicurezza e manutenzione per proteggere i tuoi beni più importanti online.

## 1. Scegliere Nomi Utente e Password Intelligenti

Sii intelligente nella scelta dei nomi utente e delle password per l'amministrazione di Joomla. Non utilizzare "admin" come nome utente e scegli una password complessa. Questo è probabilmente uno dei modi migliori per rafforzare la sicurezza di Joomla, e ironicamente è anche uno dei più semplici.

Utilizzare una password sicura è necessario per una buona sicurezza di Joomla. Assicurati che la tua password di accesso sia abbastanza lunga (8-14 caratteri) e includa alfabeti, numeri e simboli. Poiché le password sono sensibili alle maiuscole e minuscole, utilizzare sia lettere maiuscole che minuscole le rende ancora più forti. Inoltre, rendilo un'abitudine cambiare le password dell'amministratore almeno una volta al mese.

## 2. Pratica il Principio del Minimo Privilegio

Assicurati di comprendere i tre distinti gruppi di permessi:

1. Manager: Hanno il minimo accesso al backend di Joomla. Possono creare e modificare categorie e articoli. Hanno accesso al gestore media e possono caricare e rimuovere media. Non possono installare o rimuovere estensioni.
2. Amministratori: Hanno tutti i diritti dei Manager, oltre a qualche permesso aggiuntivo. Hanno accesso alla Gestione Utenti, Gestore Menu e Gestore Estensioni. Non possono accedere al menu Configurazione Globale di Joomla.
3. Super Utenti: Hanno pieno accesso al Backend di Joomla. Hanno tutti i diritti dei Manager e degli Amministratori, oltre all'accesso alla Configurazione Globale. Solo i Super Utenti possono aggiungere, modificare e rimuovere Super Utenti.

È importante distribuire questi ruoli con attenzione al tuo gruppo di utenti. Chiunque abbia il ruolo di Super Utente è in grado di eseguire qualsiasi azione all'interno del sistema Joomla. Se deleghi compiti a un membro del team che richiede meno permessi, assegna all'account del membro la descrizione di accesso minimo.  

## 3. Utilizzare l'Autenticazione a più fattori di Joomla

È altamente consigliato abilitare l'autenticazione a più fattori di Joomla, che aggiunge un ulteriore livello di sicurezza al tuo sito web Joomla. Tradizionalmente, quando vuoi accedere al tuo sito web, devi fornire il tuo nome utente e la tua password per identificarti nel sistema. Il problema più grande di questo approccio è che il tuo nome utente e la tua password possono essere rubati o indovinati. Pertanto, i plugin di autenticazione a più fattori di Joomla possono proteggere il tuo sito web dagli hacker aggiungendo un secondo livello di sicurezza. Ci sono cinque metodi diversi tra cui puoi scegliere dopo aver inserito il tuo nome utente.

## 4. Limitare l'Accesso al Backend Amministrativo di Joomla

È consigliabile limitare l'accesso al backend amministrativo di Joomla utilizzando il filtraggio IP, dato che è una risorsa sensibile. Questo può essere fatto anche per altre cartelle sensibili di Joomla seguendo i passaggi indicati di seguito:

Passo 1: Innanzitutto, crea un file .htaccess se non è già presente nella directory che desideri proteggere.

Passo 2: Aggiungi il seguente codice al file .htaccess:
   ```
   Order Deny, Allow
   Deny from all
   Allow from xx.xx.xx.xx
   ```

Passo 3: Inserisci l'indirizzo IP dedicato dal quale desideri consentire l'accesso al posto di xx.xx.xx.xx.

Maggiori informazioni su come limitare l'accesso alle directory tramite indirizzo IP usando
htaccess possono essere trovate in questo articolo della documentazione di Joomla!. Puoi anche utilizzare estensioni di sicurezza che possono limitare l'accesso al backend amministrativo di Joomla utilizzando la funzione di filtraggio IP e che includono molte altre funzionalità per rafforzare la sicurezza del tuo sito Joomla.

## 5. Utilizzare Connessioni FTP Sicure

Assicurati che le connessioni utilizzate per accedere ai file del tuo sito web Joomla siano sicure. Dovresti usare la crittografia SFTP se il tuo host la fornisce, oppure SSH. Se stai utilizzando un client FTP, il porto predefinito per SFTP è solitamente il 22.

Alcuni client FTP memorizzano le password in testo semplice o codificate sul tuo computer. Anche alcune password codificate possono essere convertite nuovamente all'originale. Raccomandiamo fortemente di non salvare le password FTP nel client per evitare di essere hackerati.

## 6. Effettuare Backup Regolari

Risparmia tempo preparandoti per lo scenario peggiore nel caso in cui il tuo sito web venga attaccato. Pertanto, è consigliato creare un backup completo e funzionante del tuo sito Joomla. Un backup funzionale può ripristinare il tuo sito web in pochi minuti dopo un attacco informatico.

I due componenti principali di un backup sono:

- Joomla Core e altri file importanti
- Il Database

Inoltre, i metodi di backup possono essere anche flessibili. Puoi effettuare un backup in due modi: Manuale e Automatizzato, come descritto di seguito:

### Processo Manuale

Il backup manuale del sito Joomla richiede due componenti: file e database. Per effettuare il backup dei file e della cartella Joomla, utilizza un'utilità FTP o il gestore di file nel caso in cui utilizzi hosting di terze parti.

I client FTP possono scaricare tutti i file uno per uno sul tuo computer locale. Tuttavia, questo processo può essere lento. Una volta scaricati i file, comprimi la cartella in un unico file zip e proteggilo con una password.

Il database può essere eseguito il backup esportando una copia del database sul tuo computer. Accedi al database che desideri esportare utilizzando phpMyAdmin. Clicca sul nome del database sul lato sinistro della pagina. Una volta cliccato sul tuo database Joomla, dovresti arrivare a una schermata con una scheda etichettata “Esporta”. Seleziona la scheda Esporta, quindi clicca sul pulsante etichettato "Vai". Poi salvalo in una posizione sicura.

### Processo Automatizzato

Per un backup automatizzato, un'estensione Joomla come Akeeba Backup può aiutare. Installa l'estensione Akeeba Backup sul tuo sito Joomla dopo averla scaricata dal sito ufficiale dello sviluppatore. Dopo il completamento dell'installazione, accedi al Dashboard dell'estensione e poi effettua il backup del tuo sito. Al termine del backup, verrai reindirizzato a una pagina. Qui, clicca su “Gestisci Backup”. Si aprirà una pagina contenente tutti i backup. Puoi scaricare il backup da qui e salvarlo localmente.

## 7. Mantieni Aggiornato il Tuo Sito Joomla

Aggiornare il tuo sito Joomla può fornire sicurezza e stabilità al sito. Inoltre, non tutti gli aggiornamenti sono aggiornamenti di versione completa del sito; alcuni aggiornamenti possono essere minori e sono semplicemente correzioni di bug, mentre altri sono aggiornamenti di versione.

Joomla ha un team di sicurezza dedicato che è noto per rilasciare patch rapidamente. Non applicare patch al tuo sito Joomla può renderlo vulnerabile agli attacchi hacker.

Per controllare se ci sono aggiornamenti per il tuo sito puoi fare quanto segue:

Passo 1: Accedi al tuo sito Joomla come amministratore

Passo 2: Successivamente, vai su Componenti>Aggiornamento di Joomla

Passo 3: Ora, Joomla verificherà se è disponibile un nuovo aggiornamento. Se mostra un nuovo aggiornamento, basta fare clic sull'opzione "Installa l'Aggiornamento".

Prima di aggiornare a una versione più recente di Joomla è necessario verificare alcune cose:

- Aggiornamento dei Temi: Controlla se i tuoi temi Joomla sono compatibili con la nuova versione di Joomla. Se non lo sono, chiedi all'autore del tema di aggiornarli o utilizza un'alternativa.
- Aggiornamento delle Estensioni: Verifica e assicurati che tutte le estensioni Joomla siano compatibili con la nuova versione di Joomla. Rimuovi tutte quelle che non sono compatibili. Per aggiornare le estensioni, vai su Estensioni>Gestione e fai clic su aggiorna.
- Svuota la Cache: Dopo aver aggiornato a una versione più recente di Joomla, svuota la cache dal tuo sito Joomla. Questo può essere fatto utilizzando la funzionalità integrata di Joomla.

## 8. Utilizzare Estensioni e Template di Terze Parti Affidabili:

Si raccomanda di utilizzare un numero minimo di estensioni sul tuo sito web per ottenere il livello ottimale di sicurezza di Joomla. L'uso di estensioni o template di terze parti non affidabili potrebbe introdurre vulnerabilità e influenzare le prestazioni del tuo sito Joomla. Non tutte le estensioni di terze parti sono prive di problemi; se puoi evitare di utilizzare un'estensione di terze parti, fallo! Scegli e utilizza estensioni e template professionali di aziende affidabili, e mantienili aggiornati per proteggere il tuo sito web.

## 9. Aggiorna la versione PHP del tuo sito Joomla

Proteggi il tuo sito da una varietà di attacchi informatici e rafforza la sicurezza del tuo sito Joomla aggiornando la versione PHP del tuo sito all'ultima versione stabile. Assicurati di selezionare una versione PHP compatibile con i tuoi template e le estensioni Joomla per evitare di compromettere il tuo sito. Esistono diversi modi per aggiornare la tua versione PHP. I principali sono trattati in un articolo nel numero di settembre 2020 del Joomla Community Magazine: Come faccio ad aggiornare la mia versione PHP?.

## 10. Rafforzare gli Header di Sicurezza HTTP

È altamente consigliato implementare o aggiornare gli header di sicurezza HTTP, poiché forniscono un livello di sicurezza per il tuo sito Joomla aiutando a mitigare attacchi e vulnerabilità di sicurezza. Solitamente, richiedono solo una piccola modifica di configurazione sul tuo server web. Questi header indicano al tuo browser come comportarsi quando gestisce il contenuto del tuo sito. Di seguito, sei comuni header di sicurezza HTTP da esaminare:

- Content-Security Policy
- X-XSS-Protection
- Strict-Transport-Security
- X-Frame-Options
- Public-Key-Pins
- X-Content-Type

## 11. Utilizza un'estensione di sicurezza per Joomla

È necessario limitare i tentativi di accesso al backend amministrativo di Joomla per evitare attacchi di forza bruta al tuo sito web Joomla. Questo può essere implementato tramite varie estensioni di sicurezza per Joomla che proteggono il backend amministrativo del sito web da tentativi di hacking. Puoi trovare queste estensioni nella categoria di sicurezza della lista delle estensioni di Joomla.

## 12. Scegli un Fornitore di Hosting Sicuro

Assicurati che il fornitore di hosting che scegli implementi misure di sicurezza per Joomla. Se opti per un hosting condiviso, assicurati che il subnetting sia implementato tenendo in considerazione la sicurezza di Joomla. Acquistare un fornitore di hosting condiviso economico potrebbe non essere un punto di partenza ideale, poiché il tuo sito potrebbe essere più lento, soggetto a spam a causa di una "cattiva vicinanza" di siti con bassa reputazione, e potrebbe essere compromesso se altri siti vengono hackerati. Inoltre, mentre scegli un piano di hosting, controlla vari parametri come personalizzazione, supporto, recensioni, ecc.

## 13. Utilizza SSL per potenziare la sicurezza di Joomla

È altamente consigliato installare un certificato SSL (Secure Socket Layer) sul tuo sito web poiché cripterà la comunicazione tra il tuo sito Joomla e i browser dei tuoi visitatori. Ottieni un certificato SSL da un'autorità di certificazione verificata e assicurati che tutto il tuo traffico HTTP venga reindirizzato a HTTPS. Per fare ciò, aggiungi il seguente codice al tuo file .htaccess:

```
# Reindirizza HTTP a HTTPS
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

## 14. Controllo di Sicurezza Frequente di Joomla

È estremamente importante scoprire le vulnerabilità prima che lo faccia un hacker, per mantenere il tuo sito web Joomla sicuro e protetto. Questo può essere fatto scegliendo uno strumento professionale per il controllo della sicurezza che ti può risparmiare molto tempo nella gestione dei tuoi siti web. Controlli di sicurezza meticolosi sono un ottimo modo per migliorare la sicurezza del tuo Joomla. Molti servizi lo fanno automatizzando compiti come la creazione di backup del sito web, la scansione per segni di intrusione e l'aggiornamento in blocco delle estensioni di cui ti fidi. Può anche eseguire una scansione del sito per l'uso delle migliori pratiche di sicurezza ed effettuare una scansione approfondita per cercare potenziali minacce alla sicurezza. Questi servizi utilizzano una combinazione ottimizzata di meccanismi manuali e automatizzati per scoprire vulnerabilità nel tuo sito Joomla.

## 15. Controlla i Messaggi Post-installazione

È altamente consigliato leggere tutti i messaggi post-installazione poiché il Team di Joomla ti fornisce informazioni importanti che richiedono la tua attenzione dopo l'aggiornamento o dopo aver installato Joomla per la prima volta. Questi messaggi contengono principalmente configurazioni di sicurezza di Joomla o modifiche ai file che dovrebbero essere effettuate manualmente e che un aggiornamento non può modificare.

## 16. Conoscere le Estensioni Vulnerabili

Controlla sempre il sito web della Vulnerable Extensions List e le sue pagine sui social media per conoscere gli ultimi rischi di sicurezza e le possibili patch. Si consiglia di disinstallare qualsiasi estensione elencata nella Vulnerable Extensions List per la quale non si conosca l'esistenza di una patch. Assicurati di aggiornare la tua estensione vulnerabile non appena è disponibile una patch. Se il tuo sito utilizza una versione vulnerabile di un'estensione che non ha un aggiornamento di patch, ti consigliamo di sostituirla.

## Conclusione

Poiché ci sarà sempre un rischio, la sicurezza di Joomla rimarrà un processo continuo, che richiede una valutazione frequente dei possibili vettori di attacco. I proprietari e gli amministratori dei siti web dovrebbero sempre migliorare la sicurezza del loro sito web per ridurre il rischio di compromissione.

*Tradotto da openai.com*

