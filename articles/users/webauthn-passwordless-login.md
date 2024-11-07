<!-- Filename: WebAuthn_Passwordless_Login / Display title: Accesso WebAuthn -->

## Accesso Senza Password con WebAuthn

L'Autenticazione Web, o WebAuthn in breve, consente a un utente di accedere in modo sicuro a un sito senza utilizzare una password, anche se è ancora necessario un nome utente. Utilizza una crittografia forte in un modo che è estremamente resistente ai problemi più comuni delle password:
* qualcuno l'ha indovinata (attacco a forza bruta)
* qualcuno l'ha intercettata (attacco man-in-the-middle)
* qualcuno ti ha ingannato nel rivelarla (attacco di phishing)
* qualcuno l'ha decifrata dopo aver ottenuto una copia dei dati del tuo database (attacchi SQL injection)
* qualcuno l'ha rubata.

WebAuthn non è solo molto sicuro; è anche molto user-friendly! Non devi più ricordare lunghe password o utilizzare un gestore di password. Tutto ciò di cui hai bisogno è un *autenticatore*, a volte chiamato anche *passkey*.

Un autenticatore può presentarsi in molte forme, fisiche o virtuali. Può essere una chiave hardware separata che si collega al tuo dispositivo tramite USB, Bluetooth o NFC. Può essere il tuo stesso dispositivo, che sblocca il suo autenticatore integrato con un PIN, un lettore di impronte digitali, una scansione facciale o un controllo biometrico simile.

Questa funzionalità già funziona su dispositivi Android e iOS/iPadOS e stiamo lavorando per abilitarla anche su Windows. Può persino essere il tuo telefono — attualmente è possibile con i telefoni Android ma questa funzionalità sta arrivando anche su dispositivi iOS / iPadOS.

WebAuthn funziona solo su HTTPS e solo quando il tuo sito utilizza un certificato valido e affidabile per esso. Non preoccuparti, non devi spendere soldi extra; servizi gratuiti come Let's Encrypt sono tipicamente integrati nei pannelli di controllo dell'hosting web e funzionano perfettamente con WebAuthn.

WebAuthn utilizza la crittografia delle chiavi pubbliche, la stessa tecnologia comprovata che mantiene sicuri i tuoi siti con HTTPS, le tue informazioni bancarie protette e così via. La chiave privata non lascia mai l'autenticatore. Il tuo sito memorizza solo una chiave pubblica. Anche se subisci una violazione dei dati, l'attaccante avrà solo una chiave pubblica praticamente inutile; ci vorrebbero migliaia o milioni di anni di CPU per decifrarla, rispetto a pochi minuti o ore necessari per decifrare l'hash di una password fissa che puoi ricordare.

WebAuthn è il futuro dell'autenticazione. Facile, sicuro e senza complicazioni. Tutto ciò che le password fisse non sono.

L'immagine seguente mostra un dispositivo hardware inserito nella porta USB di un computer portatile. È costato £15 a febbraio 2022.

![fotografia del dispositivo Hardware](../../../en/images/users/passwordless-login-hardware-device.jpg)

WebAuthn utilizza un plugin di sistema abilitato per default. Un pulsante di **Autenticazione Web** sarà presente nei moduli di accesso predefiniti di Joomla 4 e versioni successive, come illustrato nella schermata di accesso dell'Amministratore:

![form di login sicuro dell'amministratore](../../../en/images/users/passwordless-login-login-form.jpg)

## Configurazione utente

L'utente deve prima registrarsi con un normale Nome utente e Password. Dopo aver effettuato l'accesso, vai al modulo Profilo utente. Per un Amministratore:

- Seleziona **Menu utente → Modifica account → Autenticazione web W3C (WebAuthn) Login** per aprire il modulo, inizialmente senza autenticatori registrati.
- Seleziona **Aggiungi nuovo autenticator**

La presentazione esatta del passaggio successivo dipende dal tuo browser. Tipicamente, vedrai un avviso, un messaggio o una finestra che ti chiede di selezionare un tipo di autenticatore o, se stai utilizzando un autenticatore hardware collegato al tuo dispositivo, ti ricorda di premere il pulsante sull'autenticatore hardware. Per ragioni di sicurezza e pratiche, c'è un intervallo di tempo relativamente breve consentito per l'attivazione dell'autenticatore: 60 secondi.

![prompt hardware del login sicuro amministratore](../../../en/images/users/passwordless-login-hardware-propmpt.png)

Una volta sbloccato il tuo autenticatore, toccando un pulsante, scansionando la tua impronta digitale/faccia, inserendo un PIN o una combinazione dei precedenti a seconda del tuo autenticatore, il messaggio scompare, l'autenticatore è registrato e lo schermo appare come segue:

![autenticatore registrato del login sicuro amministratore](../../../en/images/users/passwordless-login-registered-authenticator.png)

È molto importante notare che puoi registrare o rimuovere gli autenticatori solo sul tuo account utente. Per motivi di sicurezza, anche un Superutente non è autorizzato a registrare, modificare o aggiungere autenticatori su altri account utente.

### Autenticatori

Puoi utilizzare qualsiasi autenticatore FIDO U2F o FIDO2. FIDO U2F è uno standard più vecchio che supporta una selezione più limitata e meno sicura di metodi crittografici. FIDO2 è lo standard più recente che supporta metodi crittografici molto più sicuri, incluso Elliptic Curve Cryptography, un metodo crittografico che si ritiene resistente anche al calcolo quantistico (se e quando diventerà una realtà pratica). Inoltre, gli autenticatori FIDO2 possono essere configurati per avere protezioni aggiuntive come un PIN o un controllo biometrico (ad es. scansione dell'impronta digitale), il che significa che anche se perdi il possesso fisico dell'autenticatore chi lo trova non può accedere ai tuoi siti.

Se stai cercando di acquistare un autenticatore hardware, puoi cercare "FIDO2" nel tuo marketplace preferito, come Amazon. Ci sono molte opzioni tra cui scegliere.

Puoi anche utilizzare una chiave FIDO software come Krypton come tuo autenticatore.

Molti dispositivi hanno autenticazione integrata conforme a FIDO2:

- Windows 10 e 11 hanno Windows Hello con un PIN, scanner di impronte digitali, fotocamera di riconoscimento facciale o una combinazione di chiave hardware e PIN. Il supporto per Windows Hello viene aggiunto al plugin con un obiettivo di rilascio di Joomla 4.2.0.
- macOS ha TouchID su tutti i laptop con chip T2 o quelli basati su Apple Silicon utilizzando il sensore TouchID integrato, così come tutti i desktop basati su Apple Silicon utilizzando la nuova tastiera Apple Aluminium con scanner di impronte digitali.
- iOS / iPadOS hanno TouchID su tutti i dispositivi con scanner di impronte digitali e FaceID su tutti i dispositivi più recenti con fotocamera infrarossa per proiezione di punti per FaceID.
- Alcuni dispositivi Android hanno uno scanner di impronte digitali o una fotocamera di riconoscimento facciale. Possono anche funzionare come autenticatore FIDO2, su Android 9 o successivi usando almeno Google Chrome.
- Possono essere disponibili anche altri dispositivi. Ad esempio, telefoni Android utilizzando ![caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Browser compatibili con WebAuthn

I browser basati su Chromium e Firefox supportano WebAuthn dall'inizio del 2019.

Safari e tutti i browser iOS/iPadOS (che sono, infatti, Safari con un'interfaccia diversa) supportano completamente WebAuthn da iOS/iPadOS 13, rilasciato alla fine del 2019.

Praticamente parlando, se il tuo sistema operativo e il tuo browser sono stati rilasciati dopo la metà del 2020, non dovresti avere problemi. Solo alcuni browser molto rari ancora non supportano WebAuthn.

## Autenticazione

Per accedere devi inserire il tuo nome utente nel campo Username del modulo di accesso.
Non è necessario inserire la tua password, ma se il tuo browser la inserisce al tuo posto, lasciala semplicemente così com'è. La password NON viene inviata al server quando il modulo viene inviato tramite il pulsante di Autenticazione Web.

Ne consegue che puoi accedere sia con il tuo Nome Utente e Password sia con Nome Utente e Autenticazione Web.

## Come Disabilitare il Plugin

Se non desideri consentire WebAuthn, vai semplicemente all'elenco dei plugin, trova System - WebAuthn Passwordless Login nel gruppo System e disabilitalo. Non ci sono parametri da impostare.

## Requisiti del Server

Affinché WebAuthn funzioni, devono essere soddisfatte le seguenti condizioni:

- HTTPS con un certificato valido e firmato. La maggior parte degli host
  consente l'uso gratuito di certificati emessi da Let's Encrypt. Questi
  funzionano perfettamente con WebAuthn.
- L'estensione OpenSSL per PHP deve essere installata e abilitata.
- L'estensione PHP GMP o l'estensione PHP BCmath deve essere installata e
  abilitata (è sufficiente una delle due).
- Idealmente, la libreria Sodium dovrebbe essere abilitata; abilita l'uso
  della crittografia a curve ellittiche sui dispositivi FIDO2 compatibili che,
  come abbiamo detto, è il metodo crittografico più sicuro.

## Domande Frequenti e Risoluzione dei Problemi

### Non riesco a vedere il pulsante di accesso “Autenticazione Web”

Non stai accedendo al tuo sito tramite HTTPS. WebAuthn è disponibile solo per siti HTTPS con un certificato valido. Questa è una precauzione di sicurezza integrata nello standard WebAuthn. Il plugin verifica effettivamente se il sito è accessibile tramite HTTPS utilizzando la classe Uri di Joomla. In rari casi in cui il server fornisce informazioni errate sul protocollo, potresti non vedere il pulsante anche se il tuo sito (afferma di essere) HTTPS. Lo stesso vale se hai modificato il tuo file configuration.php e hai impostato il parametro di configurazione opzionale \$live_site con un prefisso del protocollo http:// invece di https://.

Nota anche che moduli di login di terze parti e componenti che implementano il proprio modulo di login potrebbero non visualizzare ancora questi pulsanti. Abbiamo aggiunto nuova infrastruttura per supportarli, proprio come abbiamo dovuto fare in Joomla! 3.2 per supportare l'Autenticazione a Due Fattori.

### Devo ancora fornire un nome utente. WebAuthn non dovrebbe eliminare i nomi utente?

In realtà, no. L'attuale specifica di WebAuthn non fornisce la gestione dell'identità. I browser web ci richiedono di inviare loro un elenco di chiavi pubbliche accettabili di WebAuthn durante la fase di login. Ciò significa che abbiamo bisogno del tuo nome utente per recuperarle.

Detto ciò, l'uso di WebAuthn chiarisce finalmente che i nomi utente *non devono essere considerati segreti*. Sono considerati informazioni pubbliche che possono essere liberamente trasmesse a un avversario, proprio come le chiavi pubbliche memorizzate nel database del sito. L'unico segreto è memorizzato nell'autenticatore stesso e non lascia mai l'autenticatore!

### Ho registrato un autenticatore ma provando ad accedere mi viene detto che non l'ho fatto. È un bug?

È un bug, ma non del plugin WebAuthn stesso.

Uno o più plugin sul tuo sito generano Avvisi, Avvertenze o Errori PHP, corrompendo così la risposta inviata dal tuo server. Di conseguenza, il JavaScript sulla pagina non può analizzare la risposta del server e non è sicuro se uno qualsiasi degli autenticatori sia registrato dall'utente.

Vai al backend del tuo sito, Sistema, Configurazione Globale e imposta Rapporto Errori su Nessuno. Nella maggior parte dei casi di plugin core e di terze parti che si comportano male, questo è sufficiente. In caso contrario, esamina l'output della richiesta utilizzando gli strumenti per sviluppatori del tuo browser per vedere cosa sta corrompendo la richiesta.

### Non c'è suggerimento su Safari per utilizzare il mio autenticatore

Questo non dovrebbe più accadere con iOS 13, iPadOS 13 e macOS Catalina o qualsiasi versione successiva.

Questo è un bug di Safari nelle versioni più vecchie di Safari. Le versioni più vecchie di Safari includevano il supporto per WebAuthn solo come funzione sperimentale e non del tutto completata.

### Non riesco a utilizzare un sensore biometrico (TouchID, impronta digitale, Windows Hello)

Alcuni vecchi browser basati su Chromium (eccezion fatta per Google Chrome proprio) non avevano pieno supporto per gli autenticatori integrati. Si bloccavano o si piantavano quando si tentava di utilizzarne uno. Questi problemi sono stati risolti in questi browser attorno alla metà del 2020.

Se stai usando Windows, ricorda che il tuo dispositivo DEVE avere un chip Trusted Platform Module (TPM) e deve essere abilitato nel BIOS. Avere solo un sensore biometrico compatibile con Windows Hello non è sufficiente. Questa è una precauzione di sicurezza nello standard WebAuthn stesso: le informazioni dell'autenticatore devono essere elaborate utilizzando hardware sicuro e resistente alle manomissioni per evitare la sovversione della chiave (ad es. malware che girano sul computer non possono rubare la chiave utilizzata per l'autenticazione).

Infine, tieni presente che il supporto di Windows Hello è ancora in lavorazione e verrà rilasciato con Joomla 4.2.

### Se posso usare un autenticatore software, perché dovrei preoccuparmi di un token hardware?

Il fulcro di WebAuthn è l'assoluta segretezza della chiave privata. È conosciuta solo dall'autenticatore e dovrebbe essere impossibile comunicarla al mondo esterno.

Nel caso di un autenticatore hardware, sia esso un dispositivo hardware discreto o un TPM / Secure Enclave integrato nel tuo dispositivo, questo è assicurato dalla natura stessa di quell'hardware.

Un autenticatore software genera una chiave segreta e la memorizza nel filesystem. Tuttavia, è ancora un'applicazione software regolare che gira all'interno del tuo sistema operativo normale, sia esso quello del tuo telefono che del tuo computer. Di conseguenza, è soggetto a diverse classi di attacchi che possono essere utilizzati per rubare informazioni in modo surrettizio (problemi di sicurezza nel software stesso, malware che sfruttano vulnerabilità di tipo Spectre nei moderni CPU ecc).

Pertanto, un autenticatore software è molto più comodo e sicuro di una password normale, ma un autenticatore hardware offre la migliore sicurezza. Scegli il tuo autenticatore in base al tuo budget e alle tue esigenze di sicurezza.

Considerando che il prezzo di una chiave FIDO – che è compatibile con WebAuthn – è inferiore a 10 € su Amazon, puoi utilizzare un autenticatore hardware nella maggior parte dei casi di uso pratico.

### Perché le credenziali sono criptate nel database? Non è esagerato?

L'unica cosa memorizzata nel database è la chiave pubblica restituita dall'autenticatore quando eseguiamo la cerimonia di attestazione (questo è il nome formale di registrazione di un autenticatore secondo la specifica WebAuthn). Essendo una chiave pubblica, non necessita di protezione dalla lettura. Anche se un utente non autorizzato riuscisse a leggere queste informazioni, non sarebbe in grado di impersonare l'autenticatore, ad esempio clonandolo.

Tuttavia, se un utente malintenzionato avesse accesso in scrittura solo alla tabella del database `#__webauthn_credentials`, senza accesso in lettura al filesystem e senza accesso in scrittura a nessun'altra tabella, potrebbe concepibilmente **aggiungere** il proprio autenticatore, riuscendo così a impersonare l'utente mirato sul sistema. Si tratta di un attacco molto teorico poiché essi avrebbero anche bisogno di conoscere il gestore dell'utente per l'utente che stanno attaccando, il che è più difficile da derivare senza un po' di conoscenza interna del sito stesso. Inoltre, avere accesso in scrittura solo a questa tabella e non all'intero database (nel qual caso potrebbero creare un nuovo Super Utente) è estremamente improbabile. Tuttavia, stiamo criptando le credenziali per rendere impossibile anche questo attacco completamente teorico.

Siamo pienamente consapevoli che se un utente ha accesso in lettura al filesystem del server, ha accesso alla chiave di crittografia e alle informazioni di connessione al database, tutto ciò è memorizzato in configuration.php. Tuttavia, in questo caso sei già stato hackerato: l'attaccante può leggere configuration.php, quindi sa come connettersi al tuo database. In questo caso, possono fare quello che vogliono al tuo sito, inclusa l'eliminazione di tutti i Super Utenti esistenti e la creazione del proprio account Super Utente. Pertanto, non c'è motivo di cercare di affrontare questa situazione; saresti completamente compromesso (hackerato). L'unica cosa che potrebbe esternare grazia è avere backup regolari, testati e off-site.

### Ho configurato l'Autenticazione a Due Fattori ma accedo senza fornire la mia Chiave Segreta. Non è insicuro?

No, è intenzionale e per progettazione.

Quando abbiamo aggiunto l'Autenticazione a Due Fattori (TFA) in Joomla! 3.2, era possibile accedere al tuo sito solo con un nome utente e una password. Le password possono essere rubate o indovinate. Pertanto, TFA era l'unico modo per fornire un minimo di sicurezza su obiettivi ad alto rischio e ad alto valore. Era il 2013.

WebAuthn è una soluzione di autenticazione completamente diversa che non ha nessuno dei problemi delle password fisse. Utilizza crittografia forte e hardware sicuro per renderla praticamente impossibile da sovvertire le chiavi crittografiche di autenticazione. È anche inattaccabile da phishing, cioè non puoi essere ingannato nell'usarlo su un sito che si spaccia per autentico poiché la credenziale WebAuthn è legata al nome esatto del dominio per il quale è stata emessa (sì, se utilizzi più domini per il tuo sito o trasferisci il tuo sito su un altro dominio dovrai ri-registrare tutti i tuoi autenticatori WebAuthn – hai capito bene!). Di conseguenza, l'autenticazione con WebAuthn è incredibilmente sicura e supera i motivi che hanno richiesto la TFA. Ciò significa che se ti autentichi con successo utilizzando WebAuthn, la chiave segreta TFA non deve essere – e quindi non viene – controllata.

In un mondo ideale, saresti in grado di accedere al tuo sito solo utilizzando WebAuthn. Questa è una funzionalità su cui stiamo lavorando e che potresti non voler attivare; dopotutto, se il tuo nome di dominio cambia o perdi l'accesso a tutti i tuoi autenticatori WebAuthn oppure li ripristini, saresti bloccato fuori dal tuo sito. Pertanto, dovresti comunque abilitare la TFA sul tuo account utente partendo dal presupposto che il login con password può ancora essere utilizzato come riserva per accedere al tuo sito e deve essere protetto dagli attacchi noti contro le password fisse.

### La TFA non è sufficiente? Perché abbiamo bisogno di WebAuthn?

La TFA da sola è sufficiente nella maggior parte dei casi, ma soffre di due problemi.

In primo luogo, ha un'esperienza utente piuttosto complessa. È necessario fornire la tua chiave segreta che cambia continuamente, insieme a nome utente e password. La maggior parte delle persone utilizza TOTP (il PIN di sei cifre che cambia ogni 30 secondi), il che rallenta il processo di login e tende a frustrare gli utenti. Utilizzare una YubiKey è molto più rapido, ma anche più costoso e più complicato da distribuire quando ci sono più di pochi utenti sul sito. Una YubiKey ha anche una vita attesa di circa 2 anni di uso quotidiano quando genera Password Mono-Uso (si esaurisce la memoria scrivibile una sola volta che utilizza per tenere traccia delle firme emesse).

In secondo luogo, se stai utilizzando TOTP sei ancora suscettibile a problemi di sicurezza quali i keylogger, il phishing e la possibilità che la chiave segreta utilizzata per la generazione del TOTP venga rubata. Inoltre, con un milione di possibilità e trenta secondi per provarle, è concepibile che un attaccante possa avere fortuna poiché Joomla non blocca il tuo account né impone alcuna limitazione della velocità per tentativi di login non riusciti. Anche se tali protezioni potrebbero essere implementate, l'implementazione stessa potrebbe essere sfruttata per creare una situazione di negazione del servizio che blocca un utente legittimo fuori dal suo sito mentre l'attaccante è occupato a infiltrarsi. È il caso in cui la cura è peggiore della malattia.

WebAuthn migliora notevolmente l'esperienza utente. I principali browser hanno abbracciato WebAuthn e offrono un'esperienza utente convincente, guidando gli utenti nell'uso degli autenticatori in modo efficace. Accedere con WebAuthn è più conveniente anche rispetto all'utilizzo della funzione di riempimento automatico di un gestore di password. Con le versioni recenti dei sistemi operativi mobili, anche quell'esperienza, una volta leggermente confondente, sta rapidamente diventando più facile rispetto alle password e alla TFA.

Dove WebAuthn fa davvero la differenza è nel fronte della sicurezza. In virtù dell'uso di hardware sicuro e della validazione rigorosa del nome di dominio del sito, è praticamente immune ai keylogger, al phishing e alla sovversione delle chiavi. Ha anche una protezione incorporata contro la clonazione delle chiavi. Sì, puoi ancora perdere il tuo hardware — ma gli autenticatori FIDO2, che siano dispositivi esterni o integrati, possono essere bloccati con un PIN o biometria. Complessivamente, usare WebAuthn con autenticatori FIDO2 è più resistente al furto e alla perdita rispetto alle chiavi di casa o dell'auto.

## Note per gli sviluppatori

### Pulsanti di login extra

Il modulo plugin e com_users ora utilizzano l'evento onUserLoginButtons, definito e chiamato in `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, per recuperare le definizioni di eventuali pulsanti aggiuntivi che devono essere inseriti dopo il pulsante di login regolare.

Tutti gli sviluppatori che implementano un modulo di login o, più in generale, un form di login dovrebbero anche utilizzare il metodo statico pubblico `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` per recuperare tali definizioni e visualizzare questi pulsanti per rendere il loro software completamente compatibile con Joomla 4.

Gli sviluppatori che desiderano implementare pulsanti personalizzati dovrebbero vedere come il plugin di sistema WebAuthn implementa questa funzionalità. Tali pulsanti possono essere utilizzati per implementare servizi di single-sign-on di terze parti o anche per accedere utilizzando servizi di identità di terze parti come quelli offerti dai più popolari social media (Facebook, Google, Twitter, GitHub, ecc.).

Questo cambiamento non impatta negativamente sulla compatibilità retroattiva. I moduli di login di terze parti e i form di login continueranno a funzionare normalmente anche se non implementano la funzionalità di pulsanti di login extra con la notevole esclusione delle integrazioni consentite da tale funzionalità come l'Autenticazione Web stessa. Vale a dire che non smetteranno di funzionare (il che sarebbe una rottura della compatibilità retroattiva) ma non saranno completi delle funzionalità.

### Consentire com_ajax nella pagina di login del backend

La pagina di login dell'Amministratore inserisce nella whitelist com_ajax in AdministratorApplication in modo che possa essere utilizzato per gestire le richieste da parte degli utenti ospiti.

Questo cambiamento non causa problemi di compatibilità retroattiva purché gli sviluppatori utilizzino pratiche sensate e non presumano che essere chiamati da com_ajax nel backend sia la prova che l'utente è connesso al backend. Questa sarebbe una cattiva pratica di sicurezza. La pratica sensata è utilizzare l'oggetto Utente di Joomla per rilevare se si tratta di un utente ospite e, in caso negativo, se l'utente è autorizzato a una permesso richiesto per eseguire l'azione richiesta tramite com_ajax. Vale a dire, se questo cambiamento ha rotto il tuo codice, allora il tuo codice era già rotto e aveva bisogno comunque di essere rivisto.

## Ulteriori Informazioni

La documentazione iniziale di questa funzionalità è nella pull request al
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Tradotto da openai.com*

