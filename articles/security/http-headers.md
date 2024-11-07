<!-- Filename: https://magazine.joomla.org/all-issues/may-2022/joomla-new-http-headers-plugin-for-j4 / Display title: Intestazioni HTTP   -->

## Articolo di Rivista

Questo articolo è basato su un articolo del Joomla! Community Magazine di Brendan Hedges nell'edizione di maggio 2022.

Sebbene scritto per Joomla 4, il contenuto si applica ugualmente a Joomla 5.

## Il Nuovo Plugin per le Intestazioni HTTP di Joomla per J4

A seguito dell'articolo del mese scorso su sicurezza, password e il plugin WebAuthn di Joomla, questo mese daremo un'occhiata a un'altra caratteristica di sicurezza di Joomla lanciata con J4. Si tratta del plugin per le Intestazioni HTTP, che ora è incluso come parte delle funzioni principali di Joomla.

Internet è in continua evoluzione e Joomla non rimane mai molto indietro. È per questo che lo scelgo come la mia piattaforma preferita per lo sviluppo web. Non importa se il tuo sito web è un piccolo sito familiare o una piattaforma di e-commerce completamente sviluppata con milioni di vendite; il framework di Joomla ha qualcosa per tutti ed è sempre alla ricerca di implementare nuove tecnologie. Alcune sono addirittura rivoluzionarie.

> L'introduzione del plugin per le Intestazioni HTTP nel core di Joomla 4 è un grande passo avanti per aiutare a proteggere il tuo sito web da attacchi e attività dannose.

Questo plugin di sicurezza del sistema aiuta i proprietari di siti a configurare facilmente le Intestazioni di Sicurezza HTTP dal familiare backend di Joomla, invece di dover armeggiare nel file htaccess o in altri file di configurazione. O, ancor peggio, nel Cpanel del tuo hosting web.

Guarda quanto è complicato configurare questo su Cpanel e dimmi che non commetterai un errore! E, tutto ciò supponendo che una volta che il framework è installato in Apache e le directory create, tu conosca il formato corretto per aggiungere le intestazioni HTTP che desideri integrare.

Quante volte hai cercato di implementare un comando htaccess solo per ricaricare il tuo sito web e poi affrontare un errore http500?

Il problema più grande è che se non ottieni il formato della tua Intestazione HTTP perfetto, romperai il tuo sito.

Anche in quel caso, ciò che funziona per un sito web potrebbe non funzionare per un altro. Un buon esempio di questo è il mio file htaccess e il modo in cui ho impostato il browser per caricare una versione non www https del mio sito web:
```
## Da www a non www e da http a https mix
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteRule ^ https://mysito.it%{REQUEST_URI} [R=301,L,NE]
## Fine da www a non www e da http a https mix
```

Questo funzionava alla grande per la mia precedente azienda di hosting. Ma quando sono passato a un host diverso, ha smesso di funzionare. Vai a capire!

Il codice htaccess che ora devo usare per ottenere lo stesso risultato è simile a questo:
```
## Da www a non www e da http a https mix
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]
RewriteCond %{ENV:HTTPS} !on
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
## Fine da www a non www e da http a https mix
```

Confondente, giusto? E, se commetti un solo errore nel formato, BAM! Hai rotto il tuo sito web! Beh, almeno finché non correggi il tuo codice.

Ecco perché mantenere le cose semplici, come parte del core di Joomla, significa meno frustrazione, meno tempo perso a cercare su Google i tuoi errori e più tempo per festeggiare mentre ti rilassi sulla tua sedia e ammiri il tuo nuovo sito web.

Quindi, vediamo cosa sono effettivamente le intestazioni HTTP, come puoi trovare il plugin e cosa puoi fare con esse. È però opportuno menzionare qui che questa funzione di Joomla è una funzione avanzata di Joomla, che è più adatta a siti web sensibili ai dati, piuttosto che al nuovo sito web che hai amorevolmente creato sui tuoi teneri gattini. Tuttavia, detto ciò, anche i siti web semplici dovrebbero essere il più sicuri possibile per evitare che venga eseguito codice dannoso dopo che hanno violato il tuo sito web.

## Cosa sono gli header HTTP?

Gli header HTTP non vanno confusi con la sezione &lt;head&gt; del documento HTML. Sono completamente diversi. Gli header HTTP sono il preambolo tra il tuo server web e il browser. Un insieme di istruzioni che dicono al browser cosa, o più precisamente cosa non mostrare al visitatore.

Puoi vedere gli HTTP Header e come si riferiscono ai singoli oggetti HTML negli strumenti di sviluppo del tuo browser. In Google Chrome, apri gli strumenti di sviluppo, quindi la scheda Rete. Ora aggiorna la pagina web e clicca su un elemento HTML nel pannello di sinistra. Mostrerà l'HTTP Header per quell'elemento nel pannello di destra.

Puoi vedere nell'immagine sotto che l'immagine evidenziata restituisce un codice di stato HTTP di 200, quindi il browser l'ha trovata. C'è anche una serie di altre informazioni legate a quell'elemento, come la dimensione del file e le date di modifica.

![Joomla http headers 1](../../../en/images/security/http-headers-dev-tools-headers.png "")

Se uno dei tuoi elementi HTML non viene visualizzato, potresti anche ricevere un indizio sul motivo negli header HTTP. In questo esempio, la seconda immagine non è stata visualizzata e puoi vedere dalle informazioni nel pannello di destra che non c'è alcuna informazione nell'HTTP Header.

Eccetto il messaggio criptico:

**Politica del Referente:** 'strict-origin-when-cross-origin'

'Strict-origin-when-cross-origin' significa semplicemente che quando un elemento HTML (un'immagine in questo caso) è servito da una fonte diversa (non il tuo server), deve essere seguita la politica degli header HTTP impostata in quel momento. In questo esempio, gli HTTP Header, come impostato nel plugin di Joomla, rifiuteranno tutte le immagini che non provengono né da questo sito web, né da un altro sito web specificamente 'incluso' nei parametri degli HTTP Header impostati nel plugin degli header HTTP di Joomla.

Quindi, quando l'immagine è richiesta dal documento HTML, il browser la rifiuta e non viene caricata.

![Joomla http headers 2](../../../en/images/security/http-headers-dev-tools-headers-reject.png "")

Che differisce dal non essere trovata e restituire un messaggio di errore HTTP 404 non trovato. In questa situazione, l'immagine viene ancora cercata sul server che la ospita, ma il browser non l'ha trovata.

![Joomla http headers 3](../../../en/images/security/http-headers-dev-tools-headers-not-found.png "")

## Cosa fa il Plugin Joomla HTTP Headers

Oltre a indicare al browser cosa visualizzare e a restituire informazioni generali sul documento HTML, gli HTTP Headers aiutano a mitigare attacchi e vulnerabilità di sicurezza che potresti avere sul tuo sito Joomla. È qui che entra in gioco il plugin Joomla HTTP Headers. Questo plugin lo realizza con l'esplicita visualizzazione del contenuto HTML basata sulle impostazioni configurate direttamente nel plugin Joomla HTTP Headers.

Aggiungendo header HTTP basati sulla sicurezza extra al tuo sito Joomla con il plugin HTTP Header fornirai un ulteriore livello di sicurezza al tuo sito Joomla.

Questo è importante perché, di default, una pagina web HTML mostrerà tutto il suo contenuto al tuo visitatore, buono o cattivo, a meno che non gli venga esplicitamente detto di non farlo negli HTTP headers della pagina web. Il plugin lo consente permettendoti di configurare le opzioni avanzate di sicurezza disponibili in Content-Security-Policy per il tuo sito. Il plugin può essere configurato in modo diverso per ogni sito a seconda delle tue esigenze, rendendolo un'arma veramente flessibile nel tuo arsenale contro gli hacker.

## Perché ho bisogno di questo plugin?

In un mondo ideale, non ne avresti bisogno. Tuttavia, nel mondo in cui viviamo, ci sono troppe persone senza scrupoli che cercano modi per guadagnare denaro dagli innocenti e dagli inconsapevoli. Nel nostro mondo, ci riferiamo a queste persone come hacker. Gli hacker si danno da fare per sfruttare le vulnerabilità del software per guadagni monetari, spesso a discapito del proprietario del sito web.

Utilizzando il plugin Joomla HTTP Header per controllare quale contenuto viene servito ai tuoi visitatori, riduci le possibilità che gli hacker possano servire contenuti dannosi ai tuoi visitatori tramite plugin vulnerabili obsoleti. Questo aiuta a fermare le iniezioni di script dannosi sul tuo sito web.

**Quindi, pensiamo a questa situazione ipotetica per un minuto.**

Hai un bel sito Joomla 3. È stato realizzato 5 anni fa, e ancora appare e funziona perfettamente. Tutti i tuoi componenti, plugin e moduli sono aggiornati. Perfetto, giusto?

Beh, non proprio, perché quando hai creato il tuo sito web 5 anni fa, hai installato il trendy Foo Bar Plugin per stampare "FOO BAR" sulla tua pagina iniziale. All'inizio sembrava fantastico, ma dopo un po' hai cambiato idea e hai eliminato gli shortcode del plugin {foo}FOO - BAR{/bar} dall'articolo della tua homepage.

Ma, ecco il problema: non hai disattivato o disinstallato il plugin stesso e il suo utilizzo è svanito dalla tua memoria. **Sono sicuro che è qualcosa di cui siamo tutti colpevoli.**

Arriviamo ad oggi, 5 anni dopo, quel plugin è ancora lì, pubblicato e attivo sul tuo sito, ma non è stato aggiornato per 5 anni perché da tempo te ne sei dimenticato, o l'autore ha smesso di supportarlo. Ora, qualche individuo malintenzionato ha capito che questo plugin ha una vulnerabilità di sicurezza che può essere sfruttata per avviare un attacco di **Cross Site Scripting (XSS)** sul tuo sito web, e fare delle tue ignare visite delle vittime.

Il Cross-site scripting, noto anche come XSS, è una vulnerabilità di sicurezza nel tuo sito web che consente a un attaccante di compromettere le interazioni che i tuoi utenti hanno con il tuo sito ora vulnerabile.

L'attaccante/hacker usa XSS per sfruttare il tuo sito vulnerabile e inviare uno script dannoso al tuo ignaro utente. Poiché lo script proviene dal tuo sito, il browser del tuo utente non sa o non sospetta che lo script non dovrebbe essere fidato ed esegue lo script quando la pagina web si carica e si apre.

Gli script dannosi eseguiti in questo modo possono causare molti problemi al tuo utente, dal furto di password di accesso e dati degli utenti memorizzati nei cookie, all'invio del tuo utente a falsi siti di phishing. Gli script possono persino cambiare l'aspetto della pagina web servita dal tuo sito e mostrarti pubblicità diverse.

Utilizzare il **plugin Joomla HTTP Headers** aiuta a fermare il cross-site scripting assicurando che solo gli script e il contenuto che vuoi servire ai tuoi visitatori siano effettivamente serviti. Tutto il resto viene bloccato.

Quindi, nell'esempio sopra, avresti potuto configurare il plugin HTTP Headers per servire solo i file JavaScript (script) del tuo sito web da una cartella specificata, o magari da un CDN se ne usi uno, per fermare l'attacco.

Potresti anche impedire al tuo sito di eseguire JavaScript inline incorporato nell'HTML. Ma, sii consapevole che a seconda di come hai progettato l'HTML del tuo sito web, questo potrebbe causare problemi in futuro.

Ciò aiuterebbe a fermare l'esecuzione di codice JavaScript dannoso sul tuo sito web. Anche se il tuo vulnerabile Foo Bar Plugin fosse da incolpare per l'opportunità data a un hacker di iniettare codice dannoso nel tuo sito web in primo luogo.

**Nota:**

> I punti deboli comuni sui siti web soggetti ad attacchi XSS sono i moduli di input utente (pagine di login, moduli di iscrizione alla newsletter, moduli di contatto, ecc.) senza convalida e crittografia.

## Dove si trova il plugin HTTP Headers?

È possibile trovare il plugin HTTP Headers di Joomla insieme a tutti gli altri plugin di Joomla e vi si accede esattamente nello stesso modo a cui sei abituato.

![Joomla http headers 4](../../../en/images/security/http-headers-plugins.png "")

## Utilizzo del Plugin HTTP Headers

Utilizzare il Plugin HTTP di Joomla è relativamente semplice, anche se potrebbe essere una buona idea, prima di apportare modifiche alle impostazioni predefinite, familiarizzare con alcuni dei termini speciali relativi al suo utilizzo. Tuttavia, detto ciò, alcuni di essi dovrebbero già esserti familiari.

**Ad esempio:**

Quando si ha a che fare con le immagini, vedrai il termine 'img-src', dove 'img' si riferisce alle immagini e 'src' alla fonte valida dell'immagine. Questi sono termini con cui siamo già familiari grazie al HTML di base.

Alla fine di questo articolo, c'è un elenco di siti web utili con ulteriori informazioni per aiutarti a utilizzare questo plugin di Joomla.

## Impostazioni del Plugin HTTP Headers - Scheda 1

Quando apri il plugin, la prima scheda aperta sono le impostazioni base del plugin. Qui puoi effettuare regolazioni delle opzioni X-Frame, della Referrer-Policy, della Cross-Origin-Opener-Policy e anche Forzare gli Header HTTP. Ci sono anche alcuni link per ulteriori informazioni per aiutarti a comprendere in dettaglio cosa fanno questi elementi.

**Esaminiamo ognuno di questi a turno.**

![Joomla http headers 5](../../../en/images/security/http-headers-plugins-tab-plugin.png "")

### Opzioni X-Frame

La prima impostazione è per le Opzioni X-Frame. **È abilitata per impostazione predefinita.**

Questa opzione ti consente di decidere se il contenuto del tuo sito web può essere visualizzato su un altro sito web in un &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; o &lt;object&gt;. Se disabiliti questa opzione, qualsiasi altro sito web può visualizzare il tuo sito in un iframe.

Una volta abilitata, un tag ‘x-frame-options: SAMEORIGIN’ viene aggiunto agli header del tuo sito web. Questo tag ti consente ancora di mostrare il tuo contenuto in un &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; o &lt;object&gt; sul tuo sito web. Ma nessun altro può visualizzare il tuo contenuto in un &lt;iframe&gt; sul proprio sito web.

![Joomla http headers 6](../../../en/images/security/http-headers-plugins-headers.png "")

L'Header X-Frame Option aiuta a proteggere il tuo sito web e gli utenti da attacchi di **‘Click Jacking’**. Questo è quando un attaccante posiziona un &lt;iframe&gt; sul proprio sito web e imposta la fonte dell’&lt;iframe&gt; come il tuo sito web. Quindi l’attaccante usa più strati trasparenti del proprio sito web sopra di esso.

Questo induce un utente a cliccare su un pulsante o un link nello strato superiore trasparente perché l'utente crede di cliccare su un link nell'iframe sottostante.

Quindi, l'attaccante sta **"dirottando"** clic destinati alla pagina originale e inviandoli a una pagina web diversa.

Più seriamente, pratiche simili possono essere usate per raccogliere sequenze di tasti per dettagli di accesso di password e nome utente da account di email, account di social media, e naturalmente, dal tuo account bancario.

La maggior parte dei browser moderni supporta le Opzioni X-Frame, il che è fantastico. Quindi, la mia raccomandazione sarebbe di abilitare questa impostazione nel plugin degli header HTTP per aiutare a proteggere i tuoi utenti dal diventare vittime del 'Click Jacking'.

**La maggior parte dei browser moderni supporta le opzioni X-Frame.**

![Http headers browser support](../../../en/images/security/http-headers-plugins-xframe-browser-support.png "")

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Conclusione

Imposta questo per abilitare. Questo restringerà globalmente ciò che può essere fatto con &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; o &lt;object&gt; sul tuo sito web. Per aggiungere eccezioni, usa ‘Force HTTP Headers’ per aggiungere eccezioni granulari.
</div>

### Referrer-Policy

Il prossimo elemento nell'elenco della prima scheda è la **Referrer-Policy**. Questa, se abilitata, ti permette di scegliere quanto dei tuoi potenziali dati web viene trasferito a un altro sito web se un link o altro oggetto HTML viene cliccato sul tuo sito web.

Comunemente, lo vediamo impostato come un attributo HTML sui tag &lt;a&gt;, dove puoi formattare un link come &lt;a href=”https://someplace.com” rel=”noreferrer”&gt;Cliccami&lt;/a&gt;. Il tag noreferrer mantiene i dettagli della pagina web di invio segreti dalla pagina web ricevente. Fa questo rimuovendo le informazioni di referente dall’HTTP header della pagina web.

Essere consapevoli dei dati che il tuo sito web potrebbe ‘perdere’ a un altro sito web a cui colleghi è una parte importante nel garantire la sicurezza del tuo sito web e dei suoi utenti.

Questo è particolarmente vero se permetti agli utenti di registrarsi, contiene dati sensibili, o se il tuo sito web gestisce transazioni monetarie. Il plugin HTTP Headers di Joomla aiuta a controllare questo a livello globale, piuttosto che a livello di singolo link.

Per impostazione predefinita, la Referrer Policy del tuo sito web è impostata su ‘strict-origin-when-cross-origin’. Che non blocca nessuno dei dati del referente della pagina web di origine a meno che non venga inviato a una pagina http meno sicura. Ma, poiché la maggior parte delle pagine web usano https di questi tempi, questo è ora un problema maggiore rispetto al passato.

![Joomla http headers 8](../../../en/images/security/http-headers-plugins-headers-referer-policy.png "")

Ci sono, ovviamente, molti usi innocenti di questi dati ‘perduti’ se non stabilisci una Referrer Policy per il tuo sito web. Questi potrebbero includere dati raccolti dal sito web collegato per analisi, registrazione, o caching ottimizzato.

Purtroppo, non tutti i siti web a cui ci si riferisce utilizzano i tuoi dati ‘perduti’ per tali operazioni innocenti. Prendiamo il seguente situazione come esempio.

La maggior parte dei siti web che permettono la registrazione degli utenti avrà un link per il reset della password accanto al proprio modulo di login su una pagina di accesso/registrazione. È anche probabile che la pagina web contenga altri link a siti web esterni, link ai social media, o forse ci sono dei ‘Link utili’ nel footer.

Questi portano tutti fuori dal tuo ambiente sicuro. Ora, se non c'è una Referrer Policy in atto, è possibile che l'Header del Referente inviato a uno di quei siti web esterni quando si clicca su un link da quella pagina di accesso possa contenere il link per il reset della password. Così come altre informazioni che hai condiviso con quel sito web esterno.

Questo potrebbe costituire un rischio per la sicurezza dell'utente compromettendo i loro dati.

A causa del potenziale rischio per la sicurezza su questo tipo di pagina sensibile ai dati, è anche buona prassi rimuovere tutti i contenuti di terze parti dalla pagina. Questo includerebbe tutti i link e i contenuti forniti nei &lt;iframes&gt; come widget dei social media e video di YouTube. Poiché i dati inseriti su questa pagina potrebbero essere inviati tramite l'Header del Referente a quei siti se clicchi su quel video del gattino carino che è appena apparso.

Il plugin HTTP Headers di Joomla affronta questo problema consentendoti di scegliere una delle 8 Referrer Policies per stabilire una Referrer Policy per il tuo sito web. Ognuna con i propri limiti su quando e quanto condividere i dati.

![Joomla http headers 9](../../../en/images/security/http-headers-plugins-headers-referer-policy-setting.png "")

Diamo un'occhiata a questi. C'è un'eccellente descrizione di essi sulla pagina Mozilla Headers che li descrive come:

* **no-referrer**<br>
    L'Header del Referente sarà omesso: le richieste inviate non includono alcuna informazione del referente.
* **no-referrer-when-downgrade**<br>
    Invia l'origine, il percorso e la stringa di query nell'Header del Referente quando il livello di sicurezza del protocollo rimane lo stesso o migliora (HTTP→HTTP, HTTP→HTTPS, HTTPS→HTTPS). Non inviare l'Header del Referente per le richieste a destinazioni meno sicure (HTTPS→HTTP, HTTPS→file).
* **origin**<br>
    Invia solo l'origine nell'Header del Referente. Ad esempio, un documento su https://example.com/page.html invierà il referente https://example.com/.
* **origin-when-cross-origin**<br>
    Durante l'esecuzione di una richiesta stessa origine allo stesso livello di protocollo (HTTP→HTTP, HTTPS→HTTPS), invia l'origine, il percorso, e la stringa di query. Invia solo l'origine per le richieste di origine incrociata e richieste a destinazioni meno sicure (HTTPS→HTTP).
* **same-origin**<br>
    Invia l'origine, il percorso, e la stringa di query per richieste di stessa origine. Non inviare l'Header del Referente per richieste di origine incrociata.
* **strict-origin**<br>
    Invia solo l'origine quando il livello di sicurezza del protocollo rimane lo stesso (HTTPS→HTTPS). Non inviare l'Header del Referente a destinazioni meno sicure (HTTPS→HTTP).
* **strict-origin-when-cross-origin (default)**<br>
    Invia l'origine, il percorso e la stringa di query durante l'esecuzione di una richiesta stessa origine. Per richieste di origine incrociata invia solo l'origine quando il livello di sicurezza del protocollo rimane lo stesso (HTTPS→HTTPS). Non inviare l'Header del Referente a destinazioni meno sicure (HTTPS→HTTP).
    **Nota:** Questa è la policy predefinita se non specifichi una policy o se il valore fornito è invalido. Precedentemente, il predefinito era no-referrer-when-downgrade.
* **unsafe-url**<br>
    Invia l'origine, il percorso e la stringa di query durante l'esecuzione di qualsiasi richiesta, indipendentemente dalla sicurezza.
    **Avviso:** Questa policy potrebbe perdere informazioni potenzialmente private dagli URL delle risorse HTTPS a origini insicure. Considera attentamente l'impatto di questa impostazione.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Conclusione

Come un buon inizio, a meno che non ci sia una ragione per non farlo, imposterei questo su ‘no-referrer’, quindi una policy "condividi niente" per il tuo sito web. Oppure, 'origin-when-cross-origin', che ti permetterà di analizzare il traffico sugli URL all'interno del tuo sito web (quindi nessuna ‘perdita’ di dati), ma solo inviare il tuo dominio come dominio di riferimento al sito web esterno, dato che nessun 'extra' dato dall'URL sarà allegato all'Header del Referente.
</div>

### Cross-Origin-Opener-Policy

La terza opzione da impostare nella prima scheda è il Cross Origin Opener Policy, che è una funzione di sicurezza basata sul browser che consentirà di scollegare diversi **‘Gruppi di Contesto del Browser'** l'uno dall'altro.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-policy.png "")

Un buon esempio di questo è l'uso dei pop-up. Dove il gruppo di contesto del browser originale (tutto il testo, le immagini, i link, ecc.) viene scollegato da un nuovo gruppo di contesto del browser che viene creato e quindi visualizzato nel pop-up.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-popup.png "")

> Questa opzione di Header HTTP è piuttosto dettagliata e complicata, sebbene ci siano solo 3 opzioni. Quindi ti incoraggio a dare un’occhiata ai link qui sotto per ottenere una migliore comprensione del perché questa opzione dovrebbe essere impostata sul tuo sito web. Così come imparare alcune delle funzionalità avanzate che diventano disponibili quando questa opzione è attiva.

Il Cross Origin Opener Policy aiuta a chiudere una storica falla nel modo in cui i browser condividono i dati tra diversi gruppi di contesto, in particolare quando sono in uso pop-up sul sito web.

Impostare il tuo **COOP** ti aiuterà a mitigare minacce alla sicurezza dei dati, quella comune è riferita come, **‘Spectre’**. Spectre rende dati che sono caricati nello stesso gruppo di contesto di navigazione come il tuo codice potenzialmente leggibili da un hacker. Spectre permette di misurare il tempo che certe operazioni richiedono. Questo permette agli hacker di indovinare cosa c’è nella cache della CPU. Se riescono in questo, sapranno cosa c'è nella memoria di processo. Avranno così accesso ai tuoi dati. Che potrebbero essere sensibili.

**COOP** funziona isolando i dati del tuo documento HTML originale dai dati HTML che verrebbero visualizzati in un pop-up dal documento originale. Questo aiuta a prevenire quelli che sono definiti attacchi cross-origin, o XS-Leaks.

Questo processo è simile all'abituale rel=”noopener” che usiamo sui link regolari. Ma, a differenza di rel=”noopener” che è attivo solo sui link in uscita, documenti che hanno il cross-origin-opener-policy impostato negli header HTTP dal plugin Joomla, restringono i dati in entrambe le direzioni. Pertanto, il documento HTML con una politica COOP attiva non avrà alcun riferimento ad esso nell'Header HTTP, e la proprietà window.opener HTTP Header della nuova finestra sarà impostata su null.

Durante l'impostazione di questa opzione nel plugin Joomla HTTP Header, ci sono 3 opzioni disponibili per te.

* **unsafe-none**<br>
    Questo è il valore predefinito. Consente che il documento sia aggiunto al gruppo di contesto di navigazione del suo aprente a meno che l'aprente stesso non abbia una cross-origin-opener-policy di same-origin o same-origin-allow-pop-ups.
* **same-origin-allow-popups**<br>
    Questa opzione mantiene riferimenti a finestre o schede aperte di nuovo che non impostano una cross-origin-opener-policy o che escludono l'isolamento impostando una cross-origin-opener-policy di unsafe-none.
* **same-origin**<br>
    Isola il gruppo di contesto di navigazione solo ai documenti di stessa origine. I documenti di origine incrociata non sono caricati nello stesso gruppo di contesto di navigazione.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Conclusione

Un buon punto di partenza per il tuo sito web sarebbe di lasciare questa opzione nel plugin impostata su same-origin che è l'impostazione predefinita. Questo permetterà al contenuto nel tuo stesso sito web/dominio di essere caricato con successo nei pop-up, ma restringerà l'accesso agli elementi dall'essere caricati in un pop-up che provengono da una fonte esterna.

Come menzionato all'inizio di questa sezione, certe funzionalità avanzate dipendono dall'isolamento incrociato. Funzionalità come gli oggetti SharedArrayBuffer o metodi Performance.now() che certi service workers necessitano per timer non limitati, sono disponibili solo se il tuo documento ha un cross-origin-opener-policy HTTP Header con il valore ‘same-origin’ impostato.
</div>

### Force HTTP Headers

L'ultima opzione su cui focalizzarsi nella prima scheda è il Force HTTP Headers, che non deve essere confuso con ‘Force HTTPS’ nelle impostazioni generali di Joomla.

![Joomla http headers 11](../../../en/images/security/http-headers-plugins-force-http-headers.png "")

Questa sezione del plugin HTTP Header di Joomla ti permette di aggiungere, se lo desideri, una selezione di ‘altri’ headers non specificamente dettagliati nella scheda del plugin, oltre a forzare l'inclusione di alcuni che sono inclusi.

Dal menu a tendina, attualmente hai 10 opzioni. Ma vale la pena notare che alcune di queste **potrebbero essere eliminate nel tempo** poiché le policy degli header a cui si riferiscono sono destinate a cambiare, o essere ripensate.

Gli header HTTP attuali che puoi impostare direttamente qui sono header che puntano ai seguenti settori:

Puoi ottenere più informazioni su ogni funzionalità sul sito web Mozilla Developers.

#### Content-Security-Policy (elenco)

L'header di risposta Content-Security-Policy permette ai siti web di controllare le risorse che l'utente può caricare per ciascuna pagina web. Le policy specificano principalmente le origini dei server e gli endpoint degli script. Questo aiuta a proteggere dagli attacchi cross-site scripting.
Mozilla: Content-Security-Policy

#### Content-Security-Policy-Report-Only

L'header di risposta HTTP Content-Security-Policy-Report-Only permette agli sviluppatori web di sperimentare con le policy monitorando (ma non applicando) i loro effetti.
Mozilla: Content-Security-Policy-Report-Only

#### Cross-Origin-Opener-Policy (COOP)

L'header di risposta HTTP Cross-Origin-Opener-Policy (COOP) ti permette di garantire che un documento di primo livello non condivida un gruppo di contesto di navigazione con documenti di origine incrociata.
Mozilla: Cross-Origin-Opener-Policy

COOP isolerà il tuo documento e i potenziali attaccanti non possono accedere al tuo oggetto globale se lo aprissero in un pop-up, prevenendo una serie di attacchi di origine incrociata chiamati **XS-Leaks**.

#### Expect-CT (da Discontinuare)

L'header Expect-CT permette ai siti di optare per la segnalazione e/o l'applicazione dei requisiti di Trasparenza del Certificato, per prevenire l'uso di certificati emessi in modo improprio per quel sito che passa inosservato.
Mozilla: Expect-CT (da Discontinuare)

#### Feature-Policy (ora Deprecato)

L'header HTTP Feature-Policy fornisce un meccanismo per permettere e negare l'uso di funzionalità del browser nel proprio frame, e nel contenuto all'interno di qualsiasi &lt;iframe&gt; nel documento.
Mozilla: Feature-Policy

#### Permissions-Policy

Questo è il sostituto del Feature-Policy sopra.
Mozilla: Permissions-Policy (Sostituisce la Feature Policy sopra)

#### Referrer-Policy (nell’elenco)

L'header HTTP Referrer-Policy controlla quante informazioni del referente (inviate con l'Header del Referente) dovrebbero essere incluse nelle richieste.
Mozilla: Referrer-Policy

#### Report-To

Parte della Content-Security-Policy. L'header di risposta HTTP Content-Security-Policy Report-To istruisce l'utente-agente a memorizzare endpoint di segnalazione per un’origine.
Mozilla: Report-To

La direttiva report-to è destinata a sostituire la direttiva report-uri deprecata, report-to non è ancora supportata dalla maggior parte dei browser.

#### Strict-Transport-Security

L'header di risposta HTTP Strict-Transport-Security (spesso abbreviato in HSTS) informa i browser che il sito dovrebbe essere accessibile solo tramite HTTPS, e che qualsiasi tentativo futuro di accedervi utilizzando HTTP dovrebbe essere automaticamente convertito in HTTPS.
Mozilla: Strict-Transport-Security

Questo è più sicuro dell'implementare semplicemente un reindirizzamento HTTP a HTTPS (301) sul tuo server, dove la connessione HTTP iniziale è ancora vulnerabile ad un attacco man-in-the-middle.

#### X-Frame-Options (nell’elenco)

L'header di risposta HTTP X-Frame-Options indica se un browser dovrebbe essere autorizzato o meno a rendere una pagina in un &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; o &lt;object&gt;. I siti possono usare questo per evitare attacchi di click-jacking, assicurandosi che il loro contenuto non sia incorporato in altri siti.
Mozilla: X-Frame-Options

La sicurezza aggiuntiva è fornita solo se l'utente che accede al documento sta utilizzando un browser che supporta le X-Frame-Options.

L'header X-Frame-Options ha elementi figli chiamati frame-ancestors che sostituiscono l’header Frame-Options. Se una risorsa ha entrambe le policy, la policy frame-ancestors sarà applicata e la policy X-Frame-Options sarà ignorata.

Utilizzando il campo del valore dell'Header HTTP, puoi impostare i valori che desideri siano seguiti e assegnarli al tuo sito web, al sito amministrativo, o ad entrambi.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Conclusione

Vale la pena menzionare che il supporto del browser per gli header HTTP varia, quindi è una buona idea prima di implementare la tua scelta di Header HTTP controllare il suo supporto del browser per il tuo potenziale pubblico.

Se imposti una serie di Header HTTP per il tuo sito web e il browser dell'utente non supporta quell'opzione di Header, il browser la ignorerà.
</div>


## Impostazioni del Plugin HTTP Headers - TAB 2

### Strict-Transport-Security (HSTS)

**La scheda Strict Transport Security Policy è disabilitata per impostazione predefinita.**

![Joomla http headers 12](../../../en/images/security/http-headers-plugins-headers-strict-transport-security.png "")

Adoro fare ricerche. Perché a volte ti imbatti in un vero e proprio momento OMG! Questo è uno di quei momenti.

Wikipedia afferma:

> Netscape Communications ha creato HTTPS nel 1994 per il suo browser web Netscape Navigator. Inizialmente, HTTPS veniva utilizzato con il protocollo SSL. Mentre SSL si evolse in Transport Layer Security (TLS), HTTPS fu formalmente specificato dall'RFC 2818 nel maggio del 2000. Google ha annunciato a febbraio 2018 che il suo browser Chrome avrebbe contrassegnato i siti HTTP come "Non sicuri" a partire da luglio 2018. Questa mossa era volta a incoraggiare i proprietari di siti web ad implementare HTTPS, nel tentativo di rendere il World Wide Web più sicuro.” ……

Chi avrebbe mai pensato che Netscape avesse inventato i protocolli HTTPS tanto tempo fa? Ciò che è ancora più sorprendente è il tempo che ci è voluto per implementarli su Internet come lo conosciamo e amiamo oggi.

Da anni ormai ci hanno persuasi, forzati e infine minacciati di implementare HTTPS su tutti i nostri siti web. La maggior parte di noi si è arreso e il world wide web è ora finalmente sicuro. O lo è?

Ci sono, tuttavia, alcuni irriducibili o siti web dimenticati che utilizzano ancora solo http per fornire i loro contenuti, sebbene con un avviso “Questo sito web non è sicuro” di Google/Firefox ecc.

Una rapida ricerca su Google ha fatto emergere diverse liste obsolete di quei siti 'Solo HTTP colpevoli'. Sebbene, da quando sono state pubblicate quelle liste, molti siti web siano passati a HTTPS. Tuttavia, ci sono alcune evidenti esclusioni di organizzazioni che avresti pensato avrebbero dovuto sapere meglio.

Ad esempio:

* NGINX (http://nginx.org/)
* GNU (http://www.gnu.org/)
* L'Università di Washington (http://www.washington.edu/)

Secondo w3techs.com circa il 20% di tutti i siti web funziona ancora solo su HTTP.

**Quindi, perché è un problema?**

È un problema perché qualsiasi dato inviato e ricevuto dal browser di un utente è a rischio di intercettazione. Conosciamo questo attacco come **attacco man-in-the-middle**. Ora, questo può sembrare un dettaglio insignificante se il tuo sito web riguarda solo immagini di gattini carini.

![immagine di gattini carini](../../../en/images/security/http-headers-plugins-headers-kittens.jpg "")

Ma anche i siti web semplici possono diventare vittime di hacker e attaccanti che implementano il **click-jacking** e altri attacchi cross-origin che danneggiano i tuoi utenti.

Un sito web che non scambia dati utente o informazioni di accesso, **dovrebbe comunque utilizzare HTTPS**.

**Ok, torniamo al tema principale.**

Come già saprai, l'intero punto dell'HTTPS è di introdurre una connessione sicura tra il browser dell'utente e il tuo server. Una connessione in cui qualsiasi scambio di dati avviene in un ambiente sicuro che non può essere intercettato e copiato da una terza parte. Un uomo nel mezzo.

![attacco man in the middle](../../../en/images/security/http-headers-plugins-headers-man-in-middle.png "")

Ma sapevi che a meno che il tuo **Certificato SSL HTTPS** non utilizzi **TLS**, la tua connessione 'sicura' non è sicura come ti aspetteresti? Le connessioni HTTPS non TLS sono ancora **vulnerabili agli attacchi man-in-the-middle**.

Sebbene sia un vecchio post sul blog, questo articolo spiega bene come funziona un attacco man-in-the-middle.

I browser hanno ampiamente adottato TLS.

E SSL 1.3 non è direttamente compatibile con le versioni precedenti a meno che non venga eseguito in modalità compatibilità, il che potrebbe rappresentare un problema per alcuni.

![informazioni certificato tls](../../../en/images/security/http-headers-plugins-headers-tls.png "")

Usare il Plugin Joomla HTTP Header per gestire lo Strict-Transport-Security (HSTS) aiuta a mitigare gli attacchi man-in-the-middle, forzando l'uso del TLS nel browser web dei tuoi visitatori. TLS garantisce che tutta la comunicazione web avvenga sul lato client utilizzando un livello di trasporto sicuro.

**Stai usando un reindirizzamento 301 per servire la versione HTTP non sicura del tuo sito web alla versione sicura HTTPS?**

La maggior parte delle persone lo fa. I reindirizzamenti 301 sono istruzioni che la maggior parte dei proprietari di siti web imposta nel proprio file htaccess. Informa Google che la versione del sito web che dovrebbe essere utilizzata è quella HTTPS (sicura). Il problema con questo è che **il 301 è solo un reindirizzamento URL**, quindi il tuo sito web esegue comunque alcuni elementi della connessione iniziale su HTTP.

A differenza delle connessioni tra un utente e un server web che utilizzano HSTS, dove il server interagisce automaticamente solo tramite HTTPS.

HSTS ha però una debolezza, in quanto la prima connessione iniziale tra il browser dell'utente e il server web avviene ancora tramite HTTP. Ma tutte le connessioni successive sono automaticamente connesse tramite HTTPS fino alla scadenza dell'HTTP Header e questo intestazione viene resettata.

Diversamente da un reindirizzamento 301 standard, dove ogni caricamento della pagina include una richiesta http iniziale per avviare la connessione https.

Esiste una soluzione a questa debolezza nelle impostazioni HTTP Headers HSTS, attivare 'Preload'.

Che aggiungerà il tag 'Preload' all'intestazione di risposta.

Nelle impostazioni, c'è anche un elenco di preload **. Questa è una lista che è integrata in molti browser moderni. L'elenco informa il browser che la connessione a esempio.com deve essere effettuata solo tramite HTTPS. Eliminando quindi la necessità di effettuare anche la connessione iniziale tramite HTTP.

![preload hsts](../../../en/images/security/http-headers-plugins-headers-enter-domain.png "")

Una volta impostato HSTS nel plugin HTTP header di Joomla, tutti i necessari tag vengono aggiunti all'intestazione di risposta HTTP. Questo permette a qualsiasi browser utente che tenta di connettersi al tuo server che tutte le connessioni **devono essere fatte con HTTPS**, indipendentemente dal fatto che sia specificato nel tuo HTML o meno.

In sintesi, utilizzare il plugin di intestazioni HTTP di Joomla per integrare HSTS invece di affidarsi ai reindirizzamenti 301 per fornire i tuoi contenuti su HTTPS è un miglioramento della sicurezza importante. Un miglioramento che aiuta a fermare gli **attacchi man-in-the-middle** e fornisce al tuo utente un ambiente sicuro.

HSTS copre l'intero dominio, a differenza di un reindirizzamento 301 che copre solo un percorso specifico URI.

HSTS utilizza una cache separata del browser che è solitamente segregata, quindi non può essere facilmente o accidentalmente cancellata.

HSTS può essere precaricato in un browser. Questo assicura che un utente si connetta al tuo server solo con HTTPS, indipendentemente dal fatto che abbia visitato il sito in precedenza o meno.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Da portare via

Abilita: HSTS

Imposta max-age: Il valore predefinito è 1 anno (31536000) secondi, ma alcuni consigliano di impostarlo a 2 anni (63072000) secondi.

Abilita: Sottodomini - Se hai sottodomini, assicurati di avere un certificato SSL valido per coprirli o singolarmente o come jolly dal tuo dominio principale.

Abilita: Preload

Infine, invia il tuo dominio alla lista di precaricamento HSTS.
</div>

## Impostazioni del plugin HTTP Headers - TAB 3

### Politica di sicurezza dei contenuti (Tab 3)

**La scheda della Politica di sicurezza dei contenuti è disabilitata per impostazione predefinita.**

Quando abiliti la Politica di sicurezza dei contenuti di Joomla tramite il plugin HTTP Headers, stai dicendo al browser del tuo visitatore esattamente quali risorse caricare dal server del tuo sito Web. Questo è un ottimo modo per garantire che tu stia fornendo solo i contenuti che effettivamente desideri fornire.

![Scheda politica di sicurezza dei contenuti](../../../en/images/security/http-headers-plugins-headers-csp.png "")

Avere una Politica di sicurezza dei contenuti efficace in atto è un modo efficace per fermare attacchi come lo **scripting tra siti (XSS)** e il **Click Jacking** che originano dal tuo sito web.

Lo scripting tra siti, altrimenti noto come attacco **XSS**, è un attacco al tuo sito web in cui uno script dannoso viene "iniettato" in un sito web ignaro e altrimenti affidabile. Gli aggressori individuano un punto debole da sfruttare, che di solito è un'area in cui un utente può inserire dati.

Componenti obsoleti che consentono l'inserimento di dati da parte degli utenti, come i moduli per i commenti non validati, potrebbero avere vulnerabilità sfruttabili in un attacco di Cross Site Scripting. Ecco perché è una buona idea aggiornare sempre i componenti di Joomla e ridurre al minimo queste opportunità.

**Quindi, usando come esempio il modulo dei commenti infetto:**

Il tuo sito web utilizza un modulo dei commenti alla fine di un articolo per raccogliere discussioni degli utenti, come fanno molti siti web. Il che è fantastico.

La tua estensione per i commenti di dodgy-joomla-extensions.com funziona alla grande e i tuoi utenti la adorano. Ma non l'hai aggiornata da 5 anni e gli sviluppatori l'hanno abbandonata da tempo.

Ora, 5 anni dopo, Mr Hacker si rende conto che a causa di una vulnerabilità nel codice per il componente dei commenti, può nascondere un codice maligno in un commento che sembra altrimenti innocuo.

Ciò che quel codice fa alla fine può variare, ma quello su cui puoi contare è che ogni volta che la pagina del tuo articolo innocente viene caricata, con i commenti, anche quel codice dannoso viene caricato ed eseguito. Dopotutto è parte dell'HTML, e il browser non sa che non dovrebbe essere lì, o che non è affidabile.

Quindi, il codice dannoso viene eseguito. Forse controlla i dati dei tuoi cookie. Forse ruba dati sensibili conservati dal browser. Oppure, forse carica annunci da casinò online o siti per adulti. Forse ricarica completamente il codice HTML della tua innocente pagina web sui gattini carini da un file Javascript esterno per rubare i dettagli della carta di credito dei tuoi utenti.

**Infatti, a questo punto uno script può essere eseguito per fare praticamente qualsiasi cosa.**

Una buona Politica di sicurezza dei contenuti aiuta a fermare questo tipo di attacco, anche se la tua estensione compromessa diventa l'obiettivo di Mr Hacker.

Lo fa perché il plugin HTTP Header di Joomla consegna il CSP come un'intestazione di risposta HTTP, **che dice esplicitamente al browser cosa caricare**. Nelle impostazioni della scheda CSP nel plugin HTTP header, puoi mirare direttamente a **28 direttive di politica**. Le direttive aiutano a proteggere il tuo sito web utilizzando solo fonti approvate per i tuoi file e contenuti.

L'esempio di attacco sopra finisce per caricare un file JavaScript da una fonte diversa per modificare l'output HTML visualizzato sullo schermo. Questo potrebbe essere stato prevenuto aggiungendo la direttiva script-src 'self' nel CSP di Joomla nel plugin.

![Direttiva politica self](../../../en/images/security/http-headers-plugins-headers-policy-directive.png "")

In questo esempio, il browser caricherà solo file JavaScript nel documento HTML se provengono dal tuo dominio. Tutti gli altri file JavaScript saranno rifiutati, inclusi quelli di Mr Hacker.

Mentre questo aiuta a proteggere il tuo sito web, può anche impedire il caricamento di altri file JavaScript legittimi che desideri caricare mentre la pagina web viene visualizzata sullo schermo. Questi file esterni possono essere aggiunti come fonti nella lista bianca nella stessa direttiva. Ad esempio, se utilizzi bootstrap da un CDN, aggiungeresti:
```
script-src 'self' https://cdn.jsdelivr.net
```
In questo esempio, se hai problemi a caricare bootstrap dal CDN, https://cdn.jsdelivr.net, potresti provare ad aggiungere l'URL completo al file bootstrap di cui hai bisogno. Quindi, formateresti la tua direttiva in questo modo: `script-src 'self' https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js`.

![Direttiva politica self](../../../en/images/security/http-headers-plugins-headers-policy-directive-self.png "")

Aggiungere queste fonti esterne sarebbe più facile da implementare su un nuovo sito web mentre lo costruisci. Ma se scandagli attraverso il tuo HTML renderizzato con Dev Tools, dovresti essere in grado di trovare tutti i file esterni già utilizzati sul tuo sito web consolidato e includerli nel tuo CSP.

Quando aggiungi direttive alla tua Politica di sicurezza dei contenuti nel Plugin HTTP Headers, ci sono una **serie di valori core** puoi utilizzare per definire cosa dovrebbe essere caricato esplicitamente dal browser. Questi sono quelli di base per configurare la tua prima Politica di sicurezza dei contenuti.

Altre opzioni sono disponibili per alcune delle direttive più avanzate, un elenco completo e esempi di utilizzo possono essere trovati sul sito Content Security Policy (CSP) Quick Reference Guide.

* **'none'** blocca l'uso di questo tipo di risorsa.
* **'self'** corrisponde all'origine corrente (ma non ai sottodomini).
* **'unsafe-inline'** consente l'uso di JS e CSS inline.
* **'unsafe-eval'** consente l'uso di meccanismi come eval().

Quindi, diamo un'occhiata ad alcune di queste direttive. Ecco un elenco di alcune delle direttive disponibili nel plugin HTTP Headers di Joomla, insieme a una breve descrizione, per gentile concessione della Politica di sicurezza dei contenuti. Consiglio di visitare questo sito per ulteriori informazioni ed esempi.

<dl>
<dt>default-src</dt>
<dd>La direttiva default-src definisce la politica predefinita per il recupero di risorse come JavaScript, Immagini, CSS, Font, Richieste AJAX, Frame, Media HTML5.<br>
POLITICA DI DEFAULT-SRC ESEMPI<br>
default-src 'self' https://cdn.example.com
</dd>
<dt>script-src</dt>
<dd>Definisce fonti valide di JavaScript.<br>
POLITICA SCRIPT-SRC ESEMPIO<br>
script-src 'self' https://js.example.com
</dd>
<dt>style-src</dt>
<dd>Definisce fonti valide di fogli di stile o CSS.<br>
POLITICA STYLE-SRC ESEMPIO<br>
style-src 'self' css.example.com
</dd>
<dt>img-src</dt>
<dd>Definisce fonti valide di immagini.<br>
POLITICA IMG-SRC ESEMPIO<br>
img-src 'self' https://img.example.com https://example.com
</dd>
<dt>connect-src</dt>
<dd>Si applica a XMLHttpRequest (AJAX), WebSocket, fetch(), &lt;a ping&gt; or EventSource. Se non consentito il browser emula un codice di stato HTTP 400.<br>
POLITICA CONNECT-SRC ESEMPIO<br>
connect-src 'self'
</dd>
<dt>font-src</dt>
<dd>Definisce fonti valide di risorse di font (caricate tramite @font-face).<br>
POLITICA FONT-SRC ESEMPIO<br>
font-src https://font.example.com https://example.com
</dd>
<dt>object-src</dt>
<dd>Definisce fonti valide di plugin, per esempio &lt;object&gt;, &lt;embed&gt; o &lt;applet&gt;.<br>
POLITICA OBJECT-SRC ESEMPIO<br>
object-src 'self'
</dd>
<dt>media-src</dt>
<dd>Definisce fonti valide di audio e video, per esempio elementi HTML5 &lt;audio&gt;, &lt;video&gt;.<br>
POLITICA MEDIA-SRC ESEMPIO<br>
media-src https://media.example.com
</dd>
<dt>frame-src</dt>
<dd>Definisce fonti valide per il caricamento di frame. Nel CSP Livello 2 frame-src è stato deprecato a favore della direttiva child-src. Il livello 3 del CSP ha rimosso la deprecazione di frame-src e continuerà a deferire a child-src se non presente.<br>
POLITICA FRAME-SRC ESEMPIO<br>
frame-src 'self'
</dd>
<dt>sandbox</dt>
<dd>Abilita un sandbox per la risorsa richiesta simile all'attributo sandbox del iframe. Il sandbox applica una politica di origine comune, impedisce i pop-up, i plugin e lo script block esecuzione. Puoi mantenere il valore sandbox vuoto per mantenere tutte le restrizioni in atto, oppure aggiungere valori: allow-forms allow-same-origin allow-scripts allow-pop-ups, allow-modals, allow-orientation-lock, allow-pointer-lock, allow-presentation, allow-popups-to-escape-sandbox e allow-top-navigation.<br>
POLITICA SANDBOX ESEMPIO<br>
sandbox allow-forms allow-scripts
</dd>
<dt>report-uri</dt>
<dd>Istruisce il browser per POST report di fallimenti della policy a questo URI. Puoi anche usare Content-Security-Policy-Report-Only come nome di intestazione HTTP per istruire il browser a inviare solo report (non blocca nulla). Questa direttiva è deprecata nel CSP Livello 3 a favore della direttiva report-to.<br>
URI RAPPORTO ESEMPIO<br>
report-uri /some-report-uri
</dd>
<dt>child-src</dt>
<dd>Definisce fonti valide per web worker e contesti di navigazione annidati caricati utilizzando elementi come &lt;frame&gt; e &lt;iframe&gt;<br>
POLITICA CHILD-SRC ESEMPIO<br>
child-src 'self'
</dd>
<dt>form-action</dt>
<dd>Definisce fonti valide che possono essere utilizzate come azione HTML &lt;form&gt;.<br>
POLITICA FORM-ACTION ESEMPIO<br>
form-action 'self'
</dd>
<dt>frame-ancestors</dt>
<dd>Definisce fonti valide per incorporare la risorsa utilizzando &lt;frame&gt; &lt;iframe&gt; &lt;object&gt; &lt;embed&gt; &lt;applet&gt;. Impostando questa direttiva a 'none' dovrebbe essere approssimativamente equivalente a X-Frame-Options: DENY. Quando questa direttiva è attiva, e se il browser la supporta, sovrascriverà le impostazioni nei X-frame-options.<br>
POLITICA FRAME-ANCESTORS ESEMPIO<br>
frame-ancestors 'none'
</dd>
<dt>plugin-types</dt>
<dd>Definisce tipi MIME validi per i plugin invocati tramite &lt;object&gt; e &lt;embed&gt;. Per caricare un &lt;applet&gt; devi specificare application/x-java-applet.<br>
POLITICA PLUGIN-TYPES ESEMPIO<br>
plugin-types application/pdf
</dd>
<dt>base-uri</dt>
<dd>Definisce un set di URL consentiti che possono essere utilizzati nell'attributo src di un tag base HTML.<br>
POLITICA BASE-URI ESEMPIO<br>
base-uri 'self'
</dd>
<dt>report-to</dt>
<dd>Definisce un nome di gruppo di report definito da un'intestazione di risposta HTTP Report-To. Per ulteriori informazioni, vedi l'API di Reporting.<br>
DIRECTIVE REPORT-TO ESEMPIO<br>
report-to groupName
</dd>
<dt>worker-src</dt>
<dd>Restringe gli URL che possono essere caricati come Worker, Shared Worker o Service Worker.<br>
POLITICA WORKER-SRC ESEMPIO<br>
worker-src 'none'
</dd>
<dt>manifest-src</dt>
<dd>Restringe gli URL da cui possono essere caricati i manifesti delle applicazioni.<br>
POLITICA MANIFEST-SRC ESEMPIO<br>
manifest-src 'none'
</dd>
<dt>prefetch-src</dt>
<dd>Definisce fonti valide per le richieste di prefetch e prerendering, per esempio tramite il tag link con rel="prefetch" o rel="prerender":<br>
POLITICA PREFETCH-SRC ESEMPIO<br>
prefetch-src 'none'
</dd>
<dt>navigate-to</dt>
<dd>Restringe gli URL verso cui il documento può navigare in qualsiasi modo. Per esempio, quando si clicca su un link, si invia un modulo, o si invoca window.location. Se form-action è presente allora questa direttiva è ignorata per l'invio dei moduli. Stato dell'implementazione<br>
POLITICA NAVIGATE-TO ESEMPIO<br>
navigate-to https://example.com
</dd>
</dl>

Il plugin HTTP Headers di Joomla offre anche l'opportunità di **impostare alcuni parametri globali nella scheda Politica di sicurezza dei contenuti**.

![Joomla http headers 14](../../../en/images/security/http-headers-plugins-headers-csp-global.png "")

Puoi scegliere di applicare il CSP al tuo sito web, al sito amministrativo o a entrambi con l'impostazione client.

L'opzione 'Report-Only' ti consente di testare le tue direttive e controllarle per errori con Dev Tools prima di andare in diretta. È sempre divertente rintracciare il motivo degli errori di CSP nella console di Google!

Successivamente c'è l'impostazione 'Nonce'. Il Nonce, che significa 'numero utilizzato una sola volta', è un sistema che applica una stringa generata casualmente a un tag &lt;script&gt; o &lt;style&gt; inline incluso nel tuo HTML tramite l'API di Joomla. Queste istanze sono di solito implementate da sviluppatori di componenti / moduli / plugin Joomla di terzi quando installi quella funzionalità aggiuntiva sul tuo sito web.

Nell'immagine seguente, puoi vedere il tag &lt;style&gt; con un attributo rel nonce che è stato aggiunto agli &lt;stili&gt; CSS aggiunti al mio documento HTML dal componente Akeeba Backup.

![Stile Joomla http headers 16](../../../en/images/security/http-headers-plugins-headers-akeeba-style.png "")

Interessantemente, il core JavaScript e il CSS di Joomla aggiunti al documento HTML non includono attualmente un tag 'nonce'. Questo perché **fanno parte del 'core'** piuttosto che essere aggiunti tramite l'API di Joomla.

Se abiliti l'interruttore 'Nonce' nelle impostazioni CSP, abiliti quegli script e stili inline per essere resi dal browser come 'sicuri'. Dovrai anche impostare il tag Joomla {nonce} nella tua direttiva policy script-src a script-src 'self' {nonce}. Come fallback per i browser più vecchi che non supportano i 'nonce' puoi aggiungere anche {script-hashes} dopo il segnaposto {nonce}, in questo modo script-src 'self' {nonce} {script-hashes} (fai attenzione alla spaziatura). Ma non dimenticare di abilitare prima **Script Hashes**.

![Impostazioni Joomla nonce](../../../en/images/security/http-headers-plugins-headers-nonce-settings.png "")

Joomla genera casualmente la stringa di testo 'nonce' e la aggiunge ai tag &lt;style&gt; e &lt;script&gt;. Quando abiliti l'opzione 'nonce' nelle impostazioni del plugin, la stringa di testo viene passata all'Intestazione HTTP. Il browser quindi interpreta l'Intestazione HTTP ed elabora il corrispondente &lt;script&gt; o &lt;style&gt;. Allo stesso tempo, rimuove la stringa di testo Nonce dall'HTML renderizzato nel browser.

![Stile Joomla nonce](../../../en/images/security/http-headers-plugins-headers-nonce-style.png "")

Questo a sua volta, impedisce a Mr Hacker di poter dirottare la stringa di testo nonce e aggiungerla al suo codice iniettato. Anche se Mr Hacker riesce a iniettare il suo JavaScript nefasto nel tuo HTML, il browser lo bloccherà.

### Hash dei script

Sappiamo tutti che non dovremmo includere JavaScript inline nel nostro HTML, dovresti scriverlo in un file my-javascript.js e aggiungerlo all'&lt;head&gt; o messo appena prima del tag &lt;/body&gt;. Ma a volte siamo tutti colpevoli di farlo.

Il problema è che se fai questo, quindi aggiungi la direttiva CSP 'script-src 'self'' tutto il JavaScript inline sarà bloccato di default. È progettato per funzionare in questo modo per prevenire che il JavaScript iniettato di Mr Hackers possa essere eseguito sul tuo sito web.

C'è un override per questo con la direttiva script-src 'unsafe-inline', che consentirà al JavaScript inline di Mr Hacker di essere eseguito, così come il tuo codice affidabile. Questa non è la migliore opzione, per ovvi motivi.

**Script Hashes al salvataggio!**

Il plugin HTTP Headers di Joomla raccoglie automaticamente tutti gli &lt;stili&gt; e gli &lt;script&gt; **passati tramite l'API di Joomla** nel sito. Genera quindi i rispettivi hash e li passa tramite l'Intestazione HTTP. Il browser poi genera gli hash sul sito stesso e conferma che gli hash corrispondono. Se lo fanno, gli script vengono eseguiti, altrimenti vengono bloccati.

Per abilitare questa funzione del plugin, attiva l'interruttore su **'Enabled'**. Poi, nella tua direttiva di policy script-src aggiungi il valore 'self' {script-hashes}. Se usi la caratteristica 'nonce', così come 'script hashes', imposta il valore della direttiva come nell'esempio sopra del nonce.

![Hash degli script Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes.png "")

**Ora, è intelligente.**

Ma, ciò che è ancora meglio è che possiamo usare la stessa idea per elaborare manualmente gli hash degli script e aggiungerli alla nostra direttiva script-src 'self'. Ci vorrà un po' di lavoro per configurarlo e mantenerlo, ma potrebbe salvarti la barba se hai aggiunto del JavaScript in un articolo o modulo personalizzato.

Ci sono modi più dettagliati di fare questo utilizzando un generatore di hash sha256, sha384 o sha512. Ma poiché la maggior parte delle persone aggiungerà solo piccoli frammenti di JavaScript al proprio articolo o modulo personalizzato, lasceremo che gli strumenti Dev di Google facciano il lavoro per noi.

Il processo è semplice. L'unica differenza è come generiamo l'hash.

Supponendo che tu abbia abilitato il plugin HTTP Headers di Joomla, il CSP è attivo e hai la direttiva script-src 'self' impostata e salvata.

Passo 1 - Aggiungi il tuo JavaScript inline al tuo articolo o modulo personalizzato e salvalo. Non dimenticare di regolare le impostazioni del tuo editor per impedire che l'editor cancelli il tuo codice durante il salvataggio.

Passo 2 - Naviga fino alla tua pagina web con il tuo script dentro. Apri Dev Tools e nella scheda console vedrai un errore che assomiglia a:

Rifiutato di eseguire lo script inline perché viola la seguente direttiva di Politica di sicurezza dei contenuti: "script-src 'self'". Occorre la parola chiave 'unsafe-inline', un hash ('sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='), o un nonce ('nonce-...') per abilitare l'esecuzione inline.

![Strumenti errore Joomla script hashes](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes-tools-error.png "")

Passo 3 - Ora, devi solo copiare/incollare l'hash dal messaggio di errore nella tua direttiva JavaScript nel plugin e salvarlo di nuovo:

script-src 'self' 'sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='

![Hash degli script Joomla script src self hash](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash.png "")

Successivamente, ricarica la tua pagina web e controlla nuovamente tramite Dev Tools di Google. L'errore sarà ora andato e il browser caricherà il tuo script sulla pagina web.

**Nota:** C'è ancora un errore che appare nel mio esempio poiché il JavaScript aggiunto al mio articolo non è completo. Ma, mostra che il codice inline sta almeno cercando di funzionare.

Aggiungere hash al tuo codice inline è un buon modo per posizionarli nella whitelist nell'intestazione HTTP in modo che vengano comunque eseguiti, mentre qualsiasi codice inline che non sia esplicitamente hashed e aggiunto al tuo CSP sarà ancora bloccato. Togliendo quindi il tentativo di Mr Hackers di compromettere il tuo sito web.

![Joomla script hashes](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash-tools-error.png "")

**Nota:**

Se cambi il tuo JavaScript, dovrai ricalcolare il tuo hash e cambiare il valore nella direttiva CSP.

Se hai problemi a far funzionare i tuoi hash, ci sono 3 problemi comuni,
puoi trovare soluzioni nella pagina web Utilizzare un hash con CSP.

Strict Dynamic

Se abiliti l'opzione Strict Dynamic nel tuo CSP, questa prenderà l'autorità esplicita che hai dato a uno script tramite un hash o nonce e la applicherà a qualsiasi altro script direttamente collegato ad esso o da esso chiamato. Questa azione annulla le direttive predefinite come 'self' o 'unsafe-inline' applicate nelle tue direttive generali CSP a quegli script figli. Saranno ignorate.

Hash degli stili

L'hash degli stili del CSP funziona esattamente come funzionano gli hash del JavaScript sopra, ma usalo se aggiungi blocchi di stili CSS nel corpo del tuo HTML. Proprio come usare 'Hash degli Script', **abilita** la funzione nel plugin e imposta una direttiva di policy style-src per fare riferimento ad esso con il valore 'self' {style-hashes}.

![Hash degli stili Joomla](../../../en/images/security/http-headers-plugins-headers-csp-style-hash.png "")

**Nota:**

Se cambi il tuo CSS inline, piuttosto che il CSS creato dall'API di Joomla, dovrai ricalcolare il tuo hash e cambiare il valore nella direttiva CSP.

Frame Ancestors ‘self’

Questa opzione nel plugin consente di includere una pagina in un frame, ad esempio all'interno di un iframe, ma solo dal lo stesso sito.

Se vuoi consentire esplicitamente a un sito web diverso di incorniciare il tuo contenuto, puoi impostare una direttiva specifica 'frame-src'.

![Joomla style hashes frame src](../../../en/images/security/http-headers-plugins-headers-csp-style-hash-frame-src.png "")

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Take Away

A volte una buona CSP è più facile da costruire su un nuovo sito web mentre lavori sulle risorse esterne necessarie.

È importante utilizzare l'URL base completo e corretto per il dominio consentito nella direttiva CSP. Ad esempio: https://www.mywebsite.co.uk, o https://www.anotherwebsite.com

È anche possibile mirare ai sottodomini con la stessa CSP utilizzando i caratteri jolly. Ad esempio: https://*.example.org.

Non tutti i browser supportano tutte le direttive.

CSP supporta sha256, sha384 e sha512 Hash
</div>

## Nota Finale / Conclusione:

Scrivendo questo articolo mi sono reso conto di aver solo sfiorato la superficie di questo vasto argomento.

Mi piace scoprire argomenti che in precedenza avevo ignorato o di cui non sapevo nulla. Sei lo stesso anche tu?

La conclusione a cui sono giunto ricercando l'argomento degli Header HTTP, e in particolare, utilizzando il nuovo plugin J4 di Joomla per impostarli, è che tutti dobbiamo padroneggiare questo argomento. Ci sono troppi individui (hacker) là fuori che stanno semplicemente aspettando un'opportunità per approfittarsi di siti web con sicurezza debole. Quindi, non aiutate i vostri utenti a diventare vittime.

Divertiti a esaminare il plugin degli header HTTP di Joomla e impara come può contribuire a proteggere il tuo sito web.

Tuttavia, consiglio di fare ulteriori ricerche su questo argomento interessante prima di iniziare. Troverai nei link sottostanti degli spunti per avviare la tua ricerca. Acquisirai una comprensione molto migliore di come funziona Internet e di come il tuo sito interagisce con esso.

### Per Riferimento

Se hai bisogno di ripristinare il plugin, il plugin HTTP Headers è stato installato con le seguenti opzioni impostate:

Il plugin è abilitato di default.

* Le schede HSTS e CSP sono disabilitate di default.
* Le X-Frame-Options sono abilitate di default.
* La Referrer-Policy è inizialmente impostata su: strict-origin-when-cross-origin.
* La Cross-Origin-Opener-Policy è inizialmente impostata su same-origin.

Se sei arrivato a leggere fino a qui e hai pensato "Non è giusto, e J3?", "Perché non possiamo avere le stesse funzionalità in Joomla 3?". Beh, la buona notizia è che puoi. Sebbene dovrai scaricare il plugin dal [JED.

Una volta impostati gli header HTTP con il plugin di Joomla 4, puoi testare
i tuoi HTTP Headers sul sito web Security Headers.

Come hai ottenuto punteggio?

Assicurati che l'attivazione del plugin HTTP Headers può avere azioni inaspettate sul front end.

Infine, vorrei ringraziare Tobias Zulauf & Ced Keiflin per il loro contributo nel completare questo articolo in tempo!

