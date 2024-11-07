<!-- Filename: How_do_you_password_protect_directories_using_htaccess%3F / Display title: Proteggere con Password le Directory   -->

## Introduzione

Potresti voler proteggere una directory o un intero sito dall'accesso pubblico. Un motivo per farlo è negare l'accesso pubblico a un sito di sviluppo. Solo coloro che conoscono il nome utente e la password avranno accesso. Un altro motivo è la paranoia, ad esempio la protezione della cartella dell'amministratore in modo che gli utenti debbano inserire un nome utente e una password solo per accedere al modulo di login dell'amministratore di Joomla.

Il metodo descritto qui è per server Apache utilizzando un file *.htaccess*.

### Avvertenza da Apache.org

L'autenticazione di base non dovrebbe essere considerata sicura per nessuna definizione particolarmente rigorosa di sicurezza. Anche se la password viene archiviata sul server in formato crittografato, può essere trasmessa dal client al server in testo semplice attraverso la rete. Chiunque ascolti con qualsiasi tipo di packet sniffer sarà in grado di leggere il nome utente e la password mentre vengono trasmessi.

Il nome utente e la password vengono inviati con ogni richiesta, non solo quando l'utente li digita inizialmente. Quindi il packet sniffer non deve necessariamente ascoltare in un momento particolarmente strategico, ma solo per un tempo sufficiente a vedere qualsiasi singola richiesta che attraversa la rete.

Inoltre, il contenuto stesso è anche trasmesso attraverso la rete in chiaro, quindi se il sito web contiene informazioni sensibili, lo stesso packet sniffer avrebbe accesso a tali informazioni, anche se il nome utente e la password non fossero utilizzati per ottenere accesso diretto al sito web.

Non utilizzare l'autenticazione di base per qualcosa che richiede una vera sicurezza. È uno svantaggio per la maggior parte degli utenti, poiché pochissime persone si prenderanno la briga, o avranno il software o l'attrezzatura necessaria, per scoprire le password. Tuttavia, se qualcuno avesse il desiderio di entrare, ci vorrebbe molto poco per riuscirci.

L'autenticazione di base su una connessione SSL, tuttavia, sarà sicura, poiché tutto verrà crittografato, inclusi il nome utente e la password.

## Utilizzo di cPanel

Se utilizzi un servizio di hosting, dovresti utilizzare il suo metodo per la protezione delle directory. Ad esempio, cPanel ha un'opzione chiamata Privacy della directory. Selezionandola, puoi navigare a qualsiasi directory e assegnarle un nome. Avrai quindi l'opportunità di creare un nome utente e una password per la directory nominata. Semplice?

Se ora guardi nella directory che hai protetto, troverai un nuovo file .htaccess contenente qualcosa di simile al seguente, configurato per proteggere la cartella api di Joomla:

```
#----------------------------------------------------------------cp:ppd
# Sezione gestita da cPanel: Directory protette da password    -cp:ppd
# - Non modificare questa sezione del file htaccess!           -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/username/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Fine sezione gestita da cPanel: Directory protette da password -cp:ppd
#----------------------------------------------------------------cp:ppd
```

È importante essere consapevoli che la protezione delle directory di cPanel potrebbe utilizzare lo stesso file .htaccess usato da Joomla per altri scopi.

Se guardi nel file passwd citato, vedrai il Nome utente che hai fornito e la versione criptata della password.

La protezione può essere rimossa ripetendo il processo e deselezionando la casella di controllo `Proteggi con password questa directory`. Questo rimuove la sezione di autenticazione dal file .htaccess. Non rimuove il file .htaccess!

## Regole .htaccess

Puoi eseguire tutti i passaggi richiesti manualmente. Questo strumento potrebbe aiutarti:

<a href="https://www.htaccessredirect.net/" rel="nofollow noreferrer noopener"><em>Generatore .htaccess</em></a>

Crea i file necessari per te. Devi specificare il nome utente, la password e il percorso.

Compila le due sezioni: **File Protetto da Password** e **Generatore htpasswd** e poi seleziona il pulsante `Generate Code`. Otterrai il testo per il file .htaccess e il testo per il file .htpasswd in box separati.
Esempi:
```
//File Protetto da Password
<Files /admin>
AuthName "Prompt"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Tradotto da openai.com*

