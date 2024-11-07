<!-- Filename: J4.x:CLI_Database_Exporter_Importer / Display title: Esportazione e Importazione del Database CLI -->

## Introduzione

Prima di aggiornare Joomla! o installare un'estensione di terze parti, è fortemente raccomandato eseguire un backup del tuo sito. L'interfaccia a riga di comando di Joomla! (CLI) fornisce comandi per esportare (fare il backup) e importare (ripristinare) il tuo database di Joomla!. Si noti che non esegue il backup del tuo filesystem, che dovrebbe essere fatto separatamente.

## Requisiti

Per utilizzare questi comandi, è necessario avere accesso al terminale dell'host su cui è installato il sito. Questo potrebbe rappresentare un problema su hosting condiviso! È inoltre necessaria una conoscenza di base dei comandi shell di Linux, come ls e cd. Se tutto questo è poco familiare, dovresti probabilmente utilizzare Akeeba Backup, l'estensione di backup e ripristino più popolare e gratuita per uso base.

## Posizione di archiviazione temporanea del backup

Presta attenzione quando scegli una posizione di archiviazione per un backup. Dovrebbe trovarsi all'interno del tuo spazio file personale ma al di fuori dell'albero web. L'obiettivo è creare un file di backup che puoi scaricare sul tuo computer locale o in un altro luogo sicuro, dopodiché puoi eliminare il file di backup per risparmiare spazio. Inoltre, assicurati di non utilizzare la cartella di sistema /tmp che può essere letta da qualsiasi utente. La posizione migliore è la tua cartella tmp personale. Struttura ad albero delle cartelle:
```
|-/home/nomeutente/tmp - la tua cartella tmp personale
|-/home/nomeutente/public_html - la tua cartella radice di Joomla
```

## Istruzioni

Accedi al tuo host e vai nella cartella principale del tuo sito.
```
cd /home/username/public_html
```

- Elenca tutti i comandi CLI disponibili:
```sh
  php cli/joomla.php list
```
- Esporta il database nella cartella tmp dell'account:
```sh
  php cli/joomla.php database:export --folder /home/username/tmp/mydbname
```
- Importa il database dalla cartella:
```sh
php cli/joomla.php database:import --folder /home/username/tmp/mydbname
```

Puoi anche:

- Esportare il database come file .zip:
```sh
php cli/joomla.php database:export --zip --folder /home/username/tmp/mydbname
```
- Esportare una tabella:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Esportare una tabella come file .zip:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --zip --folder /home/username/tmp/mydbname
```
- Importare una tabella:
```sh
php cli/joomla.php database:import --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Se hai bisogno di aiuto:
```sh
php cli/joomla.php database:export --help
php cli/joomla.php database:import --help
```

## Backup

Per eseguire un backup completo di cartelle, file e del database, eseguire questi comandi:

1. Archivia la tua directory radice di Joomla:
```sh
tar --exclude='/home/username/public_html/tmp' -zcvf /home/username/tmp/joomla_bak.tgz /home/username/public_html > /home/username/tmp/joomla_bak.log
```
2. Esporta tutto il database di Joomla dalla cartella radice di Joomla:
```sh
php cli/joomla.php database:export --folder /home/username/tmp/db_bak
```

## Ripristino

Per ripristinarlo, assicurati innanzitutto che il database e l'utente del database esistano. Poi esegui questi comandi:

1.  Estrai l'archivio:
```sh
tar -xvf /home/username/tmp/joomla_bak.tgz --directory /home/username/public_html
```
2. Assicurati di essere nella directory principale del tuo sito:
```sh
cd /home/username/public_html
```
3.  Importa il database di Joomla:
```sh
php cli/joomla.php database:import --folder /home/username/tmp/db_bak
```

## Note

Nelle opzioni del comando tar -zcvf e -xvf, la v sta per verbose - un elenco di
file processati scorre rapidamente sullo schermo del terminale. Ommetti la v per
non vedere l'elenco.
*Tradotto da openai.com*

