<!-- Filename: J4.x:Apache_PHP_Handler / Display title: Gestori Apache PHP  -->

## Note

Per determinare quale metodo il tuo server web sta utilizzando per gestire i file PHP, usa i link **Administrator / System / System Information** e seleziona la scheda PHP Information. Cerca nella pagina **Server API**. I modi comuni per un server web Apache di gestire i file PHP includono i seguenti:

### DSO (mod_php)

- **Vantaggio:** uno dei gestori più veloci disponibili.
- **Svantaggio:** funziona solo con una singola versione di PHP; i file salvati dagli script PHP sono di proprietà dell'utente Apache **eccetto** quando utilizzati insieme a mod_ruid2.
- **Per riconoscere:** Server API - Apache 2.0 Handler

### CGI/FastCGI

- **Vantaggio:** gli script vengono eseguiti come utente di dominio o sottodominio, gestore molto veloce.
- **Svantaggio:** più lento di mod_php, non è possibile inserire modifiche alla configurazione PHP in un file .htaccess.
- **Per riconoscere:** Server API - CGI/FastCGI

### FPM/FastCGI

- **Vantaggio:** molto veloce, ulteriore livello di flessibilità.
- **Svantaggio:** utilizza più memoria rispetto alla maggior parte degli altri, non è possibile inserire modifiche alla configurazione PHP in un file .htaccess.
- **Per riconoscere:** Server API - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Vantaggi:**
   - Fornisce supporto per la cache.
   - È il gestore più performante con un basso impiego di memoria.
   - Non richiede configurazione.
   - Può funzionare con più versioni di PHP in un'unica configurazione.
   - Supporta direttive di configurazione PHP tramite file .htaccess.
   - Sicuro perché gli script vengono eseguiti come proprietario del dominio.
- **Svantaggi:**
   - Non rende disponibili tutte le capacità di LSAPI.
- **Per riconoscere:** Server API - ?

Su un computer portatile o desktop locale puoi utilizzare mod_php, ma potresti dover impostare l'utente Apache con il tuo nome utente e puntare la radice del documento a una posizione nel tuo spazio file. Altrimenti avrai problemi di permessi su file e cartelle.

Su un servizio di hosting, devi utilizzare una delle alternative FastCGI o LSAPI. I servizi di hosting possono offrire una scelta.

*Tradotto da openai.com*

