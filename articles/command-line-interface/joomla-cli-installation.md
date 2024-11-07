<!-- Filename: J4.x:Joomla_CLI_Installation / Display title: Installazione CLI di Joomla  -->

## Introduzione

Il CMS Joomla viene solitamente installato tramite un'interfaccia del browser web. Tuttavia, gli utenti esperti potrebbero desiderare di installare Joomla utilizzando comandi in un'interfaccia terminale. Questo consente un rapido deployment di più istanze di Joomla.  

## Requisiti di Sistema

Joomla richiede PHP, un database e un server web. Per le ultime informazioni sul software supportato e sulle versioni minime e consigliate, si prega di visitare la pagina dei <a href="https://manual.joomla.org/docs/next/get-started/technical-requirements/" rel="noreferrer noopener">Requisiti Tecnici</a>.

L'installazione può essere eseguita in due modi differenti:

1. Installazione manuale
2. Installazione automatica tramite script  

## Installazione manuale

L'installazione manuale offre un buon controllo durante il processo di installazione. Ogni passo è visibile nel terminale e può essere interrotto con `Ctrl+C` in caso di inserimento errato.

### Passaggi da completare

1. Carica il pacchetto di installazione in formato zip o tar sul server web.
2. Decomprimi il file zip o tar.
3. Rinomina la cartella decompressa e spostala in un posto appropriato nella root del documento del server web.
4. Accedi alla cartella contenente il codice di Joomla ed esegui il seguente comando:<br>
   `php installation/joomla.php install`
5. Ti verranno richiesti i parametri necessari per l'installazione, come nell'esempio di trascrizione seguente:
```bash
php installation/joomla.php install

Installazione di Joomla
=======================

Verifica dei requisiti di sistema...OK
Raccolta delle configurazioni...

 Inserisci il nome del tuo sito Joomla:
 > J51
 Inserisci il nome reale del Super User:
 > John Doe
 Imposta il nome utente per l'account Super User:
 > johndoe
 Imposta la password per l'account Super User:
 >
 Inserisci l'indirizzo email del Super User del sito web:
 > johndoe@example.com
 Tipo di database. Supportati: mysql, mysqli, pgsql [mysqli]:
 >
 Host del database [localhost]:
 >
 Nome utente del database:
 > j4
 Password del database:
 >
 Nome del database [joomla_db]:
 > j51
 Prefisso per le tabelle del database [u5dke_]:
 >
 Crittografia per la connessione al database. Valori: 0=Nessuna, 1=A unidirezionale, 2=A bidirezionale [0]:
 >
 Percorso relativo o assoluto alla cartella pubblica []:
 >
OK
Validazione della connessione al DB...OK
Creazione e popolamento del database...OK
Scrittura di configuration.php e configurazione aggiuntiva...OK
Eliminazione della cartella /installation...OK
 [OK] Joomla è stato installato
```

Una volta che lo script è stato completato con successo, il nuovo sito web potrà essere accesso tramite il tuo browser web.

### Note

* Presta molta attenzione ai tuoi input. Non è possibile tornare indietro nello script. Se l'input è sbagliato, lo script deve essere interrotto.
* Il nome del tuo sito Joomla compare nella barra del titolo dell'Amministratore quindi tienilo breve e distintivo. Può essere cambiato in seguito.
* Il nome reale del tuo Super User può essere modificato successivamente.
* Il nome utente per l'account Super User dovrebbe evitare di essere simile a *admin*. È potenzialmente insicuro poiché può essere indovinato facilmente da un hacker.
* La password dell'utente deve essere di 12 caratteri.
* Il tipo di database predefinito è *mysqli*. I tipi di database supportati sono i database MySQL (mysql) e PostgreSQL (pgsql) e tipi compatibili come MariaDB.
* L'host del database è quasi sempre `localhost`. Un indirizzo IP o un nome host deve essere inserito qui solo se il server di database responsabile è installato su un altro host. Tuttavia, l'utente del terminale deve avere permessi di scrittura sull'host selezionato. Riceverai queste informazioni dal tuo provider internet (ISP).
* Il nome utente del database è solitamente diverso dal nome del Super User.
* La password del database per il database Joomla è quasi sempre diversa dalla password del Super User.
* Il nome del database di default è `joomla_db`, ma vengono spesso usati altri nomi.
* Il prefisso per le tabelle del database è impostato su una selezione casuale di cinque caratteri. Il valore è utilizzato per separare le tabelle di Joomla da altre tabelle contenute nel database se viene utilizzato anche da altre applicazioni.
* L'impostazione di crittografia per la connessione al database è difficilmente utilizzata. A meno che non ricevi diverse indicazioni dal tuo ISP, lascia questo valore al default [0].

## Installazione automatica guidata da script

L'installazione di Joomla è controllata da un file *joomla.php* situato nella sottocartella *installation* dopo aver scompattato il pacchetto di Joomla. Qualsiasi linguaggio di programmazione che consente di chiamare ed eseguire file PHP ti permette di creare uno script che automatizza le preparazioni necessarie e l'installazione effettiva utilizzando variabili personalizzate. È possibile ottenere un elenco di parametri con il seguente comando:
```bash
php installation/joomla.php help install
```
Ecco un esempio di script shell chiamato jinstall.sh posizionato nella cartella principale di Joomla creato per una semplice installazione di Joomla:
```
#!/bin/bash

php installation/joomla.php install \
--site-name=NOME-SITO \
--admin-user=UTENTE-ADMIN \
--admin-username=NOME-UTENTE-ADMIN \
--admin-password=PASSWORD-ADMIN \
--admin-email=johndoe@example.com \
--db-type=mysqli \
--db-host=localhost \
--db-user=j51 \
--db-pass=Garbage1n0ut \
--db-name=j51 \
--db-prefix=xyz12_ \
--db-encryption=0 \
--public-folder=j51
```
Con i permessi impostati a 700 è un gioco da ragazzi chiamare lo script dalla riga di comando con `./jinstall.sh` e Joomla è installato letteralmente in un lampo. Lo script potrebbe essere stato modificato per cambiare i valori segnaposto o potrebbero essere cambiati successivamente dopo il login dell'Amministratore.

Se utilizzi questo approccio, ricorda di eliminare il tuo script jinstall.sh o spostarlo fuori dalla tua struttura web per utilizzarlo altrove in seguito. La cartella di installazione viene rimossa al termine del processo di installazione. Quindi eseguire di nuovo lo script jinstall.sh non funzionerà.

