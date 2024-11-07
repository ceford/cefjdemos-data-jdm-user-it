<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Recupero Password Amministratore  -->

## Introduzione

Normalmente un Super Utente può aggiungere, modificare e eliminare utenti e password dalla lista Utenti. In alcune situazioni questo potrebbe non essere possibile. Ad esempio, la persona che conosceva la password di un Super Utente non è più disponibile. Oppure il Super Utente potrebbe aver dimenticato la password utilizzata.

In tali casi sono disponibili due metodi per consentire a un Amministratore del sito di effettuare l'accesso come Super Utente.  

## Metodo 1: Modifica del file configuration.php

Se hai accesso al file `configuration.php` dell'installazione di Joomla sul tuo server, puoi reimpostare una password di Super User o creare un nuovo Super User se puoi accedere come Manager o Amministratore.

Devi aprire il file `configuration.php` in un editor di testo. Per prima cosa, cambia i permessi del file a 644. I tuoi strumenti di gestione del sito, come cPanel o Plesk (ce ne sono altri), solitamente ti consentono di farlo online. In caso contrario, potresti dover utilizzare FTP per scaricare il file, modificarlo localmente e caricarlo di nuovo.

Aggiungi questa riga alla fine del file ma prima della parentesi graffa di chiusura:
```
    public $root_user='nomeutente';
```
dove **nomeutente** è un nome utente con accesso al gruppo *Manager* o *Administrator* di cui conosci la password. Un nome utente che appartiene ai gruppi *Autore*, *Editore* o *Editore Capo* non funzionerà perché quei gruppi non hanno accesso al backend.

Questo utente sarà ora un Super User temporaneo.

Accedi al back end e cambia la password del Super User di cui non conosci la password o crea un nuovo account Super User. Se crei un nuovo utente, potresti voler bloccare o eliminare l'utente vecchio a seconda delle tue circostanze.

Al termine, assicurati di utilizzare il link *Seleziona qui per provare a farlo automaticamente* che appare nella casella di avviso per rimuovere la riga che è stata aggiunta al file configuration.php. Se l'uso del link non ha avuto successo, torna indietro ed elimina la riga aggiunta dal tuo file configuration.php utilizzando un editor di testo.

Se non hai utenti che conoscono le loro password, potresti dover apportare una modifica nel tuo database.

## Metodo 2: Modifica del Database

Se i metodi sopra non hanno funzionato, hai altre due opzioni, entrambe
richiedono di lavorare direttamente con il database MySQL.

### Cambiare una Password nel Database

L'opzione più semplice è cambiare la password del Super Utente nel database con
un valore noto. Questo richiede l'accesso al database MySQL tramite phpMyAdmin
o un altro client. Queste istruzioni mostrano come cambiare una password nella parola **secret**.

Questo metodo funzionerà solo se l'utente selezionato appartiene ai gruppi *Manager* o
*Administrator*.

**Assicurati di cambiare la password del Super Utente una volta che hai riottenuto l'accesso!**

1.  Apri phpMyAdmin e seleziona il database per il sito Joomla! Questo
    mostrerà le tabelle del database sul lato sinistro dello schermo.
2.  Trova e seleziona la tabella *#__users* dove *#_* è il prefisso della tabella per
    il tuo sito.
3.  Nella vista *Sfoglia*, trova l'utente di cui vuoi cambiare la password e
    seleziona l'icona Modifica per questa riga.
    - se l'elenco è lungo, seleziona il pulsante SQL in alto e usa questa query:<br>
    `SELECT * FROM `xxxxx_users` WHERE `username` = 'username'`<br>
    dove utilizzi il prefisso del tuo database per sostituire `xxxxx` e il nome utente
    che devi trovare al posto di `username`.
4.  Nel modulo di modifica cambia la password in<br>
    `d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199`<br>
    e seleziona il pulsante *Esegui* in fondo al modulo. phpMyAdmin dovrebbe
    mostrare il messaggio *Righe interessate: 1*. A questo punto, la password dovrebbe
    essere **secret**.
5.  Accedi con questo utente e password e cambia la password di questo
    utente con un valore sicuro. Controlla tutti gli utenti per assicurarti che siano
    legittimi. Se sei stato hackerato, potresti voler cambiare tutte le
    password sul sito.

### Aggiungere un nuovo Super Utente

Se cambiare la password non funziona o non sei sicuro di quale utente sia un
membro del gruppo Super User, puoi usare questo metodo per creare un nuovo
Super Utente.
1.  Apri phpMyAdmin e seleziona il database per il sito Joomla!.
2.  Seleziona il pulsante *SQL* nella barra degli strumenti per eseguire una query SQL sul
    database selezionato. Questo mostrerà un campo chiamato "Esegui query SQL
    sul database xxxxx".
3.  Elimina qualsiasi testo in questo campo e copia ed incolla la seguente query.
    Ricorda di sostituire `xxxxx` con il tuo prefisso del database.
    ```
    INSERT INTO `xxxxx_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `xxxxx_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');
    ```
    Seleziona il pulsante *Esegui* per eseguire la query e aggiungere il nuovo Super Utente alla
    tabella.

A questo punto, dovresti essere in grado di accedere al back end di Joomla!
con il nome utente *admin2* e la password *secret*.

Dopo l'accesso, vai all'elenco utenti e cambia la password con un nuovo valore sicuro e aggiungi un indirizzo email valido all'account.

Se c'è la possibilità che tu sia stato *hackerato*, assicurati di controllare che tutti gli utenti
siano legittimi, specialmente quelli che fanno parte del gruppo Super Utente.

## Password Temporanei Alternativi

**Avvertimento:** I valori delle password mostrati in questa pagina sono di dominio pubblico e
sono solo per recupero. Per evitare di essere violati, assicurati di cambiare una password temporanea con un valore sicuro dopo il login.

```python
password = "questa è la password hashata con MD5 e salata"
------------------------------------------------------
admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm
```

*Tradotto da openai.com*

