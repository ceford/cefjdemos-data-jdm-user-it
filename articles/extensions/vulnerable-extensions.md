<!-- Filename: jdocmanual?manual=user&heading=extensions&filename=vulnerable-extensions.md / Display title: Estensioni Vulnerabili  -->

## Fonti delle Estensioni

Chiunque può scrivere e distribuire un'estensione Joomla! come servizio per la comunità globale. Tali estensioni di **terze parti** possono essere trovate sui siti web di sviluppatori di estensioni professionali, siti web di blog personali, GitHub e repository simili e sul sito web della Directory delle Estensioni di Joomla.

## Estensioni Vulnerabili

Pochissime fonti offrono estensioni intenzionalmente dannose. Solitamente, un'**estensione vulnerabile** è quella che è stata trovata contenere (o contribuire a) una vulnerabilità di sicurezza dopo il rilascio iniziale.

Le estensioni vulnerabili non sono necessariamente codificate in modo approssimativo. Man mano che il Web si evolve, i requisiti tecnici e le pratiche di codifica comunemente accettate cambiano. I progetti attivi rilasciano nuove versioni delle loro estensioni man mano che i requisiti cambiano e risolvono rapidamente qualsiasi vulnerabilità segnalata.

Se sei preoccupato per una delle tue estensioni, dovresti consultare la lista delle Estensioni Vulnerabili di Joomla (VEL), che contiene informazioni su oltre 240 estensioni, per lo più vecchie.

## Il JED Checker

Se sei preoccupato per un'estensione che non compare nel VEL, puoi utilizzare l'estensione JED Checker. Questa è un'estensione utilizzata per controllare le estensioni inviate per apparire nella lista della Directory delle Estensioni Joomla. Si installa come qualsiasi altra estensione. Una volta utilizzata, accetta un file zip dell'estensione ed esamina i suoi contenuti per verificarne la conformità agli standard JED. È estremamente utile anche per le estensioni che non compaiono nella lista JED. Ecco un esempio di screenshot:

![risultato del jed checker](../../../en/images/extensions/extensions-jed-checker.png)

I 400 file PHP con Avviso di Licenza GPL mancante si trovano in librerie di terze parti con una Licenza diversa. Anche i 30 file identificati dallo Script di Scansione Anti-Malware di Joomla si trovano in quelle librerie di terze parti. C'è del lavoro da fare sui file in cui manca la sicurezza JEXEC!

## Rimozione di un'Estensione Vulnerabile

### Crea un Elenco di File da Rimuovere

Se riesci a trovarlo, leggi il file XML dell'estensione per determinare esattamente quali directory, file e tabelle del database sono state aggiunte al tuo sistema. Il file XML si trova nell'archivio zip originale utilizzato durante il processo di installazione dell'estensione. Ad esempio, l'archivio zip per un'estensione chiamata mod_vulnerable, conterrà un file XML chiamato mod_vulnerable.xml e potrebbe contenere un elenco di file come il seguente:

```
    mod_vulnerable.php
    mod_vulnerable/vulnerable_file.txt
    mod_vulnerable/another_vulnerable_file.txt
    mod_vulnerable/yet_another_vulnerable_file.txt
    mod_vulnerable/index.html
```

### Disinstallare Tramite l'Installer di Joomla

Utilizzando l'Installer nel backend Amministratore di Joomla!, disinstalla l'estensione vulnerabile. Potrebbe essere necessario disinstallare anche moduli, componenti o plugin correlati.

### Verificare che il Processo di Disinstallazione sia Completo

Non fidarti che l'estensione rimuova in modo sicuro tutti i suoi file. Confronta directory e file sul tuo sistema con l'elenco XML dell'estensione per assicurarti che tutti i file correlati siano stati effettivamente rimossi.

### Facoltativamente, Rimuovere le Tabelle del Database Correlate

Controlla il tuo database e rimuovi eventuali tabelle create dall'estensione. Per facilitare il processo di aggiornamento a nuove versioni, molti script di disinstallazione non rimuovono le tabelle del database correlate. Puoi trovare l'elenco delle tabelle nel file XML di ciascuna estensione.

Se hai intenzione di installare una versione dello stesso componente più sicura e compatibile e desideri riutilizzare i dati esistenti, puoi generalmente lasciare le tabelle del database così come sono.

### Rimuovere i Link del Menu

Semplicemente rimuovere i link del menu a un'estensione o non pubblicare un modulo **non** è sufficiente per proteggere il tuo sito! Finché i file dell'estensione esistono sul tuo server, sei vulnerabile. Nota come negli esempi seguenti un attaccante può bypassare il file index di Joomla! per mirare direttamente a qualsiasi file, di qualsiasi estensione.

```
    www.tuo_sito.org/components/com_bad_component/vulnerable_file.php
    www.tuo_sito.org/modules/mod_bad_module/vulnerable_file.php
```

*Tradotto da openai.com*

