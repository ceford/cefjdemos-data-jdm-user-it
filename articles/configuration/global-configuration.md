<!-- Filename: J4.x:Global_Configuration / Display title: Configurazione Globale   -->

## Panoramica

Durante l'installazione, un sito Joomla crea un file chiamato **configuration.php** nella radice del sito. Questo file contiene i valori delle variabili di configurazione che si applicano all'intero sito. Esempi includono il nome del sito e le credenziali del database inserite durante il processo di installazione. Ci sono molte altre variabili a cui vengono assegnati valori iniziali appropriati.

Il modulo di Configurazione Globale permette a un Super Utente di modificare le variabili di configurazione per soddisfare le esigenze del sito. Oltre alle variabili memorizzate in configuration.php, il modulo tiene traccia delle informazioni relative a Log, Filtraggio e Controllo degli Accessi, alcune delle quali sono memorizzate nel database. 

## Schermata

Il modulo di Configurazione Globale ha sei schede, alcune delle quali contengono lunghe liste di parametri. Utilizza il pulsante *Attiva/Disattiva Aiuto in Linea* nella barra degli strumenti per visualizzare più o meno informazioni su ciascun parametro.

![Scheda sito configurazione globale](../../../en/images/configuration/global-configuration-site-tab.png)

Alcuni parametri mostrano o nascondono altri parametri quando selezionati. Ad esempio, il pulsante **Sito Offline** mostra più campi quando è impostato su *Sì* rispetto a quando è impostato su *No*. Con l'aiuto in linea espanso, la maggior parte dei campi è sufficientemente ben documentata da non necessitare ulteriori spiegazioni qui, oltre ad alcune note aggiuntive per ciascuna scheda.

## Scheda Sito

### Pannello Sito

- **Nome del Sito** Questo è il nome del sito che appare nel modulo di accesso dell'Amministratore e nel link del Sito nella barra del Titolo. Modificalo secondo le tue esigenze.
- **Sito Offline** Esiste un [tutorial](jdocmanual?article=user/configuration/site-offline) separato su questo argomento.
- **Limite Elenchi Predefinito** imposta il numero massimo predefinito di elementi per pagina nelle visualizzazioni elenco. Per impostazione predefinita, questo parametro è impostato su 20, ma le visualizzazioni elenco di solito includono un elenco a discesa per selezionare altri valori che variano da 5 a 100. Meno valori sono più veloci da elaborare e richiedono meno scorrimento da parte dell'utente.

### Pannello Metadati

- **Descrizione Metadati Sito** Questa è la descrizione dei metadati predefinita utilizzata se tale descrizione non è specificata in un campo Descrizione Meta di un articolo o in un campo Descrizione Meta di un menu. Se tutti e tre sono vuoti, la descrizione dei metadati è omessa dall'output della pagina. I motori di ricerca spesso utilizzano questo per fornire un testo descrittivo per una pagina. Se assente, i motori di ricerca potrebbero utilizzare il testo dal contenuto della pagina, che potrebbe essere inappropriato. Si raccomanda una descrizione dello scopo del sito di circa 20 parole.
- **Diritti sui Contenuti** imposta l'entry metadata *diritti*. Se appropriato, descrivi qui quali diritti hanno altri nell'uso di questo contenuto. Questa voce nei metadati viene omessa dalle pagine web se questa voce è vuota. Esempio: Licenza Creative Commons Attribution 4.0 International (vedi il [Scegli Licenza Creative Commons](https://creativecommons.org/choose/)).

### Pannello SEO

SEO è un acronimo per *Search Engine Optimisation* (Ottimizzazione per i Motori di Ricerca). Le impostazioni in questo gruppo alterano il formato degli URL per le pagine nel sito web e questo può avere un effetto significativo sul posizionamento nelle ricerche delle singole pagine e dell'intero sito. Gli URL SEO sono più leggibili per gli esseri umani.

**Suggerimento** Dopo aver apportato qualsiasi modifica alle impostazioni in questo gruppo, aggiorna le pagine del sito web già aperte nel tuo browser web (di solito Ctrl+R o Cmd+R faranno questo). La mancanza di aggiornamento può significare che il formato dei link web interni al sito non corrisponde più a quello che Joomla si aspetta e quindi dare l'impressione di collegamenti interrotti.

**Suggerimento** Se possibile, evita di modificare le Impostazioni SEO una volta che un sito web è consolidato. Farlo potrebbe causare collegamenti interrotti da altri siti e forse una temporanea diminuzione nel posizionamento nei motori di ricerca.

- **Alias Unicode** Cambiare questo parametro non cambia retroattivamente gli alias, ma cambia solo il comportamento della generazione automatica degli alias per la modifica e la creazione di contenuti futuri. *Traslitterazione* (No) è l'impostazione predefinita.

### Pannello Cookie

- **Dominio Cookie** Sostituisce il dominio dei cookie predefinito del sito con il dominio aggiunto qui. La situazione più probabile in cui questo sarebbe necessario è quando il sito Joomla è "collegato" con altri siti (ad es. forum o e-commerce) in sotto-domini del sito Joomla. Il dominio del cookie predefinito potrebbe essere come `www.esempio.com`, ma usando `.esempio.com` (nota il punto iniziale) qui consegnerà cookie validi per qualsiasi sotto-dominio di esempio.com.
- **Percorso Cookie** Sostituisce il percorso predefinito del sito per cui il cookie è valido con il percorso aggiunto qui. Questo potrebbe essere necessario se hai diverse installazioni di Joomla in cartelle sorelle.

## Scheda del sistema

![Scheda del sistema di configurazione globale](../../../en/images/configuration/global-configuration-system-tab.png)

### Pannello di debug

Gli elementi in questo pannello sono ben spiegati dall'aiuto in linea. Tuttavia, se si riscontra un problema che disabilita l'accesso normale all'interfaccia di amministrazione, potrebbe essere necessario impostare Debug System modificando configuration.php con un editor di testo. Sulla maggior parte dei sistemi di hosting basati su Linux, i permessi del file sono impostati su 444, il che impedisce di salvare con un editor di testo. Cambiare il permesso a 644 prima di modificare. Quindi impostare \$debug = `true`; e impostare \$error_reporting = `'maximum'`; e salvare. Dovresti quindi ottenere un tracciato dello stack che identifica esattamente dove si verifica il problema. Puoi usare questo per cercare aiuto nei Forum. La maggior parte dei problemi sorgono da estensioni di terze parti incompatibili o da problemi con l'ambiente di hosting.

## Scheda Server

![Scheda server configurazione globale](../../../en/images/configuration/global-configuration-server-tab.png)

### Pannello di posta

Un sito Joomla dovrebbe essere in grado di inviare email in uscita. Tra le altre cose, invierà messaggi automatici al proprietario del sito quando sono disponibili aggiornamenti. Tuttavia, alcuni servizi di hosting limitano i metodi con cui le email in uscita possono essere inviate.

#### Invia email di prova

Prima di Joomla 5.3, il pulsante **Invia email di prova** inviava un messaggio all'indirizzo configurato nel campo **Email del mittente**. Dalla versione 5.3, l'email di prova viene inviata direttamente all'indirizzo email dell'amministratore connesso.

- Prova prima PHP Mail e seleziona il pulsante *Invia Mail di Test*. Se l'email arriva sei a posto. Altrimenti:
- Prova l'opzione Sendmail. Se non funziona:
- Prova l'opzione SMTP. Questa deve essere configurata per un server di posta specifico. Potrebbe essere uno fornito dal tuo servizio di hosting. Potrebbe essere un account GMail.
- **SMTP Host** Il nome host del server SMTP (ad es.
  *smtp.example.com*).
  - **SMTP Port** La porta da utilizzare quando ci si connette al server SMTP.
    Di solito sarà *25* quando la Sicurezza SMTP è impostata su *None*, oppure
    *465* o *587* quando la Sicurezza SMTP è impostata su `SSL/TLS` o `STARTTLS`.
    Chiedi al tuo fornitore di servizi SMTP quale porta utilizzare.
  - **SMTP Security** Il tipo di sicurezza richiesta dal server SMTP:
    *None*, *SSL/TLS* o *STARTTLS*. Il valore predefinito è *None*.
  - **SMTP Authentication** Se il server SMTP esterno
    richiede o meno l'autenticazione prima di accettare email in uscita. Il
    valore predefinito è *No*.
  - **SMTP Username** Il nome utente da usare quando ci si connette al
    server SMTP in modalità SSL o TLS. Può essere lasciato vuoto se non è presente
    l'autenticazione SMTP.
  - **SMTP Password** La password da usare quando ci si connette al
    server SMTP in modalità SSL o TLS. Può essere lasciata vuota se non è presente
    l'autenticazione SMTP.

### Utilizzare Gmail come Server di Posta

Se hai un account Gmail funzionante, puoi utilizzare Gmail come tuo
server di posta configurandolo nella configurazione globale. Nella scheda server impostare quanto segue:

- Mailer: SMTP
- SMTP Host: smtp.gmail.com
- SMTP Port: 465
- SMTP Security: SSL/TLS
- SMTP Authentication: Sì
- Impostare le due righe successive con le tue informazioni. È necessario utilizzare una password specifica per l'applicazione (ASP), descritta di seguito.
- SMTP Username: il tuo nome utente gmail
- SMTP Password: la password specifica per l'app (ASP) che hai generato,
  descritta di seguito.

Le seguenti sono combinazioni di configurazione funzionanti:

- SMTP Port: 587
- SMTP Security: STARTTLS
- SMTP Port: 25
- SMTP Security: STARTTLS

#### Note

- Il modulo SSL non necessita di essere abilitato in Apache.
- L'estensione OpenSSL deve essere abilitata in PHP. I dettagli si possono
  trovare sulla [pagina di installazione php.net](https://www.php.net/manual/en/openssl.installation.php).
- Se stai usando WAMP su Windows, il modulo openssl non è abilitato di
  default e devi abilitarlo. Per farlo:
  - Apri il file php.ini e rimuovi il punto e virgola `;` dall'inizio della linea `extension=php_openssl.dll` per decommentarla.
  - Salva il file php.ini e riavvia il servizio Apache.
- Se usi la verifica in due passaggi su Gmail, devi aggiungere una nuova
  password in Impostazioni - Account - Cambia impostazioni account - Altre
  Impostazioni Account Google - Sicurezza - Verifica in due passaggi - Gestisci le
  tue password specifiche per l'applicazione.
- Quando la nuova Password Specifica per l'Applicazione (ASP) viene presentata in
  gruppi di quattro caratteri separati da spazi, assicurati di **non inserire gli spazi** nella password SMTP nelle impostazioni del server di posta in Joomla.
- Password Specifiche per l'Applicazione (ASP): Vedi la pagina di supporto Google su come
  [Accedere con le Password per le App](https://support.google.com/accounts/answer/185833).
- Verifica in Due Passaggi: Vedi la pagina di supporto Google su come [Attivare la Verifica in Due Passaggi](https://support.google.com/accounts/answer/185839).

## Scheda di Registrazione

![Scheda del sito di configurazione globale](../../../en/images/configuration/global-configuration-logging-tab.png)

In condizioni normali, un sito Joomla dovrebbe avere il logging disabilitato. Se ci sono problemi, puoi abilitare il logging impostando il campo **Registra Quasi Tutto** su `Sì`. Il campo **Registra API Deprecate** è davvero solo per gli sviluppatori. Il campo **Percorso alla Cartella di Log** ti mostra dove cercare i log se hai impostato il logging per aiutare nel debug. I registri di errore che trovi lì sono solo quelli intercettati da Joomla. Potrebbero esserci altri errori che appariranno solo nei registri di errore del tuo server.

## La scheda Filtri Testo

![Scheda di configurazione globale del sito](../../../en/images/configuration/global-configuration-filters-tab.png)

Le impostazioni del filtro del testo verranno applicate a tutti i campi dell'editor di testo inviati dagli utenti nei gruppi selezionati. Queste opzioni di filtraggio forniscono un maggiore controllo sull'HTML che i tuoi fornitori di contenuti inviano. Puoi essere tanto severo o liberale quanto necessario per soddisfare le esigenze del tuo sito. Il filtraggio è facoltativo e le impostazioni predefinite offrono una buona protezione contro i markup comunemente associati ad attacchi sui siti web.

## Scheda Permessi

![Scheda configurazione globale del sito](../../../en/images/configuration/global-configuration-permissions-tab.png)

I permessi controllano ciò che gli utenti in ciascun Gruppo Utenti possono vedere e fare. Le voci nella scheda Permessi impostano i permessi predefiniti per il sito.

Ci sono descrizioni complete sull'uso delle impostazioni sotto questa scheda e sui principi generali di funzionamento e configurazione dei permessi in un [Tutorial sulla Lista di Controllo Accessi](jdocmanual?article=user/users/access-control).

*Tradotto da openai.com*

