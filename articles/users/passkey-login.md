<!--
{
    "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
    "title": "Accesso con passkey",
    "description": " ",
    "author": ""
}
-->

## Introduzione

L'accesso con passkey, precedentemente noto come Web Authentication o, in
breve, WebAuthn, consente a un utente di accedere in modo sicuro a un sito
senza utilizzare una password, anche se è ancora necessario un nome utente.
Utilizza una crittografia avanzata in un modo estremamente resistente ai
problemi più comuni delle password:

* qualcuno l'ha indovinata (attacco a forza bruta)
* qualcuno l'ha intercettata (attacco man-in-the-middle)
* qualcuno ti ha ingannato inducendoti a divulgarla (attacco di phishing)
* qualcuno l'ha violata dopo essere entrato in possesso di una copia dei dati
del database (attacchi di SQL injection)
* qualcuno l'ha rubata.

L'accesso con passkey non è solo molto sicuro; è anche molto intuitivo!
Non devi più ricordare lunghe password né utilizzare un gestore di password.
Tutto ciò di cui hai bisogno è un *autenticatore*, talvolta chiamato anche
*passkey*.

Un autenticatore può avere molte forme, fisiche o virtuali. Può essere una
chiave hardware separata che si connette al dispositivo tramite USB, Bluetooth
o NFC. Può essere il dispositivo stesso, che sblocca il proprio autenticatore
integrato tramite un PIN, un lettore di impronte digitali, una scansione del
volto o un controllo biometrico simile.

Questa funzionalità è già disponibile sui dispositivi Android e iOS/iPadOS e
stiamo lavorando per abilitarla anche su Windows. Può persino essere il tuo
telefono: attualmente è possibile con i telefoni Android, ma questa
funzionalità arriverà anche sui dispositivi iOS / iPadOS.

L'accesso con passkey funziona solo tramite HTTPS e solo quando il tuo sito
utilizza un certificato valido e attendibile. Non preoccuparti, non devi
spendere denaro aggiuntivo; i servizi gratuiti come Let's Encrypt sono in
genere integrati nei pannelli di controllo degli hosting web e funzionano
perfettamente con l'accesso con passkey.

L'accesso con passkey utilizza la crittografia a chiave pubblica, la stessa
tecnologia collaudata che protegge i tuoi siti con HTTPS, mantiene sicure le
tue informazioni bancarie e così via. La chiave privata non lascia mai
l'autenticatore. Il tuo sito memorizza solo una chiave pubblica. Anche in
caso di violazione dei dati, all'aggressore resterebbe una chiave pubblica
praticamente inutile; per violarla occorrerebbero da migliaia a milioni di
anni di calcolo della CPU, rispetto ai pochi minuti o alle poche ore
necessari per violare l'hash di una password fissa che puoi ricordare.

L'accesso con passkey è il futuro dell'autenticazione. Semplice, sicuro e
senza complicazioni. Tutto ciò che le password fisse non sono.

L'immagine seguente mostra un dispositivo hardware inserito nella porta USB
di un computer portatile. Costava 15 £ a febbraio 2022.

![fotografia del dispositivo hardware](../../../en/images/users/passkey-login/01-hardware-device.jpg)

L'accesso con passkey utilizza un plugin di sistema abilitato per impostazione
predefinita. Un pulsante **Accedi con passkey** sarà presente nelle schermate
di accesso predefinite di Joomla 4 e versioni successive, come illustrato
nella schermata di accesso dell'amministratore:

![modulo di accesso sicuro dell'amministratore](../../../en/images/users/passkey-login/02-login-form.png)

## Configurazione dell'utente

L'utente deve prima registrarsi con un normale nome utente e una password.
Dopo aver effettuato l'accesso, vai al modulo Profilo utente. Per un
amministratore:

- Seleziona **Menu utente → Modifica account → Accesso con passkey** per
  visualizzare il modulo, inizialmente senza autenticatori registrati.
- Seleziona **Aggiungi nuova passkey**

La presentazione esatta del passaggio successivo dipende dal browser.
In genere verrà visualizzato un avviso, un messaggio o una finestra che chiede
di selezionare un tipo di autenticatore oppure, se utilizzi un autenticatore
hardware collegato al dispositivo, che ti ricorda di premere il pulsante
sull'autenticatore hardware. Per motivi di sicurezza e praticità, l'intervallo
di tempo consentito per attivare l'autenticatore è relativamente breve:
60 secondi.

![richiesta hardware per l'accesso sicuro dell'amministratore](../../../en/images/users/passkey-login/03-hardware-prompt.png)

Dopo aver sbloccato l'autenticatore — toccando un pulsante, eseguendo la
scansione dell'impronta digitale / del volto, inserendo un PIN o una
combinazione delle opzioni precedenti, a seconda dell'autenticatore — il
messaggio scompare, l'autenticatore viene registrato e la schermata appare
come segue:

![autenticatore registrato per l'accesso sicuro dell'amministratore](../../../en/images/users/passkey-login/04-registered-authenticator.png)

È molto importante notare che puoi registrare o rimuovere autenticatori solo
dal tuo account utente. Per motivi di sicurezza, anche a un Super User è
vietato registrare, modificare o aggiungere autenticatori negli account di
altri utenti.

### Autenticatori

È possibile utilizzare qualsiasi autenticatore FIDO U2F o FIDO2. FIDO U2F è uno
standard meno recente che supporta una selezione più limitata e meno sicura di
metodi crittografici. FIDO2 è lo standard più recente, che supporta metodi
crittografici molto più sicuri, tra cui la crittografia a curva ellittica, un
metodo crittografico ritenuto resistente persino al calcolo quantistico (se e
quando quest'ultimo diventerà una realtà pratica). Inoltre, gli autenticatori
FIDO2 possono essere configurati con protezioni aggiuntive, come un PIN o un
controllo biometrico (ad esempio la scansione delle impronte digitali), il che
significa che, anche se si perde il possesso fisico dell'autenticatore, chiunque
lo trovi non potrà accedere ai propri siti.

Se si desidera acquistare un autenticatore hardware, è possibile cercare
"FIDO2" nel proprio marketplace preferito, come Amazon. È disponibile un'ampia
scelta.

È inoltre possibile utilizzare una chiave FIDO software, come Krypton, come
autenticatore.

Molti dispositivi dispongono di un'autenticazione integrata conforme a FIDO2:

- Windows 10 e 11 dispongono di Windows Hello con un PIN, uno scanner per le impronte digitali,
  una fotocamera per il riconoscimento facciale oppure una combinazione di chiave hardware e PIN.
- macOS dispone di TouchID su tutti i portatili con chipset T2 o basati su
  Apple Silicon che utilizzano il sensore TouchID integrato, nonché su tutti i
  computer desktop basati su Apple Silicon che utilizzano la nuova tastiera Apple
  Aluminium con uno scanner per le impronte digitali.
- iOS / iPadOS dispone di TouchID su tutti i dispositivi dotati di scanner per
  le impronte digitali e di FaceID su tutti i dispositivi più recenti dotati di
  una fotocamera a proiezione di punti a infrarossi FaceID.
- Alcuni dispositivi Android dispongono di uno scanner per le impronte digitali
  o di una fotocamera per il riconoscimento facciale. Questi possono funzionare
  anche come autenticatori FIDO2, su Android 9 o versioni successive utilizzando
  almeno Google Chrome.
- Potrebbero essere disponibili anche altri dispositivi. Ad esempio, i telefoni
  Android che utilizzano
  [caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Browser compatibili con l'accesso tramite passkey

In pratica, se il sistema operativo e il browser sono stati rilasciati dopo la
metà del 2020, non dovrebbero esserci problemi. Solo alcuni browser molto poco
diffusi non supportano ancora l'accesso tramite passkey.

## Autenticazione

Per accedere è necessario inserire il proprio nome utente nel campo Nome utente
del modulo di accesso. Non è necessario inserire la password, ma se il browser
la inserisce automaticamente è sufficiente lasciarla. La password NON viene
inviata al server quando il modulo viene inviato tramite il pulsante Web
Authentication.

Ne consegue che è possibile accedere utilizzando il proprio nome utente e la
password oppure il nome utente e l'accesso tramite passkey.

## Come disabilitare il plugin

Se non si desidera consentire l'accesso tramite passkey, è sufficiente accedere
all'elenco dei plugin, individuare il plugin **System - Accesso tramite passkey
(senza password)** nel gruppo Sistema e disabilitarlo. Non è necessario impostare
alcun parametro.

## Requisiti del server

Affinché l'accesso tramite passkey funzioni, devono essere soddisfatti i
seguenti prerequisiti:

- HTTPS con un certificato valido e firmato. La maggior parte degli host consente di utilizzare
  certificati gratuiti emessi da Let's Encrypt. Questi funzionano perfettamente
  con l'accesso tramite passkey.
- L'estensione OpenSSL per PHP deve essere installata e abilitata.
- L'estensione PHP GMP o l'estensione PHP BCmath deve essere installata
  e abilitata (è sufficiente una delle due).
- Idealmente, la libreria Sodium dovrebbe essere abilitata; consente di utilizzare
  la crittografia a curva ellittica sugli autenticatori FIDO2 compatibili, che,
  come abbiamo detto, è il metodo crittografico più sicuro.

## Domande frequenti e risoluzione dei problemi

### Non riesco a vedere il pulsante *Accedi con passkey*

Non si sta accedendo al sito tramite HTTPS. L'accesso tramite passkey è
disponibile solo per i siti HTTPS con un certificato valido. Si tratta di una
precauzione di sicurezza integrata nello standard di accesso tramite passkey. Il
plugin verifica effettivamente se il sito viene raggiunto tramite HTTPS
utilizzando la classe Uri di Joomla. In rari casi, quando il server dichiara
erroneamente il protocollo, il pulsante potrebbe non essere visualizzato anche
se il sito (dichiara di) utilizzare HTTPS. Lo stesso vale se è stato modificato
il file configuration.php e impostato il parametro di configurazione opzionale
\$live_site con il prefisso di protocollo http:// invece di https://.

Si noti inoltre che i moduli e i componenti di accesso di terze parti che
implementano un proprio modulo di accesso potrebbero non visualizzare ancora
questi pulsanti. Abbiamo aggiunto una nuova infrastruttura per supportarli,
analogamente a quanto abbiamo dovuto fare in Joomla! 3.2 per supportare
l'autenticazione a due fattori.

### Devo ancora fornire un nome utente. Il login con Passkey non dovrebbe eliminare i nomi utente?

Non proprio. La specifica attuale del login con Passkey non fornisce una gestione delle identità. I browser web richiedono che inviamo loro un elenco di chiavi pubbliche Passkey accettabili durante la fase di accesso. Questo significa che abbiamo bisogno del tuo nome utente per recuperarle.

Detto questo, l'uso del login con Passkey rende finalmente chiaro che i nomi utente *non devono essere considerati segreti*. Sono considerate informazioni pubbliche che possono essere trasmesse liberamente a un malintenzionato, proprio come le chiavi pubbliche memorizzate nel database del sito. L'unico segreto è memorizzato nell'autenticatore stesso e non lascia mai l'autenticatore!

### Ho registrato un autenticatore, ma quando provo ad accedere mi viene detto che non ne ho registrato nessuno. È un bug?

È un bug, ma non del plugin per il login con Passkey.

Uno o più plugin del tuo sito generano notifiche, avvisi o errori PHP, corrompendo così la risposta inviata dal server. Di conseguenza, il JavaScript nella pagina non riesce ad analizzare la risposta del server e non è in grado di stabilire se l'utente ha registrato degli autenticatori.

Vai al backend del tuo sito, Sistema, Configurazione globale e imposta Segnalazione degli errori su Nessuno. Nella maggior parte dei casi di malfunzionamento dei plugin principali e di quelli di terze parti questo è sufficiente. In caso contrario, esamina l'output della richiesta utilizzando gli strumenti per sviluppatori del browser, per vedere cosa sta corrompendo la richiesta.

### In Safari non viene visualizzata alcuna richiesta per usare il mio autenticatore

Questo problema non dovrebbe più verificarsi con iOS 13, iPadOS 13 e macOS Catalina o versioni successive.

Si tratta di un bug di Safari presente nelle versioni precedenti di Safari. Le versioni precedenti di Safari includevano il supporto per il login con Passkey solo come funzionalità sperimentale e non ancora completamente terminata.

### Non posso usare un sensore biometrico (TouchID, impronta digitale, Windows Hello)

Alcuni browser meno recenti basati su Chromium (ad eccezione di Google Chrome propriamente detto) non disponevano del supporto completo per gli autenticatori integrati. Andavano in crash o si bloccavano quando si tentava di utilizzarne uno. Questi problemi sono stati risolti in questi browser intorno alla metà del 2020.

Se utilizzi Windows, ricorda che il tuo dispositivo DEVE avere un chip Trusted Platform Module (TPM), che deve essere abilitato nel BIOS. Avere semplicemente un sensore biometrico compatibile con Windows Hello non è sufficiente. Si tratta di una precauzione di sicurezza prevista dallo stesso standard del login con Passkey: le informazioni dell'autenticatore devono essere elaborate utilizzando hardware sicuro e resistente alle manomissioni, per impedire la compromissione delle chiavi (ad esempio, un malware in esecuzione sul computer non può rubare la chiave utilizzata per l'autenticazione).

Infine, tieni presente che il supporto per Windows Hello è ancora in fase di sviluppo e sarà rilasciato con Joomla 4.2.

### Se posso usare un autenticatore software, perché dovrei preoccuparmi di avere un token hardware?

Il fulcro del login con Passkey è la segretezza assoluta della chiave privata. Questa è conosciuta solo dall'autenticatore e dovrebbe essere impossibile comunicarla al mondo esterno.

Nel caso di un autenticatore hardware, sia esso un dispositivo hardware dedicato oppure un TPM / Secure Enclave integrato nel dispositivo, ciò è garantito dalla natura stessa di tale hardware.

Un autenticatore software genera una chiave segreta e la memorizza nel file system. Tuttavia, rimane una normale applicazione software che viene eseguita all'interno del normale sistema operativo, sia esso quello del telefono o del computer. Di conseguenza, è soggetta a diverse classi di attacchi che possono essere utilizzate per rubare informazioni furtivamente (problemi di sicurezza del software stesso, malware che sfruttano vulnerabilità di classe Spectre nelle CPU moderne, ecc.).

Pertanto, un autenticatore software è molto più pratico e sicuro di una normale password, ma un autenticatore hardware offre la massima sicurezza. Scegli il tuo autenticatore in base al tuo budget e alle tue esigenze di sicurezza.

Considerando che il prezzo di una chiave FIDO (compatibile con il login con Passkey) è inferiore a 20 € su Amazon, puoi utilizzare un autenticatore hardware nella maggior parte dei casi d'uso pratici.

### Perché le credenziali sono crittografate nel database? Non è eccessivo?

L'unica cosa memorizzata nel database è la chiave pubblica restituita
dall'autenticatore quando eseguiamo la procedura di attestazione (questo è
il nome formale della registrazione di un autenticatore secondo la
specifica di accesso con Passkey). Essendo una chiave pubblica, non deve
essere protetta dalla lettura. Anche se un utente non autorizzato riuscisse
a leggere queste informazioni, non sarebbe in grado di impersonare
l'autenticatore, ad esempio clonandolo.

Tuttavia, se un utente malintenzionato avesse accesso in scrittura
soltanto alla tabella del database `#__webauthn_credentials`, senza accesso
in lettura al file system e senza accesso in scrittura a qualsiasi altra
tabella, potrebbe teoricamente **aggiungere** un proprio autenticatore,
riuscendo quindi a impersonare l'utente preso di mira nel sistema. Si
tratta di un attacco molto teorico, poiché dovrebbe anche conoscere
l'identificatore dell'utente che sta attaccando, cosa più difficile da
dedurre senza una certa conoscenza interna del sito stesso. Inoltre, avere
accesso in scrittura solo a questa tabella e non all'intero database (nel
qual caso potrebbe creare un nuovo Super User) è estremamente improbabile.
Tuttavia, crittografiamo le credenziali per rendere impossibile anche a
questo attacco completamente teorico di avere successo.

Siamo pienamente consapevoli che, se un utente ha accesso in lettura al
file system del server, ha accesso alla chiave di crittografia e alle
informazioni di connessione al database, tutte memorizzate in
configuration.php. Tuttavia, in questo caso il sistema è già stato
compromesso: l'attaccante può leggere configuration.php e quindi sa come
connettersi al database. In questo caso può fare ciò che vuole al sito,
incluso eliminare tutti i Super User esistenti e creare il proprio account
Super User. Pertanto non c'è motivo di cercare di gestire questa
situazione: il sistema sarebbe completamente compromesso (violato). L'unica
cosa che potrebbe salvarvi è disporre di backup regolari, verificati e
conservati fuori sede.

### Ho configurato l'autenticazione a due fattori, ma ho effettuato l'accesso senza fornire la mia chiave segreta. Non è insicuro?

No, è intenzionale e previsto dal design.

Quando abbiamo aggiunto l'autenticazione a due fattori (TFA) in Joomla! 3.2,
era possibile accedere al sito solo usando un nome utente e una password. Le
password possono essere rubate o indovinate. Pertanto, la TFA era l'unico
modo per fornire un livello minimo di sicurezza su obiettivi ad alto rischio
e di alto valore. Era il 2013.

L'accesso con Passkey è una soluzione di autenticazione completamente
diversa, che non presenta nessuno dei problemi delle password statiche.
Utilizza una crittografia avanzata e hardware sicuro per rendere
praticamente impossibile compromettere le chiavi crittografiche di
autenticazione. È inoltre inattaccabile tramite phishing, cioè non è
possibile indurvi a utilizzarlo su un sito che impersona quello legittimo,
poiché la credenziale di accesso con Passkey è associata al nome di dominio
esatto per il quale è stata emessa (sì, se usate più domini per il vostro
sito o trasferite il sito a un altro dominio dovrete registrare nuovamente
tutti i vostri autenticatori di accesso con Passkey: avete capito bene!).
Di conseguenza, l'autenticazione con l'accesso Passkey è estremamente
sicura e supera le motivazioni che avevano reso necessaria la TFA. Ciò
significa che, se l'autenticazione con l'accesso Passkey ha esito positivo,
non è necessario controllare la chiave segreta TFA e pertanto non viene
controllata affatto.

In un mondo ideale, sarebbe possibile accedere al sito solo usando
l'accesso con Passkey. Questa è una funzionalità su cui stiamo lavorando e
che potreste non voler abilitare; dopotutto, se il nome del dominio cambia
o perdete l'accesso a tutti i vostri autenticatori di accesso con Passkey o
li reimpostate, non potreste più accedere al sito. Pertanto dovreste
comunque abilitare la TFA sul vostro account utente, considerando che
l'accesso con password può ancora essere utilizzato come alternativa per
accedere al sito e deve essere protetto dagli attacchi noti contro le
password statiche.

### TFA non è abbastanza? Perché abbiamo bisogno dell'accesso con passkey?

La TFA da sola è sufficiente nella maggior parte dei casi, ma presenta due problemi.

Innanzitutto, offre un'esperienza utente piuttosto scomoda. È necessario fornire
la chiave segreta che cambia continuamente insieme al nome utente e alla password.
La maggior parte delle persone usa TOTP (il PIN di sei cifre che cambia ogni
30 secondi), il che rallenta l'accesso e tende a frustrarle. L'uso di una YubiKey
è molto più rapido, ma anche più costoso e più complicato da configurare quando
sul sito sono presenti più di un paio di utenti. Inoltre, una YubiKey ha una
durata prevista di circa 2 anni di utilizzo quotidiano quando genera password
monouso (esaurisce la memoria scrivibile una sola volta che utilizza per tenere
traccia delle firme emesse).

In secondo luogo, se si utilizza TOTP si è comunque esposti a problemi di sicurezza
come i keylogger, il phishing e la possibilità che la chiave segreta usata per
generare il TOTP venga rubata. Inoltre, con un milione di possibilità e trenta
secondi per tentare di indovinarle, è concepibile che un aggressore possa essere
fortunato, poiché Joomla non blocca l'account e non applica altrimenti una
limitazione della frequenza ai tentativi di accesso falliti. Sebbene queste
protezioni possano essere implementate, l'implementazione stessa potrebbe essere
abusata per creare una situazione di negazione del servizio che impedisca a un
utente legittimo di accedere al proprio sito mentre l'aggressore è impegnato a
infiltrarsi al suo interno. È un caso in cui il rimedio è peggiore della malattia.

L'accesso con passkey migliora notevolmente l'esperienza utente. I principali
browser hanno adottato l'accesso con passkey e offrono un'esperienza utente
convincente, guidando gli utenti nell'utilizzo corretto degli autenticatori.
Accedere con una passkey è più comodo persino rispetto all'utilizzo della
funzione di compilazione automatica di un gestore di password. Con le versioni
recenti dei sistemi operativi mobili, anche quell'esperienza, un tempo leggermente
confusa, sta rapidamente diventando più semplice di quanto non siano mai state
le password e la TFA.

Dove l'accesso con passkey dà veramente il meglio di sé è sul fronte della
sicurezza. Grazie all'uso di hardware sicuro e alla forte convalida del nome di
dominio del sito, è praticamente immune a keylogger, phishing e compromissione
delle chiavi. Dispone persino di una protezione integrata contro la clonazione
delle chiavi. Sì, è comunque possibile perdere l'hardware — ma gli autenticatori
FIDO2, siano essi dispositivi esterni o integrati, possono essere bloccati con
un PIN o con dati biometrici. Nel complesso, l'uso dell'accesso con passkey con
autenticatori FIDO2 è più resistente a furti e smarrimenti rispetto alle chiavi
di casa o dell'auto.

## Note per gli sviluppatori

### Pulsanti di accesso aggiuntivi

Il modulo del plugin e com_users ora utilizzano l'evento onUserLoginButtons,
definito e chiamato in
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, per recuperare le
definizioni di eventuali pulsanti aggiuntivi che devono essere posizionati dopo
il pulsante di accesso standard.

Tutti gli sviluppatori che implementano un modulo di accesso o, più in generale,
un modulo per il modulo di accesso, dovrebbero usare anche il metodo statico
pubblico
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` per recuperare tali
definizioni e visualizzare questi pulsanti, rendendo il proprio software
pienamente compatibile con Joomla 4.

Gli sviluppatori che desiderano implementare pulsanti personalizzati dovrebbero
esaminare il modo in cui il plugin di sistema per l'accesso con passkey implementa
questa funzionalità. Tali pulsanti possono essere utilizzati per implementare
servizi di single sign-on di terze parti o persino per effettuare l'accesso
utilizzando servizi di identità di terze parti, come quelli offerti dai social
media più diffusi (Facebook, Google, Twitter, GitHub ecc.).

Questa modifica non influisce negativamente sulla compatibilità con le versioni
precedenti. I moduli e i moduli per i moduli di accesso di terze parti continueranno
a funzionare normalmente anche se non implementano la funzionalità dei pulsanti
di accesso aggiuntivi, con la notevole omissione delle integrazioni offerte da
tale funzionalità, come la Web Authentication stessa. In altre parole, non
smetteranno di funzionare (il che costituirebbe una modifica incompatibile), ma
non saranno completi sotto il profilo delle funzionalità.

### Consentire com_ajax nella pagina di accesso del backend

La pagina di accesso dell'amministratore inserisce com_ajax nella whitelist di
AdministratorApplication, in modo che possa essere utilizzato per gestire le
richieste degli utenti ospiti.

Questa modifica non causa problemi di compatibilità con le versioni precedenti,
purché gli sviluppatori adottino pratiche corrette e non presumano che il fatto
di essere chiamati da com_ajax nel backend dimostri che l'utente abbia effettuato
l'accesso al backend. Sarebbe una cattiva pratica di sicurezza. La pratica corretta
consiste nell'utilizzare l'oggetto User di Joomla per rilevare se si tratta di un
utente ospite e, in caso contrario, se all'utente è stata assegnata un'autorizzazione
necessaria per eseguire l'azione richiesta tramite com_ajax. In altre parole, se
questa modifica ha compromesso il funzionamento del vostro codice, il codice era
già difettoso e doveva comunque essere riscritto.

## Ulteriori informazioni

La documentazione iniziale di questa funzionalità è disponibile nella richiesta
pull
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Tradotto da openai.com*