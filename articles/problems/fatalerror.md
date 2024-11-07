<!-- Filename: J4.x:FatalError / Display title: ErroreFatale -->

## Introduzione

Di tanto in tanto Joomla può visualizzare una pagina di errore invece della pagina
che ti aspettavi. Ci sono due tipi di pagine di errore:

- La pagina di errore del sistema ha uno sfondo rosso. Viene visualizzata se si verifica
  un errore grave prima che il sito o il modello dell'amministratore venga reso.
- La pagina di errore del modello assomiglia al normale sito o modello dell'amministratore ma l'area dei contenuti viene sostituita con un messaggio di errore. Questo accade quando l'errore si verifica nel codice dei contenuti.

### Pagina di Errore del Sistema

![Pagina di errore fatale del sistema](../../../en/images/problems/fatal-error.png)

### Pagina di Errore del Modello

![Pagina di errore del modello](../../../en/images/problems/template-error.png)

## Come Risolvere

Ci sono diverse possibili ragioni per cui si verificano errori fatali. Eccone alcune:

- Un cambiamento nel tuo host, ad esempio una versione di PHP aggiornata che non è compatibile con Joomla o una delle tue Estensioni.
- Un problema con lo spazio su disco, l'uso della memoria o il tempo di esecuzione dello script.
- Una nuova Estensione installata o abilitata che non è compatibile con Joomla. Un plugin difettoso può disabilitare l'accesso all'Amministratore!

### Abilitare il Debug

Se la tua interfaccia di Amministrazione **sta** ancora funzionando:
- Vai a **Dashboard Principale → Pannello di Sistema → Configurazione Globale**. 
- Nella scheda Sistema, imposta *Debug Sistema* su *Sì*. 
- Nella scheda Server, imposta *Rapporto Errori* su *Massimo*. 
- Quindi premi *Salva & Chiudi*.

Se la tua interfaccia di Amministrazione **non** sta funzionando, modifica il file *configuration.php* nella cartella principale del tuo sito Joomla.

1.  Cambia i permessi da *444* o *-r--r--r--* (nessuno ha il permesso di scrivere nel file) a *644* o *-rw-r--r--* (solo il Proprietario ha il permesso di scrivere).
2.  Modifica il file con un editor di testo e imposta `$debug` su `true` e `$error_reporting` su `'maximum'`.
3.  *Salva* il file.

Con le modifiche fatte, ricarica la pagina che causava l'errore. Ora dovresti vedere un tracciato dello stack. Esempio:

![Pagina di errore del template](../../../en/images/problems/template-error-stack-trace.png)

Il primo elemento nel tracciato dello stack indica dove l'errore è stato attivato. A volte è sufficiente per identificare l'Estensione difettosa. A volte l'Estensione difettosa è più in basso nel tracciato dello stack. Potrebbe non significare molto per te, ma il tracciato dello stack è inestimabile per gli esperti che rispondono alle domande nei Forum di Joomla.

Se riesci a identificare l'Estensione difettosa, disabilitala. Puoi farlo usando l'interfaccia di Amministrazione se sta funzionando. Altrimenti, usa phpMyAdmin per trovare l'Estensione nella tabella del database `#__extensions` e imposta il suo valore `enabled` su `0`. Non dovresti aver bisogno di disabilitare nessuna Estensione core di Joomla.

## Assistente Post del Forum

Per aiutare a risolvere i problemi, dovresti scaricare il
[Forum Post Assistant (FPA)](https://forumpostassistant.github.io/docs/) e
caricarlo nella root del tuo sito web Joomla. Il link per trovarlo è anche
vicino alla parte superiore di ogni pagina del Forum di Joomla. L'FPA è uno script PHP indipendente
che analizza la tua installazione di Joomla e ti indica cosa potrebbe
non funzionare correttamente. Ancora una volta, potrebbe non significare molto per te, ma gli esperti che
rispondono alle domande nei Forum potrebbero chiederti di visionarlo.

## Pulizia

Quando il tuo problema è risolto:

1. Vai su **Dashboard Home → Pannello di sistema → Configurazione globale**
2. Seleziona la scheda Sistema e imposta *Debug Sistema* su *No*.
3. Seleziona la scheda Server e imposta *Rapporto errori* su *Impostazione predefinita del sistema*.
4. *Salva e Chiudi*.
5. Rimuovi l'Assistente post del forum.

I permessi del file `configuration.php` sono impostati su sola lettura (444 o *r--r--r--*) quando il modulo di Configurazione globale viene salvato. Non è necessario farlo manualmente. 

*Tradotto da openai.com*

