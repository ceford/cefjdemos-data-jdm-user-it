<!-- Filename: Multiple_Domains_and_Web_Sites_in_a_single_Joomla!_installation / Display title: Più domini e siti web in un'unica installazione di Joomla! -->

**Nota:** Questo articolo è stato aggiornato l'ultima volta nel 2012!

Anche se è buona pratica assegnare a ogni sito web il proprio dominio,
installazione di Joomla! e database, ci possono essere condizioni particolari
in cui è giustificata una soluzione multi-sito sotto un'unica installazione di Joomla!

## Un'applicazione di esempio

Una piccola impresa, 'Johnson Candies', ha due marchi separati ma correlati: *Red Candy* e *Yellow Candy*. Richiedono un unico sito Web basato su Joomla! dove entrambi i tipi di caramelle siano visibili, ciascuno con la propria home page sul sito Joomla! che corrisponde ai domini `www.redjohnsoncandy.com` e `www.yellowjohnsoncandy.com`.

Inoltre, **ogni marchio e sito richiede il proprio design**: un template giallo per uno; un template rosso per l'altro.

## Vantaggi

Includendo entrambi i marchi in un'unica installazione web di Joomla!, Johnson Candies è in grado di risparmiare tempo di modifica (un solo login), condividere articoli e dati tra entrambi i marchi (o siti) e utilizzare una sola funzionalità, come ad esempio un modulo Contattaci, per entrambi i marchi.

## Procedura di Implementazione

### Prepara i Tuoi Domini

Utilizza un unico dominio per il tuo account di hosting, come di consueto. Crea i domini aggiuntivi richiesti nel pannello di controllo del tuo account di hosting. Ai fini di questo tutorial, utilizzeremo `www.redjohnsoncandy.com` oltre al dominio base `www.yellowjohnsoncandy.com`.

### Installa e Configura Joomla!

Installa e configura Joomla! normalmente. Successivamente, sviluppa articoli, menu e moduli per ciascun sito.

### Crea i Modelli

Successivamente, sviluppa e installa i modelli necessari - uno per ciascun sito che desideri avere. Nell'esempio sopra, creeresti un modello per *red candy* chiamato *Modello Rosso* e un modello per *yellow candy* chiamato *Modello Giallo*. Una volta installati i modelli, assegnali agli elementi di menu pertinenti, utilizzando il gestore di modelli di Joomla! nell'area Amministratore di Joomla!.

### Aggiungi un Reindirizzamento

#### Opzione #1: Crea un Reindirizzamento .htaccess (Apache)

**Nota:** *Abilita prima gli URL SEF in Joomla!*

Un'opzione è usare .htaccess (Apache) per reindirizzare le richieste a un dato dominio a una pagina specifica in Joomla!.

Il nostro obiettivo è reindirizzare qualsiasi richiesta al dominio Red Candy a una pagina specifica del sito Joomla!. In questo esempio, reindirizziamo qualsiasi richiesta a `www.redjohnsoncandy.com` a una pagina categoria-blog. Avresti precedentemente assegnato il modello 'red candy' a questo elemento di menu, per creare l'illusione di un sito separato.
```
#La seguente regola funziona, ma cambia il nome del dominio visualizzato.
RewriteCond %{HTTP_HOST} ^(www\.)?redjohnsoncandy\.com$
RewriteRule (.*) http://www.yellowjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12 [R=301,L]
```
Bene, questo funziona - ma puoi vedere subito lo svantaggio. Anche se l'utente sta visualizzando con successo il sito Red Candy, vedrà comunque il nome del dominio Yellow Candy. Sfortunatamente, se stai utilizzando sia .htaccess che domain-parking (tecnicamente un reindirizzamento) - questo è necessario per evitare di creare un LOOP.

#### Opzione #2: Crea un Reindirizzamento di Intestazione PHP

Questa soluzione ha il vantaggio di mantenere l'illusione di domini/siti web separati evidente per il visitatore. Invece di usare .htaccess (Apache) per il nostro reindirizzamento, utilizziamo uno dei modelli del sito.

In questo esempio, il dominio base è `www.redjohnsoncandy.com`. Hai creato un modello per quell'area chiamato *Modello Rosso*. Il trucco è aprire il file index.php di 'Modello Rosso' e aggiungere le seguenti **come primissime linee** del file index.php principale dell'installazione.

```php
<?php
$domain = $_SERVER["HTTP_HOST"];
$uri = $_SERVER["REQUEST_URI"];
$url = $domain . $uri;

if (($url == "redjohnsoncandy.com/") ||
   ($url == "www.redjohnsoncandy.com/")) {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.redjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12");
}
?>
```

Ecco il vantaggio: il visitatore verrà ora reindirizzato alla pagina *Sito Rosso* appropriata, che ha assegnato il *Modello Rosso* **solo** nel caso in cui siano arrivati al dominio 'sito rosso'. Altrimenti, la regola condizionale PHP viene ignorata e il Sito Giallo viene caricato.

È importante ricordare di richiedere anche l'URI (URL che segue il puro dominio) in modo da poter fare reindirizzamenti nello stesso dominio. Quando l'URI è invisibile nell'url la variabile diventa un segno "/". Ecco perché devi confrontare il tuo url puro con un segno "/" alla fine. In questo modo sarai in grado di fare reindirizzamenti 301 all'interno dello stesso dominio. Altrimenti creerai un loop infinito nel processo di reindirizzamento.

#### Opzione #3: Crea un Reindirizzamento di Intestazione PHP per più domini con reindirizzamenti specifici per modelli personalizzati

Soluzione per uno spazio web singolo, con diversi domini, un'installazione Joomla e a seconda del dominio di atterraggio dell'utente, reindirizza a una pagina predefinita diversa. Incolla il seguente codice PHP **come primissima cosa** nel file index.php principale dell'installazione. Per assegnare un altro dominio, copia/incolla la funzione "if" e modificala con i valori dell'altro dominio nello stesso modo. Inoltre, per configurare le visualizzazioni dei modelli, dovrai assegnare alias di link/articolo modulo diversi e configurare le visualizzazioni dei modelli all'interno del gestore di modelli di Joomla!. L'impostazione dell'alias è necessaria quando si utilizzano le impostazioni SEF.
```php
<?php
$domain = $_SERVER["SERVER_NAME"];
$requri = $_SERVER['REQUEST_URI'];
if (($domain == "www.example.de" && $requri == "/" ||
   $domain == "example.de"))  {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.example.de/index.php?option=com_content&view=article&id=6");
}
?>
```

