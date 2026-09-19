<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "Configurazione dell'ambiente locale",
    "description": " ",
    "author": ""
}
-->

A partire da Joomla! 4 abbiamo modificato il processo di sviluppo. Non è più
possibile clonare il repository e avere un'installazione di Joomla utilizzabile.
Seguiamo le best practice e implementiamo un processo di compilazione per il CMS.

## Guida introduttiva rapida

I passaggi per configurare l'ambiente di sviluppo dipendono dal sistema
operativo. Non possiamo scrivere documentazione per ogni sistema operativo (SO);
utilizza il tuo motore di ricerca preferito per trovare una guida.

### Strumenti necessari

1.  PHP - sostanzialmente lo stesso necessario per eseguire un sito Joomla, ma
    è necessaria la versione CLI (interfaccia a riga di comando) di PHP. (Vedere
    la pagina [Configurazione di un server LAMPP per lo sviluppo PHP](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer - per gestire le dipendenze PHP di Joomla. Per assistenza
    nell'installazione di Composer, leggere la documentazione
    all'indirizzo <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js - per compilare i file JavaScript e SASS di Joomla. Per assistenza
    nell'installazione di Node.js, seguire le istruzioni disponibili
    all'indirizzo <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Nota,
    sarà necessario NodeJS 12 o superiore per installare Joomla.
4.  Git - per la gestione delle versioni.

### Passaggi per configurare l'ambiente locale

1.  Clonare il repository
2.  Eseguire il checkout del branch dell'ultima release.
3.  Eseguire `composer install` (composer = gestore dei pacchetti per PHP) dalla
    directory principale del repository git. (È possibile aggiungere
    *--ignore-platform-reqs* se PHP-LDAP non è installato localmente e non è
    necessario.)
4.  Eseguire `npm ci` (npm = gestore dei pacchetti per JavaScript, il parametro "ci"
    significa "installazione pulita") dalla directory principale del repository git.
    (Nota: per questa operazione è necessaria la versione 10.1.0 o superiore di npm.
    Eseguire `npm install -g npm@lts` per aggiornare la versione di npm alla
    versione LTS.)

Gli utenti Linux e OSX possono configurare il seguente alias bash inserendo quanto segue nel file *~/.bashrc*:

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Questo eliminerà tutti i file compilati nel sistema ed eseguirà una nuova installazione con un unico comando chiamando `jinstall` all'interno dell'installazione di Joomla.

## Una guida introduttiva un po' più lunga

Joomla è simile a molti altri strumenti web moderni. Contiene una grande
componente PHP e sempre più codice JavaScript. Sebbene la programmazione in
PHP non richieda molta preparazione, JavaScript necessita di numerosi
strumenti di supporto. Il motivo principale è che nessuno scrive codice in un
modo comprensibile da ogni browser, quindi il codice deve essere trasformato,
ad esempio da ES6 a una versione compatibile di JavaScript. Lo stesso vale
per i CSS. Per Joomla utilizziamo SASS, che verrà convertito in CSS nativo,
in modo che qualsiasi browser possa comprenderlo. Di contro, configurare un
ambiente di sviluppo è un po' più complicato, ma gli strumenti rendono la
programmazione più comoda. Grazie ai watcher e al ricaricamento automatico
del browser, puoi vedere le modifiche in tempo reale.

### PHP

Dovrebbe essere sufficiente eseguire `composer install`, poiché installerà le dipendenze PHP salvate nel file *composer.lock*. È possibile eseguire questo comando tutte le volte che si desidera. Installerà nuovi pacchetti solo quando il file *composer.lock* viene modificato. Non eseguire `composer update`, poiché aggiornerà tutti i pacchetti alle versioni più recenti e aggiornerà il file *composer.lock*.

**Nota:** potrebbe essere necessario eseguire `composer install` con l'opzione `--ignore-platform-reqs` per ignorare i requisiti della piattaforma specificati in Composer. Ad esempio, se l'estensione LDAP di PHP non è installata.

### Script Node/npm

Node.js include un gestore di pacchetti chiamato NPM (per certi versi simile a Composer). NPM dispone di un comando `run` e abbiamo preparato alcuni script per semplificare il lavoro. È necessario eseguire i comandi dalla directory principale del repository quando si modificano file JS o SASS. In precedenza era necessario eseguire una volta `npm ci` per installare le dipendenze.

#### npm run build:css (fino a Joomla 6.1)

Compilerà i file SASS in CSS e creerà anche i file minificati.

#### npm run build:js (fino a Joomla 6.1)

Compilerà e transpilerà i file JavaScript nel formato corretto
e creerà i file minificati.

#### Da Joomla 6.2 utilizzare i seguenti comandi:

- npm run build -- -n <extension> per ricostruire un'estensione specifica 
- eseguire npm run builders-list per trovare il nome dell'estensione
- npm run build -- --all per ricostruire tutto

## Possibili problemi

Quando esegui composer install puoi imbatterti in questi errori

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

La soluzione consiste nell'eseguire composer install con
l'opzione `--ignore-platform-reqs` per ignorare i requisiti della piattaforma
specificati in Composer. Ciò si verifica se non hai installato l'estensione LDAP
di PHP.

```
    composer install --ignore-platform-reqs
```

Se ricevi un errore di accesso come quello mostrato di seguito, elimina
il file `administrator/cache/autoload_psr4.php`.

![schermata dell'errore di accesso a Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)

*Tradotto da openai.com*