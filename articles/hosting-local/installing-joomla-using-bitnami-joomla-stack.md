<!-- Filename: Installing_Joomla!_using_BitNami_Joomla!_stack / Display title: Installazione di Bitnami -->

## Prefazione

**NOTA:** Il pacchetto BitNami Joomla! non esiste più come installer autonomo. Ora è disponibile come: 1) Un'istanza basata sul cloud, 2) In un container, sia Kubernetes che Docker, o 3) Una macchina virtuale. La macchina virtuale verrà eseguita sul tuo sistema operativo in un hypervisor come Virtual Box o VMware Player. È ancora fornita con tutte le dipendenze richieste come nell'installer autonomo.

L'Opzione 1 di seguito non si applica più. Inoltre, nell'Opzione 2, BitNami Lamp Stack più in basso, viene fornito nel cloud o in una macchina virtuale. In ogni caso, Bitnami rende avere un'installazione locale performante di Joomla! facile e completa.

Puoi scaricare l'ultima versione del pacchetto Bitnami per Joomla! per Windows, Linux e Mac su <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a>.

**Revisione Necessaria!**

BitNami Joomla! Stack è un installer all-in-one che facilita l'installazione di Joomla sul tuo computer. È gratuito, facile da usare e autonomo. Ciò significa che raggruppa e configura automaticamente ogni pezzo di software (dipendenza) necessario per eseguire Joomla per scopi di sviluppo o produzione, inclusi Apache HTTP Server, MySQL e PHP.  

## Opzione 1: stack Joomla! (Consigliato)

Questo metodo presuppone che tu abbia già installato un ambiente
(**W**indows/**L**inux/**M**ac)...**AMP** (Apache HTTP Server, MySQL e
PHP) sul tuo sistema.

### Installazione dello Stack Joomla!

Indipendentemente dal sistema operativo che stai utilizzando (Windows / Linux /
Mac), il processo di installazione è lo stesso.

Scarica l'ultima versione dello Stack Joomla! dal
<a href="http://bitnami.org/stack/joomla"
rel="nofollow noreferrer noopener">sito web di BitNami</a>.

Trova il programma di installazione che hai appena scaricato (il nome del file sarà simile a
bitnami-joomla-VERSION-linux-installer.run). Fai doppio clic sull'icona per
avviare il programma di installazione.

Se stai utilizzando Linux, dovrai prima dare i permessi di esecuzione al
file, usando questo comando:

chmod +x /percorso/del/bitnami-joomla-VERSION-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Configurazione di Joomla Bitnami lampstack" />

Clicca su "Next".

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Componenti Joomla Bitnami lampstack" />

Seleziona i componenti che desideri installare. Se non sei sicuro, lascia
i componenti predefiniti selezionati. Clicca su "Next" quando hai finito.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Directory di installazione di Joomla Bitnami lampstack" />

Ora ti chiederà dove vuoi installare il programma. Indica la
posizione in cui vuoi installare lo stack BitNami Joomla! e clicca
"Next" quando hai finito.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Account admin di Joomla Bitnami lampstack" />

L'utente e la password forniti qui verranno utilizzati per creare l'account admin
in Joomla! Clicca su "Next" quando hai finito.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Nome del sito Joomla Bitnami lampstack" />

Inserisci il nome che desideri utilizzare per il tuo sito Joomla e clicca "Next".

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Pronto per l'installazione di Joomla Bitnami lampstack" />

Il programma di installazione ti permette di configurare un account email in modo che Joomla! possa
inviare notifiche via email. Clicca su "Next".

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Copia dei file di Joomla Bitnami lampstack" />

Attendi un momento mentre il programma di installazione copia i file e configura la tua
installazione di Joomla!

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Schermata finale di Joomla Bitnami lampstack" />

Joomla! è ora configurato e pronto per essere utilizzato. Clicca su "Finish" per avviare
l'applicazione.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png"
decoding="async" data-file-width="784" data-file-height="586"
width="784" height="586" alt="Gestione server Joomla Bitnami lampstack" />

Utilizzare lo strumento di gestione è semplice per avviare/fermare i server Apache e MySQL.

<img
src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png"
decoding="async" data-file-width="982" data-file-height="729"
width="982" height="729" alt="Schermata dell'applicazione Joomla" />

Puoi gestire facilmente il database Joomla! con phpMyAdmin.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png"
decoding="async" data-file-width="982" data-file-height="751"
width="982" height="751" alt="Schermata phpMyAdmin" />

## Opzione 2: BitNami LAMPStack e Joomla!

### Che cos'è BitNami LAMPStack?

BitNami LAMPStack è un pacchetto gratuito e facile da installare che raggruppa ogni
software necessario (dipendenze) per configurare un ambiente LAMP (Apache, MySQL
e PHP per Linux) per scopi di sviluppo o produzione. È autonomo, non apporta modifiche
al tuo sistema e può essere disinstallato facilmente. Puoi scaricare l'ultima
versione di BitNami LAMPStack per Linux su
<a href="http://bitnami.org/stack/lampstack"
rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a>.
Sono disponibili anche una <a href="http://bitnami.org/stack/wampstack"
rel="nofollow noreferrer noopener">versione per Windows</a>
e una <a href="http://bitnami.org/stack/mampstack"
rel="nofollow noreferrer noopener">versione per OS X</a>.

Indipendentemente dal sistema operativo che stai utilizzando (Windows / Linux /
Mac), il processo di installazione è lo stesso.

### Installazione di BitNami LAMPStack

Trova l'installer che hai appena scaricato dal sito web di BitNami (il
nome del file sarà simile a
bitnami-lampstack-VERSION-linux-installer.run). Fai doppio clic sull'icona per
avviare l'installer.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Benvenuto lampstack di Bitnami" />

Clicca su "Avanti".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Directory lampstack di Bitnami" />

Ora ti verrà chiesto dove vuoi installare il programma. Seleziona la
posizione sulla tua macchina e clicca su "Avanti" quando hai finito.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Password lampstack di Bitnami" />

Digita la tua password root di MySQL. Questa sarà la password per l'utente "root"
del database.

<img
src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Pronto per installare lampstack di Bitnami" />

L'installer è ora pronto per iniziare il processo di installazione. Clicca
su "Avanti".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Copia dei file di Bitnami lampstack" />

Aspetta un minuto mentre l'installer copia i file e configura il tuo
installazione di LAMPStack.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Schermata finale di Bitnami lampstack" />

BitNami LAMPStack è ora configurato ed è pronto per essere utilizzato. Clicca su "Fine"
per lanciare l'applicazione.

### Installazione manuale di Joomla!

Segui le istruzioni descritte nell'articolo Installare
Joomla.

