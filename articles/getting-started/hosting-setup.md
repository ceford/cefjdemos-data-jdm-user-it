<!-- Filename: J4.x:Hosting_Setup / Display title: Configurazione dell'Hosting -->

## Introduzione

Questa pagina fornisce alcune indicazioni per chi è completamente nuovo alla tecnologia di hosting. È possibile impostare un sito web sul proprio laptop o computer desktop. Questo è noto come hosting locale ed è un buon modo per sperimentare nuove funzionalità ed è completamente gratuito. Per rendere il contenuto del tuo sito web disponibile al resto del mondo, avrai bisogno di un account su un servizio di hosting e, per questo, dovrai pagare.

## Software di supporto

Joomla! è un'applicazione che dipende da tre elementi di software di supporto:
il linguaggio di scripting PHP, un database (uno tra MySQL, MariaDB o PostgreSQL)
e un server web (uno tra Apache, Nginx, Microsoft IIS, o ...). I numeri di versione
minimi sono indicati nelle tabelle seguenti:

### Requisiti per Joomla! 5.x

| Software           | Consigliato     | Minimo      |
|--------------------|-----------------|-------------|
| PHP                | 8.3             | 8.1.0       |
| **Database**       |                 |             |
| MySQL              | 8.1             | 8.0.13      |
| MariaDB            | 11.1.0          | 10.4.0      |
| PostgreSQL         | 16.0            | 12.0        |
| **Server Web**     |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.25            | 1.21        |
| Microsoft IIS      | 10              | 10          |

### Requisiti per Joomla! 4.x

| Software           | Consigliato     | Minimo      |
|--------------------|-----------------|-------------|
| PHP                | 8.2             | 7.2.5       |
| **Database**       |                 |             |
| MySQL              | 8.0             | 5.6         |
| PostgreSQL         | 11.0            | 11.0        |
| **Server Web**     |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.18            | 1.10        |
| Microsoft IIS      | 10              | 8           |

## Servizi di Hosting

I servizi di hosting commerciale forniscono tutto il necessario per supportare un sito web. Alcuni offrono anche l'installazione con un solo clic di applicazioni popolari come i sistemi di gestione dei contenuti, i forum di discussione, i wiki e così via. Ma si prega di notare: gli esperti del Forum di Joomla non raccomandano l'uso dell'installazione con un solo clic di Joomla.

Ogni servizio di hosting offre diversi piani a diversi livelli di prezzo. Più paghi, più spazio su disco e larghezza di banda ottieni, insieme a più indirizzi email, database e così via. Alcuni forniscono anche un nome di dominio gratuito. Per lo più, devi pagare per un nome di dominio e una piccola tassa di registrazione annuale.

## Hosting Gratuito

Non esiste un hosting gratuito! Tuttavia, un servizio di hosting partner di Joomla offre un sito web Joomla gratuito nel dominio joomla.com. Questo ti dà l'opportunità di provare il tuo sito web Joomla completamente funzionante senza alcun costo. È simile a un piano di hosting condiviso, ma con restrizioni e frequenti inviti ad effettuare l'upgrade a un piano a pagamento. Inoltre, il piano gratuito deve essere rinnovato ogni 30 giorni o verrà terminato. Il seguente articolo mostra i passaggi necessari per configurare un sito Joomla gratuito.

* [Hosting Gratuito Joomla](jdocmanual?article=user/hosting/free-hosting)

Se scopri che ti piace Joomla, puoi passare a un piano a pagamento o cercare altrove un servizio di hosting adatto alle tue esigenze e al tuo budget.


## Hosting Condiviso

Puoi ottenere un piano di hosting minimo per circa £/$/€50 all'anno. Questo livello di piano è spesso indicato come hosting condiviso ed è adatto a tutto ciò che non coinvolge dati sensibili. Le aziende dovrebbero cercare consulenza specialistica su piani di hosting appropriati. Scegliere un servizio di hosting non è privo di problemi. Il più economico potrebbe avere impostazioni *php.ini* inutilmente restrittive che non compaiono nella loro pubblicità. Alcuni potrebbero avere una pessima reputazione per quanto riguarda il supporto.

Se opti per un piano di hosting condiviso verifica quanto segue:

- Supporto per applicazioni PHP come Joomla, WordPress e Mediawiki.
- Spazio su disco: 500Mb è un minimo assoluto. 1Gb o più sarebbe meglio se si prevede di utilizzare molte immagini.
- Numero di Database: Joomla ne utilizza uno, ma presto scoprirai che ne hai bisogno di 5 o 10 o più. Alcuni piani offrono un numero illimitato all'interno dell'allocazione totale dello spazio su disco.
- Dimensione del database: con Smart Search il database può crescere molto rapidamente. Se l'hosting condiviso ha una restrizione sulla dimensione del database, sarà importante scoprire quale sia. Questo può portare a un sito non funzionante.
- Numero di indirizzi email: abbondanti!
- Numero di connessioni HTTP e DB al server, che alcuni host condivisi limitano.
- Backup: come vengono effettuati e se c'è un documento sui Termini di Servizio (TOS) che indica chi è responsabile per i backup.

Verifica anche il pannello di controllo e la piattaforma offerti. Giudicando dai post nei Forum, la maggior parte utilizza cPanel su Linux. Il servizio di hosting dovrebbe fornire tutto il software di supporto di base per il sito web:

- Server web Apache 2.4+ - *directory indexes* dovrebbero essere disabilitati. Supportati anche:
  - Nginx 1.18+ (meno utenti quindi meno supporto nei Forum)
  - Microsoft IIS\[6\] (meno utenti quindi meno supporto nei Forum)
- Database MySQLi 8.1+ o clone di MariaDB con supporto InnoDB. Supportato anche:
  - PostgreSQL 11.0+ (meno utenti quindi meno supporto nei Forum).
- PHP 8+ è raccomandato.
- Strumento di gestione del database phpMyAdmin.

Prima di acquistare, verifica i seguenti requisiti PHP minimi per Joomla:

- *memory_limit* - Minimo: 256M
- *upload_max_filesize* - Minimo: 64M
- *post_max_size* - Minimo: 64M
- *max_execution_time* - Consigliato: 30
- *allow_url_fopen* - vero

Molti di questi parametri possono essere impostati dall'utente in cPanel. Chiedi se è possibile.

Se hai acquistato un nome di dominio, il tuo servizio di hosting lo configurerà per te. Dovrebbero anche fornirti un indirizzo IP da utilizzare fino a quando la registrazione del tuo dominio viene propagata ai Domain Name Servers (DNS), solitamente entro poche ore.

Il seguente articolo mostra cosa aspettarsi se acquisti un piano di hosting che include un'interfaccia utente cPanel.

* [Hosting cPanel](jdocmanual?article=user/hosting/cpanel-hosting)

## Hosting VPS

Un piano di hosting con Server Virtuale Privato (VPS) fornisce pieno accesso a un server che condivide l'hardware. Si comporta come un computer dedicato. Puoi fermare e avviare il server, riavviarlo e installare il tuo software proprio come faresti su un computer desktop. Puoi creare account per utenti individuali proprio come nell'hosting condiviso. Tipicamente, puoi consentire alcune funzionalità che normalmente non sono permesse negli account di hosting condiviso.

I piani di hosting Dedicato e Cloud sono simili nel principio, ma offrono risorse dedicate o risorse personalizzate in base alle tue esigenze.

Questi piani avanzati non sono trattati qui.


## Ospitalità Locale

La maggior parte delle persone che sviluppano siti web mantengono copie locali su un laptop o un computer desktop per testare aggiornamenti o nuove estensioni o per provare nuovi design. Configurare un sito di sviluppo locale richiede alcune conoscenze tecniche, ma è abbastanza semplice seguire istruzioni semplici.

I seguenti articoli descrivono come configurare l'ospitalità locale su diversi tipi di computer desktop o laptop:

* [Ospitalità Locale su Windows](jdocmanual?article=user/hosting/local-hosting-on-windows) solo per Windows
* [Ospitalità Locale con XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp) per Linux, Mac e Windows.
* [Ospitalità Locale su Linux](jdocmanual?article=user/hosting/local-hosting-on-linux)

