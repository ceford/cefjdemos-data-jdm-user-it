<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Installazione di Raspberry Pi -->

## Prefazione

**Nota: Questo documento non è ancora completo e completamente testato.**

Il <a href="https://www.raspberrypi.org/" rel="nofollow noreferrer noopener">Raspberry Pi</a> è un piccolo computer a scheda singola che è stato originariamente sviluppato per promuovere l'insegnamento dell'informatica di base nelle scuole e nei paesi in via di sviluppo. Grazie alla sua versatilità, è diventato molto popolare ed è utilizzato come lettore multimediale, piccolo server autonomo, ecc. Puoi usarlo come server web e installare Joomla! su di esso. Questa pagina ti mostra come far funzionare il tuo sito web Joomla! su Raspberry Pi.

## Hardware

- **Raspberry Pi versione 3 Modello B** - Esistono vari modelli di Raspberry Pi. Puoi utilizzare la maggior parte dei modelli che hanno una porta Ethernet (i tipi Model B). Tuttavia, per prestazioni migliori useremo l'ultima versione con più memoria RAM.
- **Scheda micro SD** - Per il sistema operativo + server web + Joomla. (Il modello RPi versione 3 B utilizza micro SD, altre versioni potrebbero utilizzare schede SD normali)
- **Adattatore 5 Volt (1 Amp)** - per alimentare il Raspberry Pi è necessario convertire la corrente domestica (230V o 110V) in 5 Volt. Il Raspberry Pi necessita di circa 1 Ampere, e forse di più se ci colleghi dispositivi USB.
- **Cavo Ethernet standard** - per collegare il RPi alla tua rete locale / router / internet.

## Installazione del Sistema Operativo

Il sistema operativo Raspbian è una versione di Debian Linux appositamente compilata per il Raspberry Pi. Sono disponibili due versioni di <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a>: **Raspbian Jessie con Pixel Lite** (versione con desktop PIXEL basato su Debian Jessie) e **Raspbian Jessie Lite** (versione minima basata su Debian Jessie). Poiché utilizziamo il Raspberry Pi come server web per Joomla, non avremo bisogno dell'interfaccia grafica.

**Scarica** <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> e decomprimi il file scaricato, ad esempio **2016-09-23-raspbian-jessie-lite.zip** (306 MB) in **2016-09-23-raspbian-jessie-lite.img** (1.4 GB).

Ora dobbiamo copiare il file .img sulla scheda (micro) SD. Puoi utilizzare un tool con interfaccia grafica come <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (per Windows, Mac OS X e Linux) o farlo tramite linea di comando.

**Fai attenzione** quando scrivi l'immagine del disco *img su un altro disco. Se specifichi il disco di destinazione sbagliato, sovrascriverai quel disco con il file *img rendendolo inutilizzabile, con conseguente perdita di dati.

### Windows

In un terminale (CMD) controlla quale dispositivo corrisponde alla scheda SD e fai qualcosa del genere:

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img od=[dispositivo della tua scheda SD]
```

Vedi anche <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Installazione delle Immagini del Sistema Operativo usando Windows</a>

### Apple OSX

Controlla quale dispositivo viene utilizzato per la tua scheda SD. Nel nostro caso è *disk1s1* e nel Terminale eseguiremo:

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Vedi anche: <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Installazione delle Immagini del Sistema Operativo su MacOS</a>

### Linux

Colleghiamo un lettore di schede SD con la scheda (micro) SD a un computer. Con *dmesg* possiamo trovare il nome del dispositivo della scheda SD. Nel nostro caso, dmesg mostra qualcosa come `[xxxxxx.xxxxxxx] sdd: sdd1 sdd2`, il che significa che abbiamo una scheda SD con 2 partizioni. Non scrivere l'immagine di Raspbian su una partizione ma sull'intero disco **sdd**.

Useremo *dd* ("Disk Dump") per scrivere un File di Input (*if*) su un File di Output (*of*) usando una specifica Dimensione del Blocco (*bs*).

**Fai attenzione**: *dd* scriverà su un dispositivo senza alcun avviso. Controlla due volte di scrivere sul dispositivo corretto! Se scrivi sul disco sbagliato, ricorderai sempre il comando *dd* come "Distruttore di Disco".

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Vedi anche <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Installazione delle Immagini del Sistema Operativo su Linux</a>

**ATTENZIONE per la versione Raspbian Stretch**: per avere un server SSH funzionante dall'avvio, è necessario creare un file vuoto *ssh* sulla partizione di root.  

## Collegamento del Raspberry Pi alla LAN

Quando avremo installato il sistema operativo Raspbian sulla scheda SD, dovremo:

- Inserire la scheda micro SD nello slot per schede SD sul Raspberry Pi.
- Collegare un cavo Ethernet al Raspberry Pi e alla rete locale (collegandolo al nostro router).
- Collegare l'alimentatore da 5V al Raspberry Pi.

L'avvio del Raspberry Pi richiede circa 30 secondi. Dobbiamo trovare l'indirizzo IP per connetterci a esso utilizzando SSH. Possiamo utilizzare diversi approcci per farlo:

- Accedere all'interfaccia web del router e cercare i dispositivi connessi;
- Utilizzare un telefono cellulare collegato al router Wi-Fi utilizzando un'app di scansione della rete chiamata **Fing Overlook**;
- Utilizzare un comando come **nmap**. Supponendo che il nostro PC abbia l'indirizzo IP **192.168.0**.25, possiamo trovare tutti gli altri dispositivi nella stessa gamma di rete facendo quanto segue:
```
    sudo nmap -sP 192.168.0/24
```
Il quale potrebbe mostrare i seguenti dettagli:

    Starting Nmap 6.47 ( http://nmap.org ) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Per accedere al nostro Raspberry Pi, useremo il comando **ssh**.

```
    ssh pi@192.168.0.35
```

La prima volta che ci si connetterà, verrà mostrato qualcosa simile a:

    The authenticity of host '192.168.0.35 (192.168.0.35)' can't be established.
    ECDSA key fingerprint is 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Are you sure you want to continue connecting (yes/no)?

Sceglieremo **Sì**

    Warning: Permanently added 192.168.0.35 (ECDSA) to the list of known hosts.
    pi@192.168.0.35's password:

e useremo la *password predefinita*: *raspberry* che, in caso di login riuscito, mostrerà:

    The programs included with the Debian GNU/Linux system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
    permitted by applicable law.
    pi@raspberrypi:~ $

Possiamo configurare il Raspberry Pi usando un'interfaccia testuale tramite:

    sudo raspi-config

### Strumento di Configurazione del Software del Raspberry Pi (raspi-config)

Con questo strumento di configurazione cambieremo solo le seguenti impostazioni.

#### 1 Espandi Filesystem

Per impostazione predefinita, lo spazio su disco della scheda SD è delle stesse dimensioni del file .img da 1,4 GB che hai usato per creare la scheda SD per il tuo Raspberry Pi. Puoi usare questa opzione per ottenere il resto dello spazio su disco.

#### 2 Cambia Password Utente

Per motivi di sicurezza è meglio **cambiare la password predefinita** "raspberry" il prima possibile.

#### 3 Opzioni d'Avvio

Desideriamo che il Raspberry Pi avvii la console di testo

##### B2 Console Autologin Console di testo, login automatico come utente 'pi'

#### 9 Opzioni Avanzate

##### A3 Divisione della Memoria

Poiché utilizzeremo il Raspberry Pi come server headless senza collegarlo a un monitor, possiamo ridurre la memoria utilizzata per la GPU da 64 a **16**

#### 5 Opzioni di Internazionalizzazione

##### I2 Cambia Fuso Orario

Cambieremo il fuso orario con il nostro fuso orario (ad esempio, Europa/Amsterdam)

Dopo tutte le modifiche, riavvieremo il Raspberry Pi e ci collegheremo di nuovo con la nostra nuova password.

    ssh pi@192.168.0.35

Ora è il momento di installare tutto il resto.

## Aggiornare il software

Prima di installare qualsiasi altra cosa, noi:

- **aggiorneremo** la lista delle versioni del software da tutti i repository 
  esterni
    sudo apt-get update

- **aggiorneremo** tutto il software installato
    sudo apt-get upgrade

**Aggiornare la lista delle versioni e aggiornare tutto il software sono operazioni
che dovrebbero essere eseguite regolarmente.**

## Server web Nginx

Una veloce e leggera alternativa al server web Apache è il sempre più popolare server web **Nginx**.

### Installazione di Nginx

Installeremo nginx e tutte le dipendenze (leggi: software di cui nginx ha bisogno per funzionare) con

    sudo apt-get install nginx

Riceveremo un messaggio simile a:

    Lettura dei file di elenco... Fatto
    Costruzione dell'albero delle dipendenze
    Lettura delle informazioni sullo stato... Fatto
    I seguenti pacchetti extra saranno installati:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
    Pacchetti suggeriti:
     libgd-tools fcgiwrap nginx-doc ssl-cert
    I seguenti pacchetti NUOVI saranno installati:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
    0 aggiornati, 12 installati di recente, 0 da rimuovere e 0 non aggiornati.
    È necessario scaricare 3.550 kB di archivi.
    Dopo questa operazione, verranno utilizzati 8.666 kB di spazio su disco aggiuntivi.
    Vuoi continuare? [Y/n] y

Scegliendo "y" nginx e tutti i pacchetti necessari verranno installati.

Puoi verificare l'installazione con un browser. Vai all'indirizzo IP del tuo Raspberry Pi, nel nostro caso
<a href="http://192.168.0.35/"
rel="nofollow noreferrer noopener">http://192.168.0.35/</a> Dovremmo vedere un messaggio simile a:

    Benvenuti in nginx su Debian!
    Se vedi questa pagina, il server web nginx è stato installato con successo e funziona su Debian. Ulteriori configurazioni sono richieste.
    Per la documentazione online e il supporto, si prega di fare riferimento a nginx.org.
    Si prega di utilizzare lo strumento reportbug per segnalare bug nel pacchetto nginx con Debian.
    Tuttavia, controllare i report di bug esistenti prima di segnalare un nuovo bug.
    Grazie per aver usato Debian e nginx.

#### Avviare e fermare Nginx

Dopo l'installazione, Nginx verrà avviato automaticamente. Puoi:

- Fermare Nginx: sudo service nginx stop
- Avviare Nginx: sudo service nginx start
- Riavviare Nginx: sudo service nginx restart

### Configurare Nginx

#### Configurazione globale di Nginx

Nella configurazione globale di Nginx possiamo configurare la cache predefinita, ecc. Il Raspberry Pi 3 utilizza un processore ARM Cortex-A53 **quad-core** a 64 bit da 1,2 GHz. Se hai una versione anteriore con meno core della CPU, dovresti usare

    sudo nano /etc/nginx/nginx.conf

per cambiare "worker_processes" per adattarlo alla quantità di CPU del tuo dispositivo. Per impostazione predefinita, è configurato come

    worker_processes 4;

quindi per il Raspberry Pi 3 non devi cambiarlo.

Dopo aver modificato la configurazione di Nginx o la configurazione del dominio virtuale, devi fare un

    sudo nginx reload

per rendere effettive le modifiche.

#### Domini virtuali

È possibile eseguire più siti web Joomla sullo stesso server utilizzando domini virtuali.

Metti ogni sito web in una cartella separata nella directory webroot predefinita /var/www/, ad esempio:

- /var/www/example.com/
- /var/www/voorbeeld.nl/
    sudo mkdir /var/www/example.com
    sudo mkdir /var/www/voorbeeld.nl

Per ogni sito creeremo un dominio virtuale che è fondamentalmente un file di testo con informazioni specifiche del dominio:

- /etc/nginx/sites-available/example.com
    server {
    listen 80;
    server_name example.com www.example.com;
    root /var/www/example.com;

    access_log /var/log/nginx/example.com.access_log;
    error_log /var/log/nginx/example.com.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

- /etc/nginx/sites-available/voorbeeld.nl
    server {
    listen 80;
    server_name voorbeeld.nl www.voorbeeld.nl;
    root /var/www/voorbeeld.nl;

    access_log /var/log/nginx/voorbeeld.nl.access_log;
    error_log /var/log/nginx/voorbeeld.nl.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

Dobbiamo abilitare ogni sito collegando dal /etc/nginx/sites-enabled/ al dominio virtuale in "sites-available". Creiamo un link simbolico per ciascun dominio virtuale:

    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
    sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl

Per rendere effettiva questa configurazione del dominio virtuale, facciamo

    sudo nginx reload

e quando tutto è stato configurato correttamente, risponderà:

    Ricaricamento della configurazione nginx: nginx.

## Database

Possiamo installare MariaDB o MySQL; Joomla funzionerà con entrambi. Installiamo MariaDB con:

    sudo apt-get install mariadb-server

Durante l'installazione devi aggiungere una password per l'utente **root**. Creiamo una **password del database**, ad esempio **correcthorsebatterystaple**.

Infine, miglioriamo la sicurezza della nostra installazione di MariaDB rimuovendo gli account root accessibili dall'esterno dell'host locale, gli account utente anonimi e il database di test. Possiamo farlo con

    mysql_secure_installation

## PHP

Per PHP installeremo **php-fpm** (FastCGI Process Manager) che viene eseguito come daemon e riceve richieste Fast/CGI. Inoltre, installeremo **php5-mysql**, un modulo per le connessioni al database MySQL direttamente dagli script PHP.

PHP7 più recente dovrebbe essere installato con

    sudo apt-get install php-fpm php-mysql

Ora dobbiamo informare Nginx che dovrebbe usare php-fpm per i file .php. Aggiungiamo un paio di righe ai nostri domini virtuali:

    sudo nano /etc/nginx/sites-available/example.com

aggiungi:

    location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
    }

Testalo creando il seguente file PHP

    sudo nano /var/www/example.com/test.php

Usiamo un browser per testare se vediamo la pagina di configurazione PHP su
<a href="http://192.168.0.35/example.com/test.php" rel="nofollow noreferrer noopener">http://192.168.0.35/example.com/test.php</a>

## Joomla!

- da fare
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Collegare Raspberry Pi a Internet

Vogliamo che le persone su internet possano visitare il nostro sito Joomla sul nostro Raspberry Pi. Per fare ciò, dobbiamo **configurare il nostro router Internet** per inoltrare tutto il **traffico in entrata** sulla porta 80 **al nostro Raspberry Pi**.

Usa il tuo browser web per connetterti all'interfaccia web del tuo router. Un router si trova di solito sul primo numero del tuo intervallo IP, nel nostro caso su 192.168.0.1. Nel nostro router configuriamo l'**Inoltro delle Porte**:

- Indirizzo IP esterno: 0.0.0.0
- Porta esterna di inizio: 80
- Porta esterna di fine: 80
- Indirizzo IP interno: 192.168.0.35 (= il nostro Raspberry Pi)
- Porta interna di inizio: 80
- Porta interna di fine: 80
- Protocollo: TCP

Assicurati che sia abilitato.

Se tutto funziona correttamente, dovresti vedere il tuo sito Joomla sul Raspberry Pi visitando il tuo indirizzo IP esterno (Trova il tuo indirizzo IP esterno con uno strumento come <a href="http://www.whatsmyip.org/" rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Utilizzare un nome di dominio

Supponiamo che il nostro indirizzo IP esterno sia 42.42.42.42. Supponiamo anche di aver registrato un nome di dominio chiamato example.com. Vogliamo servire il nostro sito Joomla sul nostro Raspberry Pi ai visitatori che visitano example.com. Se il registrar del nome di dominio ci dà la possibilità di configurare il server **Domain Name System (DNS)**, allora dovremo creare un **record MX** nel DNS che punti il nostro **nome di dominio** al nostro **indirizzo IP** 42.42.42.42. Nota che può richiedere fino a 24 ore affinché tutti i provider di internet reindirizzino il traffico dei loro clienti al record MX configurato.

### Indirizzo IP statico

La maggior parte dei router continuerà ad assegnare lo stesso indirizzo IP interno al tuo Raspberry Pi. A volte è meglio configurare il tuo Raspberry Pi per utilizzare un indirizzo IP statico:

    sudo nano /etc/network/interfaces

cambia

    iface eth0 inet static

in

    iface eth0 inet static
    address 192.168.0.35
    netmask 255.255.255.0
    gateway 192.168.0.1

Il gateway è l'indirizzo IP del tuo router. Puoi anche trovarlo usando

    route

# Link esterni

- <a href="https://raspberrypi.org" rel="nofollow noreferrer noopener">Raspberry Pi Foundation</a> (RPF) - sito ufficiale e forum
- <a href="http://elinux.org/RaspberryPiBoard" rel="nofollow noreferrer noopener">Raspberry Pi Wiki</a>, supportato dal RPF
- Video della presentazione <a href="https://youtu.be/u2MFQCoexD0" rel="nofollow noreferrer noopener">Joomla su Raspberry Pi (con Nginx)</a> al Joomladay Germania 2013 a Norimberga, Germania

*Tradotto da openai.com*

