<!-- Filename: J4.x:Using_the_CLI / Display title: Utilizzando la CLI -->

## Interfaccia a Riga di Comando (CLI)

Se hai accesso al terminale del server che esegue il tuo sito web, puoi utilizzare il CLI di Joomla per eseguire compiti di routine senza la necessità di usare le credenziali di accesso utente di Joomla. Anche senza accesso al terminale, come in alcuni account di hosting condiviso, puoi eseguire comandi CLI utilizzando cron job. I comandi CLI sono spesso più veloci o più convenienti rispetto agli equivalenti eseguiti tramite l'interfaccia dell'Amministratore di Joomla (o di cPanel). Esempi di casi in cui potresti preferire utilizzare la CLI includono il backup del sito e la messa offline/online del sito.

Il core di Joomla ha circa 30 comandi utili e puoi aggiungerne altri con estensioni aggiuntive. Ad esempio, potresti recuperare dati esterni come dati di geolocalizzazione o di tassi di cambio per un componente personalizzato.  

## Utilizzo del CLI

Il CLI viene utilizzato invocando l'eseguibile della riga di comando php. Questo spesso è diverso da quello utilizzato da un server web come Apache. Se stai utilizzando un cron job, potresti dover fornire il percorso completo all'eseguibile php, come segue:

    /usr/local/bin/php /home/nomeutente/public_html/[sottocartella facoltativa]/cli/joomla.php

Altrimenti, quando utilizzi la riga di comando del terminale, cambia directory nella directory cli di Joomla e inizia l'esecuzione del comando senza parametri:

    cd /home/nomeutente/public_html/[sottocartella facoltativa]/cli
    php joomla.php

![Elenco dei comandi](../../../en/images/command-line-interface/cli-command-list.png)

E prova alcuni comandi di aiuto per familiarizzare con ciò che aspettarti:

    php joomla.php help
    php joomla.php list
    php joomla.php help cache:clean
    php joomla.php help config:get

Ciascuna delle descrizioni di Aiuto e le stringhe di utilizzo sono codificate nei file della libreria Console o in plugin di terze parti.

Prova alcuni semplici comandi di azione:

    php joomla.php config:get debug
    php joomla.php cache:clean
    php joomla.php site:down
    php joomla.php site:up

## Opzioni

Se stai chiamando comandi da un cron, potresti non voler vedere alcun output:

    php joomla.php -q cache:clean

Nota che le opzioni possono utilizzare uno spazio o il segno di uguale, ma le variabili devono utilizzare il segno di uguale:

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Comandi

Una breve spiegazione di ciascun comando principale.

### Cache

Cancella le voci scadute dalla cache del sistema:

    php joomla.php cache:clean --help
    php joomla.php cache:clean

![Output di cache clean](../../../en/images/command-line-interface/cli-cache-clean.png)

    php joomla.php cache:clean expired

![Output di cache clean expired](../../../en/images/command-line-interface/cli-cache-clean-expired.png)

### Config

Ottieni o imposta una variabile di configurazione, una delle variabili in
configuration.php o un gruppo di variabili. I gruppi validi sono db, session,
mail,

    php joomla.php config:get debug --help
    php joomla.php config:get debug

![Output di config get debug](../../../en/images/command-line-interface/cli-get-debug.png)

    php joomla.php config:set debug=true

![Output di config set debug](../../../en/images/command-line-interface/cli-set-debug.png)

    php joomla.php config:get --group session

![Output di config get group session](../../../en/images/command-line-interface/cli-config-get-group-session.png)

### Core

Verifica la disponibilità di aggiornamenti o aggiorna Joomla.

    php joomla.php core:check-updates --help
    php joomla.php core:check-updates

![Output di core check updates](../../../en/images/command-line-interface/cli-check-updates.png)

    php joomla.php core:update --help
    php joomla.php core:update

![Output di core update](../../../en/images/command-line-interface/cli-core-update.png)

### Database

Esporta o importa il database. È possibile esportare o importare tutte le tabelle o una
tabella selezionata. Non usare questa funzione per importare tutte le tabelle di un
sito multilingue. C'è un problema che potrebbe impedire a Smart Search
di funzionare completamente.

    php joomla.php database:export --help
    php joomla.php database:export --table f4rc2_banners --folder /home/username/tmp/mydb (una tabella)
    php joomla.php database:export --folder /home/username/tmp/mydb (tutte le tabelle)

    php joomla.php database:import --help
    php joomla.php database:import --table /home/username/tmp/mydb/f4rc2_banners (una tabella)
    [ERROR] Il file /home/username/tmp/mydb/f4rc2_banners.xml non esiste.
    php joomla.php database:import --folder /home/username/tmp/mydb (tutte le tabelle in questa cartella)

### Extension

Elenca, Scopri, Installa o Rimuovi estensioni.

    php joomla.php extension:list --help
    php joomla.php extension:list
    php joomla.php extension:list --type component
    php joomla.php extension:list --type file
    php joomla.php extension:list --type language
    php joomla.php extension:list --type library
    php joomla.php extension:list --type module
    php joomla.php extension:list --type package
    php joomla.php extension:list --type plugin
    php joomla.php extension:list --type template

    php joomla.php extension:discover --help
    php joomla.php extension:discover
    php joomla.php extension:discover:list
    php joomla.php extension:discover:install --eid=

    php joomla.php extension:install --help
    php joomla.php extension:install --path=
    php joomla.php extension:install --url=

    php joomla.php extension:remove --help
    php joomla.php extension:remove

### Finder

Elimina e ricostruisce l'indice (i filtri di ricerca sono preservati).

    php joomla.php finder:index --help
    php joomla.php finder:index
    php joomla.php finder:index purge

![Output di finder index purge](../../../en/images/command-line-interface/cli-finder-index-purge.png)

### Scheduler

Elenca, cambia stato o esegui attività pianificate.

    php joomla.php scheduler:list --help
    php joomla.php scheduler:list

    php joomla.php scheduler:state --help
    php joomla.php scheduler:state (richiesta interattiva per id attività)

    php joomla.php scheduler:run --help
    php joomla.php scheduler:run --id ID
    php joomla.php scheduler:run --all

### Session

Esegui la raccolta dei dati non utilizzati della sessione.

    php joomla.php session:gc --help
    php joomla.php session:gc
    php joomla.php session:gc --application administrator

    php joomla.php session:metadata:gc --help
    php joomla.php session:metadata:gc

### Site

Metti il sito offline o online.

    php joomla.php site:down --help
    php joomla.php site:down

    php joomla.php site:up --help
    php joomla.php site:up

### Update

Verifica la presenza di aggiornamenti delle estensioni in sospeso. Rimuove vecchi file che dovrebbero
essere stati eliminati durante un aggiornamento di Joomla

    php joomla.php update:extensions:check --help
    php joomla.php update:extensions:check

    php joomla.php update:joomla:remove-old-files --help
    php joomla.php update:joomla:remove-old-files

![Output di update joomla remove old files](../../../en/images/command-line-interface/cli-update-remove-old-files.png)

### User

Elenca e gestisci gli utenti.

    php joomla.php user:list --help
    php joomla.php user:list

    php joomla.php user:add --help
    php joomla.php user:add --username cinderella --name Cinderella --email cinders@localhost --usergroup Manager (richiesta per password)
    php joomla.php user:add (richiesta per i dati)

![Output di user add con richieste](../../../en/images/command-line-interface/cli-add-user.png)

    php joomla.php user:addtogroup --help
    php joomla.php user:addtogroup (richiesta per i dati)
    php joomla.php user:addtogroup --usernam=cinderella --group=Manager

    php joomla.php user:removefromgroup --help
    php joomla.php user:removefromgroup (richiesta per i dati)
    php joomla.php user:removefromgroup --usernam=cinderella --group=Manager

    php joomla.php user:reset-password --help
    php joomla.php user:reset-password (richiesta per i dati)
    php joomla.php user:reset-password --username=cinderella (richiesta per password)

    php joomla.php user:delete --help
    php joomla.php user:delete (richiesta per nome utente)
    php joomla.php user:delete --username=cinderella (richiesta di conferma - y per confermare)

