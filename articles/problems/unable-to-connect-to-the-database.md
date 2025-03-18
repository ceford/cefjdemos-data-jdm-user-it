<!-- Filename: Unable_to_connect_to_the_database / Display title: Connessione al Database  -->

## Errore di Connessione

Se ricevi un errore "**Impossibile connettersi al database**" durante l'installazione, verifica di aver inserito correttamente i dettagli del database MySQL/MariaDB. Lo script di **installazione** non ti consentirà di continuare a meno che i dettagli non siano corretti.

Nota che non è previsto creare un utente e una password del database durante l'installazione. Devono essere creati prima.

Se il problema si verifica dopo aver spostato il tuo sito su un altro host, controlla i seguenti elementi del tuo file *configuration.php*. Le impostazioni normali del database sono le seguenti:

    public $dbtype = 'mysqli';
    public $host = 'localhost';
    public $user = 'yourdbuser';
    public $password = 'yourdbpassword';
    public $db = 'yourdbname';
    public $dbprefix = 't6q6i_';

Se il problema si verifica in un sito che funzionava correttamente, ci sono diversi motivi possibili, a volte temporanei e a volte accidentali.

## I guasti più comuni

1. A volte vedrai questo messaggio se MySQL/MariaDB ha smesso di funzionare sul tuo server. L'amministratore del server potrebbe temporaneamente arrestare MySQL/MariaDB per eseguire la manutenzione. In tali circostanze, il tuo sito probabilmente tornerà a breve.
2. Il tuo utente del database è stato eliminato. In tal caso, dovrai ricreare il tuo utente del database con lo stesso nome utente e password che esistevano quando hai installato Joomla per la prima volta. Utilizza il pannello di controllo del tuo dominio per gestire questo o contatta l'amministratore del tuo server.
3. Il nome utente o la password del tuo database sono cambiati.

*Tradotto da openai.com*
