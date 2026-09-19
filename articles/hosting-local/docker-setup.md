<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Configurazione di Docker",
    "description": " ",
    "author": ""
}
-->

## Configurazione di un ambiente Joomla locale utilizzando Docker

Per eseguire Joomla sul proprio computer sono necessarie quattro cose: 
- scaricare e configurare un server web **Apache** o **nginx**, 
- un servizio di database come **MySQL o** **MariaDB**, 
- e naturalmente **PHP** 
- e **Joomla.** 

Per fare in modo che tutti questi componenti diversi comunichino effettivamente tra loro, la maggior parte di noi si affida a software inclusi come **XAMPP**, **Laragon** o **FlyEnv**.

Tuttavia, le configurazioni tradizionali possono facilmente causare conflitti tra le porte o server di database che, misteriosamente, si rifiutano di avviarsi. Quando un server locale si arresta in modo anomalo, potresti ritrovarti a scaricare e reinstallare manualmente interi siti Joomla più e più volte solo per testare una singola PR,
rischiando di perdere il lavoro mentre risolvi un bug. Questo consuma tempo prezioso e le soluzioni sono solitamente solo rimedi temporanei.

**Il passaggio a Docker ([Scopri di più su Docker](https://docs.docker.com/get-started/))** 
Con Docker, puoi
salta completamente la configurazione manuale. Invece di installare
direttamente i server web sul computer, devi solo scrivere un singolo file
di "ricetta". Docker scarica, isola e collega automaticamente tutto in
background. Se qualcosa si rompe, non devi reinstallare l'intera
configurazione; ti basta riavviare il container.

In questa guida imparerai il modo più semplice per configurare un ambiente
Joomla locale utilizzando Docker, così potrai dedicare meno tempo alla
risoluzione dei problemi dei server e più tempo a contribuire.

### Prerequisiti

Prima di iniziare devi installare una sola cosa: **Docker Desktop**.

- Scaricalo da [**docker.com**](https://www.docker.com/) ed esegui il
  programma di installazione
- Su Windows, lascia selezionata l'opzione "Usa WSL 2 invece di Hyper-V" -
  rende tutto più veloce
- Apri Docker Desktop e attendi finché nell'angolo inferiore sinistro non
  viene mostrato lo stato verde **Motore in esecuzione**.

![Docker Desktop](../../../en/images/hosting-local/docker-setup/01-docker-setup-desktop.png)

Tutto qui.

### Il file docker-compose.yml

Quando hai bisogno che più servizi comunichino tra loro, come un server
web (Apache/Nginx), PHP e un database (MySQL/MariaDB), utilizzi un file
speciale di orchestrazione chiamato `docker-compose.yml`. Questo file funge
da modello per il tuo progetto, definendo tutti i servizi necessari e il
modo in cui collaborano. (L'immagine ufficiale di Joomla per Docker è in
realtà costruita sopra un'immagine PHP e Apache. Ciò significa che,
utilizzando questa unica immagine Joomla, ottieni PHP, Apache e Joomla, tutti
inclusi nello stesso pacchetto).

Per prima cosa, crea una nuova cartella sul tuo computer per il progetto
(ad esempio, sul Desktop, crea una cartella chiamata `joomla-docker`).

All'interno di quella cartella, crea un nuovo file di testo e chiamalo
esattamente così:

    docker-compose.yml

Apri quel file in un qualsiasi editor di testo (come VS Code o Blocco note),
incolla esattamente il codice seguente e salvalo:

```
    services:
      joomla:
        image: joomla:latest
        ports:
          - "8080:80"
        environment:
          - JOOMLA_DB_HOST=db
          - JOOMLA_DB_USER=joomla
          - JOOMLA_DB_PASSWORD=joomlapass
          - JOOMLA_DB_NAME=joomladb
        depends_on:
          - db
      db:
        image: mariadb:10.11
        environment:
          - MYSQL_ROOT_PASSWORD=rootpass
          - MYSQL_DATABASE=joomladb
          - MYSQL_USER=joomla
          - MYSQL_PASSWORD=joomlapass
        volumes:
          - db_data:/var/lib/mysql
    volumes:
      db_data:
```

### Avvio dell’ambiente

Apri il terminale (o PowerShell su Windows), vai alla cartella `joomla-docker`
ed esegui:

```
    docker compose up -d
```

La prima volta che esegui questo comando, Docker scaricherà le immagini di Joomla e MariaDB, operazione che potrebbe richiedere uno o due minuti a seconda della velocità della tua connessione Internet. Dopodiché, ogni avvio successivo sarà quasi istantaneo, come puoi vedere di seguito.

![Output del terminale dopo l'avvio di Docker](../../../en/images/hosting-local/docker-setup/02-docker-setup-terminal-transcript.png)

### L'installer di Joomla

Apri il browser e vai all'indirizzo `http://localhost:8080`. Dovresti vedere la
schermata di installazione di Joomla.

![Configurazione dell'installer di Joomla: nome del sito](../../../en/images/hosting-local/docker-setup/03-docker-setup-joomla-installer-sitename.png)

Inserisci il nome del sito e i dati dell'amministratore nella prima schermata.

![Dati di accesso dell'installer di Joomla](../../../en/images/hosting-local/docker-setup/04-docker-setup-joomla-installer-login-data.png)

Quando raggiungi la schermata **Configurazione del database**, è qui che la maggior parte
delle persone si blocca:

**Non inserire `localhost` come nome host.**

Poiché il database viene eseguito nel proprio container, Joomla ha bisogno del nome del
servizio del container, non di localhost. Usa questi valori esatti:

- **Tipo di database:** MySQLi
- **Nome host:** `db`
- **Nome utente:** `joomla`
- **Password:** `joomlapass`
- **Nome del database:** `joomladb`

![Configurazione del database dell'installer di Joomla](../../../en/images/hosting-local/docker-setup/05-docker-setup-joomla-installer-database-config.png)

Fai clic per procedere, completa l'installazione e avrai finito.

Quando hai terminato di lavorare per la giornata, esegui `docker compose stop` per
metti in pausa i container e libera memoria. Il tuo sito sarà esattamente dove
lo avevi lasciato la prossima volta.

------------------------------------------------------------------------

### Problemi comuni

- **La pagina all'indirizzo localhost:8080 non viene caricata subito dopo l'avvio:** Il
  container del database impiega alcuni secondi per completare l'inizializzazione. Attendi 30
  secondi e aggiorna la pagina.
- **La porta 8080 è già in uso:** Modifica `"8080:80"` in `"8081:80"` nel
  file compose e accedi invece all'indirizzo `localhost:8081`.
- **I container sono stati avviati, ma Joomla mostra un errore del database:** Verifica nuovamente
  che il nome host nell'installer sia `db` e non `localhost`.

### Consiglio da professionisti: accedere ai file di Joomla per lo sviluppo

Al momento, il tuo sito Joomla è in esecuzione, ma i file PHP effettivi
sono nascosti all'interno del container Docker. Se vuoi contribuire a Joomla,
testare PR o scrivere i tuoi plugin, devi avere quei file sul tuo
computer, così da poterli aprire in VS Code o nel tuo editor preferito.

Per sincronizzare i file dal container al disco rigido locale, devi solo
aggiungere due righe (`volumes: `) e (`- ./site_joomla:/var/www/html`)
alla sezione `joomla` del tuo file `docker-compose.yml`, come mostrato di seguito:

```yml
services:
  joomla:
    image: joomla:latest
    ports:
      - "8080:80"
    volumes:
      - ./site_joomla:/var/www/html
    # ... (rest of your settings)
```

**Cosa fa:** 

La prossima volta che eseguirai `docker compose up -d`, Docker creerà automaticamente
una cartella chiamata `site_joomla` proprio accanto al file compose. Al suo interno
copierà l'intero core di Joomla (inclusi il pannello di amministrazione,
i componenti e i template).

![Esplora risorse dell'IDE con l'installazione di Joomla in Docker](../../../en/images/hosting-local/docker-setup/06-docker-setup-ide-explorer.png)

Qualsiasi modifica al codice apportata in quella cartella sul computer verrà aggiornata immediatamente all'interno del container in esecuzione! Ora l'ambiente è completamente configurato per lo sviluppo locale.

### Suggerimento bonus 1: Testare versioni specifiche di Joomla e PHP

Durante il test delle PR, i maintainer ti chiederanno spesso di eseguire i
test con versioni specifiche di PHP. Con XAMPP, eseguire il downgrade o
l'upgrade di PHP è un incubo. Con Docker, bastano due secondi.

Invece di usare `image: `**`joomla:latest`** nel tuo
**`docker-compose.yml`**, puoi specificare versioni esatte utilizzando i tag. Ad
esempio, se devi testare **Joomla 5.2** su **PHP 8.3**, ti basta modificare
quella riga in: **`image: joomla:5.2-php8.3-apache`**

Esegui nuovamente **`docker compose up -d`** e Docker sostituirà
istantaneamente l'ambiente del tuo server. Puoi trovare tutti i tag delle
versioni disponibili nella <a href="https://hub.docker.com/_/joomla" class="ng-star-inserted"
target="_blank" rel="noopener" data-hveid="0"
data-ved="0CAAQ_4QMahgKEwjl8vi347CTAxUAAAAAHQAAAAAQkgI">pagina ufficiale di Joomla
su Docker Hub</a>.

### Consiglio bonus 2: aggiungere phpMyAdmin

Se provieni da **XAMPP**, potresti sentire la mancanza di un'interfaccia
visiva per visualizzare il tuo database. Puoi aggiungere facilmente
**phpMyAdmin** alla tua configurazione aggiungendo un nuovo **blocco
di servizio** in fondo al file **`docker-compose.yml`**:

```yml
    phpmyadmin:
        image: phpmyadmin/phpmyadmin:latest
        ports:
          - "8081:80"
        environment:
          - PMA_HOST=db
        depends_on:
          - db
```

Riavvia i container e ora puoi accedere a phpMyAdmin visitando
**http://localhost:8081** nel browser. Accedi semplicemente usando
**`joomla`** come nome utente e **`joomlapass`** come password.

*Tradotto da openai.com*