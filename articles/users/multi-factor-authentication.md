<!-- Filename: J4.x:Multi-factor_Authentication / Display title: Autenticazione a più fattori  -->

## Introduzione

Il sistema di Autenticazione Multi-fattore di Joomla! è basato su Akeeba Loginguard e gran parte di questa documentazione è stata derivata con il permesso di Akeeba.

## Cosa fa?

Aggiunge diversi metodi facoltativi di Verifica in Due Passaggi per il login in Joomla! Dopo aver effettuato l'accesso solo con nome utente e password, ti viene richiesto di fornire la tua verifica del secondo passaggio, ad esempio un codice generato da Google Authenticator. Finché non fornisci una verifica del secondo passaggio corretta, non potrai accedere a nessuna pagina del sito. Verrai sempre reindirizzato alla pagina di "accesso obbligatorio". Questo è simile a ciò che fa Google quando provi ad accedere a GMail.

Questo differisce dal metodo originale di autenticazione a due fattori di Joomla!, che richiedeva di inserire il secondo fattore di autenticazione (ad esempio, il codice generato da Google Authenticator) insieme al nome utente e alla password.

I vantaggi della Verifica in Due Passaggi sono:

- È meno confusione per l'utente. Non c'è più bisogno del campo "Chiave Segreta" che confonde gli utenti.
- Può funzionare con metodi di accesso non basati su password come il login sociale (ad esempio, Facebook), token hardware sicuri, SSO (single sign-on) ecc. 
  Chiarimento: la Verifica in Due Passaggi può essere configurata per essere richiesta dopo che un utente ha effettuato l'accesso con un metodo di login non basato su password. Non implementa metodi di login non basati su password.
- Ha un migliore controllo dell'accesso. Puoi impostare le Opzioni Utente per Richiedere o Disabilitare l'Autenticazione Multi-fattore per gruppo utente.
- Permette metodi di autenticazione alternativi in un unico account. Puoi avere diversi metodi di autenticazione sul tuo account. Ad esempio, puoi configurare un'app Google Authenticator e una YubiKey.
- Supporta metodi che non richiedono l'inserimento di un codice. Ad esempio, dongle FIDO2, verifica biometrica ecc. Questi necessitano di interagire con il browser e/o il sistema operativo tramite API HTML5 native.
- Supporta metodi che richiedono l'interazione dell'utente. Ad esempio, l'invio di un codice tramite messaggio push, SMS o email. Questi metodi richiedono di sapere quale utente viene autenticato prima di inviare il codice di autenticazione all'utente.
- È gratuito. A differenza dei servizi di terze parti che offrono l'autenticazione multi-fattore, non devi pagare un costo di configurazione iniziale o una tariffa mensile/annuale di manutenzione per ogni sito o utente che utilizza la Verifica in Due Passaggi. Il software è gratuito.

## Come funziona

Accedi al tuo sito normalmente, ad esempio fornendo un nome utente e una password. È importante notare che non è necessario inserire le credenziali di autenticazione a due fattori in questa fase.

Il sistema rileva che hai effettuato l'accesso ma non hai completato il secondo passaggio di autenticazione. Memorizza l'URL che avresti dovuto vedere e ti reindirizza immediatamente alla pagina di accesso riservato. Qualsiasi tentativo di navigare verso una pagina diversa farà apparire la pagina riservata.

I moduli sul tuo sito possono contenere informazioni riservate. Per garantire la riservatezza, i moduli vengono forzatamente disattivati al momento del rendering. Ciò significa che nessuna posizione del modulo verrà visualizzata sulla pagina. Ricorda che nel caso notassi l'assenza dell'intestazione o di altre aree chiave del design del tuo sito nella pagina di accesso riservato.

Si noti che i plugin, d'altra parte, NON sono disabilitati. Ciò è dovuto sia al fatto che Joomla rende estremamente difficile rimuovere plugin specifici una volta caricati, sia perché la maggior parte dei plugin svolge funzioni critiche sul tuo sito.

Dopo aver fornito la tua verifica al secondo passo, viene impostato un flag nella sessione utente, indicando che sei completamente autorizzato a utilizzare il sito. Inoltre, verrai reindirizzato all'URL che era stato memorizzato subito dopo il tuo accesso iniziale.

## Autenticazione a due fattori versus accessi WebAuthn

Accedere con WebAuthn è l'opzione più sicura. Fornisci solo un nome utente che dovrebbe essere considerato informazione pubblica e non privilegiata. Il sito crea una sfida crittografica che viene firmata dal browser utilizzando hardware sicuro — un token di sicurezza hardware esterno o il Trusted Platform Module / Secure Enclave del tuo dispositivo — e restituita al server. Il server convalida la firma. Questa convalida utilizza la crittografia a chiave pubblica con il sito che memorizza solo la chiave pubblica. Questo rende l'accesso virtualmente impossibile da phishing e estremamente sicuro. Se usi questo metodo non hai bisogno di un secondo fattore di autenticazione — ma se davvero lo desideri, puoi usare anche WebAuthn.

Escludendo l'uso di metodi di accesso federato (come accedere con il tuo account di social media, un servizio di Single Sign-On, un server LDAP ecc.), un accesso convenzionale con nome utente + password non è neanche lontanamente sicuro quanto un accesso WebAuthn. L'inserimento di un nome utente e di una password può essere intercettato, rubato o indovinato. Questo rende il fidarsi solo di un nome utente e una password molto problematico.

Per l'autenticazione a più fattori fornisci solo il tuo nome utente e la password. Un attacco di phishing riuscito otterrebbe solo questo primo fattore di autenticazione ma non il tuo secondo fattore di autenticazione. Dopo un accesso riuscito ti viene presentata una pagina captive. Non puoi fare nient'altro sul sito finché non fornisci il tuo secondo fattore. Poiché l'inserimento del secondo fattore viene presentato in una pagina propria, può essere interattivo (es. WebAuthn), asincrono (es. ricevendo un OTP tramite email, messaggio di testo o notifica push) o iniziato dall'utente (es. un TOTP o un OTP Yubikey). Ancora meglio, un utente può avere più metodi di secondo fattore abilitati sul proprio account per prevenire blocchi accidentali dal sito. Ad esempio, potresti usare WebAuthn con un dongle hardware sicuro esterno come tuo secondo fattore primario e più sicuro. Potresti anche avere un normale TOTP configurato nel caso in cui perdi il dongle o dimentichi di portarlo con te. Alcuni metodi di secondo fattore permettono di avere più istanze, ad esempio puoi avere più autenticatori WebAuthn così puoi usare l'autenticatore integrato nel tuo computer Windows, nel tuo iPhone e nel tuo tablet Android senza dover ricordare di portare un dongle hardware e adattatori ogni volta che lasci la tua scrivania.

Ricapitoliamo. Dalla più sicura alla meno sicura, le tue opzioni sono:

- WebAuthn come tuo metodo principale di accesso con autenticazione multifattoriale secondaria.
- WebAuthn come tuo unico metodo di accesso.
- Nome utente e password come tuo metodo principale di accesso con autenticazione multifattoriale secondaria.
- Solo un nome utente e password come tuo unico metodo di accesso.

## Plugin

Ciascuno dei fattori nell'Autenticazione Multi-fattore è implementato tramite plugin. Possono essere abilitati o disabilitati secondo necessità. E se ne possono aggiungere di nuovi quando vengono introdotti nuovi metodi. I plugin forniti con il core di Joomla includono:

- **Codice di Verifica**: codici di verifica a sei cifre generati da un'app di autenticazione (Google Authenticator, Authy, LastPass Authenticator, ecc.), un gestore di password (1Password, BitWarden, Keeper, KeePassXC, Strongbox, ecc.) o, in alcuni casi, dal loro browser.
- **YubiKey**: Consente agli utenti del tuo sito di utilizzare l'Autenticazione Multi-fattore utilizzando un token hardware sicuro YubiKey. Gli utenti hanno bisogno del proprio YubiKey disponibile su www.yubico.com.
- **Autenticazione Web**: supportata da tutti i browser moderni. La maggior parte dei browser offre un'autenticazione specifica del dispositivo protetta da una password e/o biometria (sensore di impronte digitali, scansione del volto, ...).
- **Codice di Autenticazione via Email**: Usa codici di sicurezza a sei cifre, con limite di tempo, inviati via email. L'impostazione predefinita è di 2 minuti.
- **Codice Fisso**: è pensato per il test e l'illustrazione ed è disabilitato per impostazione predefinita. Non dovrebbe essere abilitato su un sito di produzione.

Nota che esiste un plugin separato **Sistema - Accesso Passwordless WebAuthn** per gestire l'accesso dal pulsante di Autenticazione Web nel modulo di accesso.

## Opzioni Utenti

Il modulo Utenti: Opzioni ha un modulo di Autenticazione Multifattoriale per configurare il funzionamento dell'Autenticazione Multifattoriale in Joomla. Seleziona il pulsante Attiva/Disattiva Guida In Linea per ottenere informazioni su ciascuna opzione.

![opzioni utenti modulo autenticazione multifattoriale](../../../en/images/users/users-configuration-mfa.png)

## Profilo Utente

Il modulo Amministratore / Utenti: Modifica Profilo ha schede separate per
l'accesso WebAuthn e l'autenticazione multi-fattore, ma quest'ultima è visibile solo
al proprietario dell'account. Anche gli Utenti Super non vedono questa scheda per
altri utenti.

Il modulo Sito / Modifica il Tuo Profilo ha le schede del modulo backend disposte una
sopra l'altra, il che può risultare confuso perché l'Autenticazione Web
appare due volte, prima per l'accesso senza password e poi per l'Autenticazione Multi-Fattore. L'illustrazione seguente mostra la parte del modulo relativa all'Autenticazione Multi-fattore dopo che è stato creato un metodo. Questo imposta automaticamente la funzionalità su Abilitata e mostra l'opzione per creare
Codici di Backup.

![vista del sito del modulo di autenticazione multi-fattore utente](../../../en/images/users/multi-factor-authentication-site-profile.jpg)

Come accennato in precedenza, puoi provare ciascuno di essi selezionando il pulsante + Aggiungi ..., ma seleziona Annulla nel modulo successivo se decidi di non
procedere.

*Tradotto da openai.com*

