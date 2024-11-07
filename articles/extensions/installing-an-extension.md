<!-- Filename: Installing_an_extension / Display title: Installazione di un'estensione -->

## Documentazione dell'Estensione

Prima di iniziare, è sempre saggio leggere la documentazione associata a un'estensione. La maggior parte delle estensioni ha pagine web e forum dedicati, ed è una buona idea consultarli per primi. Se c'è un file README incluso con l'estensione, dovresti leggerlo. Potrebbero esserci istruzioni speciali per l'installazione o la configurazione.

## Installazione Estensioni del Sistema

Il modulo Sistema / Installa / Estensioni è abbastanza ben documentato nella schermata di aiuto. Ciò che non è così ovvio è che ciascuno dei metodi di installazione è un plugin. Nelle prime versioni di Joomla 4, il plugin Installa dal Web era il primo nell'elenco e potrebbe essere ancora così nelle versioni che sono state aggiornate. Avere quel metodo per primo è scomodo se di solito utilizzi uno degli altri metodi, poiché ci vogliono alcuni secondi per recuperare i dati dal sito della Directory delle Estensioni di Joomla.

Per cambiare l'ordine:

- Vai a **Dashboard Principale / Plugin**
- Seleziona **installer** dal filtro a discesa **Seleziona Tipo**.
- Seleziona l'icona **Ordina** per rivelare le maniglie di ordinamento
  (ellissi verticali).
- Trascina l'elemento **Installer - Installa dal Web** in fondo
  all'elenco.
- Torna a **Sistema / Installa / Estensioni** per vedere il risultato.

Sei quindi pronto a utilizzare uno dei metodi di installazione standard.

### Carica File Pacchetto

Per la maggior parte delle estensioni e degli utenti, la procedura sarà:

- Scarica l'estensione sul tuo computer locale come un pacchetto zip.
- Dal backend del tuo sito Joomla (amministrazione) seleziona
  **Sistema → Installa → Estensioni**.
- Dalla scheda **Carica File Pacchetto** seleziona il pulsante *Sfoglia per il file* 
  e seleziona il pacchetto dell'estensione sul tuo computer locale o trascina e rilascia 
  il file dal tuo gestore file.
- Il processo di caricamento e installazione inizia automaticamente,
- Alcune estensioni potrebbero fornire ulteriori istruzioni sull'installazione.
- Nota che i moduli e i plugin devono essere solitamente abilitati prima di funzionare.

### Installa da Cartella

Alcune estensioni potrebbero essere troppo grandi per utilizzare il metodo Carica File Pacchetto,
di solito a causa di un limite sulla *Dimensione Massima di Caricamento dei File* impostato dal tuo host.
In questo caso, puoi utilizzare il metodo Installa da Cartella.

- Crea una directory temporanea sul tuo disco rigido locale e decomprimi l'
  archivio dell'estensione in questa directory temporanea.
- Utilizzando FTP, carica il contenuto di questa directory (inclusi file e
  sottodirectory) nella directory /tmp della radice di Joomla sul tuo server in modo che 
  tu abbia un percorso come /tmp/acmeextension.
- Nel campo Directory di Installazione specifica la directory del server dove hai 
  caricato i file e le sottodirectory del pacchetto, ad esempio
  /home/username/public_html/tmp/acmeextension.
- Seleziona il pulsante **Verifica e Installa** e Joomla installerà il contenuto
  della directory specificata.

### Installa da URL

Invece di scaricare un file zip sul tuo computer locale, puoi semplicemente usare l'URL 
per il download. Joomla recupererà il file zip direttamente e salterà i passaggi di download
e caricamento dei metodi precedenti.

### Installa dal Web

Questa opzione ti consente di installare un'estensione direttamente dalla Directory
delle Estensioni Joomla. L'elenco iniziale è in ordine di numero di recensioni ma puoi selezionare 
per Categoria per trovare rapidamente un elenco di estensioni che potrebbero soddisfare le tue esigenze.

## Scopri l'installazione del sistema

Come descritto nella schermata di aiuto, la funzione Scopri consente di installare estensioni che sono troppo grandi per alcuni sistemi, soprattutto ambienti di hosting condiviso a basso costo. Qualcosa che potrebbe non essere ovvio è che potresti dover creare cartelle in posizioni diverse sul tuo servizio di hosting, in genere:

- Carica i file del sito in siteroot/components/com_mybigcomponent
- Carica i file dell'amministratore in siteroot/administrator/components/com_mybigcomponent
- Carica i file multimediali (CSS e JavaScript) in siteroot/media/com_mybigcomponent
- Carica i file di lingua del sito in siteroot/language/en-GB se non sono in una cartella di lingua nella cartella del sito del componente.
- Carica i file di lingua dell'amministratore in siteroot/administrator/language/en-GB se non sono in una cartella di lingua nella cartella dell'amministratore del componente.

Una volta fatto ciò, Scopri dovrebbe trovare e consentire l'installazione del componente e potrebbe effettivamente funzionare.

## Lingue di Installazione del Sistema

La lingua predefinita è l'inglese GB. Non può essere rimossa o installata. Potrebbe non essere evidente ma ogni pagina carica prima le stringhe appropriate in en-GB per garantire che le chiavi di lingua utilizzate dai programmatori non appaiano nel risultato della pagina. Se la lingua selezionata dall'utente non è l'inglese, viene caricata la lingua dell'utente, sovrascrivendo le stringhe inglesi. Se una lingua non è stata completamente tradotta il risultato sarà un mix di lingua utente e stringhe inglesi. Potrebbe sembrare strano ma è meglio di un mix di chiavi utente e di programmatori.

Dall'elenco delle lingue disponibili seleziona quella che desideri installare. Alcune sono contrassegnate con un pulsante verde per indicare che sono aggiornate con l'attuale versione di Joomla. Altre sono contrassegnate con un pulsante giallo per indicare che non sono completamente aggiornate. Procedi comunque con l'installazione. Potresti vedere alcune parole in inglese in posti che dovrebbero essere nella lingua selezionata. Ma potrebbero essere rare.

*Tradotto da openai.com*

