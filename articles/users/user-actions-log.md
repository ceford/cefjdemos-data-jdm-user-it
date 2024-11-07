<!-- Filename: J4.x:User_Actions_Log / Display title: Registro Azioni Utente   -->

## Introduzione

Il componente Log delle Azioni Utente (com_actionlogs) fornisce un'infrastruttura per creare un registro delle attività del sito web. Le azioni che vengono registrate possono essere regolate in modo dettagliato dall'amministratore del sito. Le estensioni di terze parti possono integrarsi nel componente per aggiungere messaggi personalizzati o far elaborare al sistema le azioni standard dell'amministratore.

**Nota:** Solo gli Super User hanno accesso al componente Log delle Azioni Utente.

## Registro Azioni Utente

Per visualizzare l'elenco del Registro Azioni Utente:

- Seleziona **Utenti → Registro Azioni Utente** dal menu Amministratore.

![pagina elenco registro azioni utente](../../../en/images/users/user-actions-log-list.png)

Da questa pagina un Super Utente ha una panoramica globale di tutte le attività utente
eseguite su un sito.

- Esporta Selezionati come CSV: questo pulsante esporta solo gli elementi selezionati
  nell'elenco visibile.
- Esporta Tutti come CSV: questo pulsante esporta tutti i record. I filtri sono 
  ignorati.
- Elimina: questo pulsante elimina gli elementi selezionati.
- Cancella Registro: questo pulsante elimina tutte le voci del registro.
- Opzioni: un modulo di configurazione per impostare le opzioni di registrazione.

## Opzioni

Il modulo Opzioni del Registro delle Azioni Utente consente al Super Utente di selezionare quali eventi registrare e se includere o meno gli indirizzi IP nei dati del registro.

![pagina delle opzioni del registro delle azioni utente](../../../en/images/users/user-actions-log-options.png)

## Plugin

Il sistema di registrazione delle azioni utilizza diversi plugin:

### Registro Azioni - Joomla

Quando abilitato, questo plugin registra le azioni principali degli utenti, incluse azioni come login/logout, aggiornamento articolo, aggiunta modulo. Il plugin non ha parametri.

### Sistema - Registro Azioni Utente

Quando abilitato, questo plugin definisce il numero di giorni dopo i quali i log verranno eliminati. Un valore di zero significherà che i log non verranno mai eliminati automaticamente.

### Privacy - Registri delle Azioni

Quando abilitato, questo plugin esporta i dati del registro azioni per una richiesta di privacy dell'utente.

## Modulo Azioni Recenti

Questo modulo è visualizzato solo per gli Super Utenti nel cruscotto principale.

![modulo registro azioni utente](../../../en/images/users/user-actions-log-module.png)

## Come collegare un'estensione al sistema

Sentiti libero di modificare questa sezione migliorandola o correggendola.

### Script di installazione del componente

Aggiungi l'estensione alla tabella (`#__action_logs_extensions`) in modo che appaia nella configurazione dei registri delle azioni utente.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Se fallisce, lancerà una RuntimeException
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Aggiungi la configurazione dell'estensione alla tabella (`#__action_log_config`) in modo che i dati delle tue azioni vengano acquisiti.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transaction';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Se fallisce, lancerà una RuntimeException
                // Inserisci l'oggetto nella tabella.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Ovviamente sarebbe meglio eseguire dei controlli per garantire che il record non esista già.

### Helper del componente

In questo esempio, l'helper del componente viene utilizzato per eseguire la memorizzazione delle azioni.
```php
       /**
         * Registra i dettagli della transazione nel registro
         * @param   object  $user    Evita di ottenere di nuovo l'utente corrente.
         * @param   int     $tran_id  L'id della transazione appena creata o aggiornata
         * @param   int     $id  Riferimento id passato dal modulo per identificare se nuovo record
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // ottieni i dettagli del componente come l'id
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // ottieni i dettagli della transazione da usare nel log per un facile riferimento
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transaction";
            if ($id === 0) { $type = 'Nuovo '; } else { $type = 'Aggiornamento '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Ottieni il modello da un altro componente da utilizzare
         * @param   string  $name    Il nome del modello. Opzionale. Predefinito per il mio per sicurezza.
         * @param   string  $prefix  Il prefisso della classe. Opzionale
         * @param   array   $config  Array di configurazione per il modello. Opzionale
         * @return object   Il modello
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Modulo front-end della transazione

Ora che le basi sono impostate, dobbiamo solo attivare il processo. Stiamo acquisendo informazioni su una transazione che viene creata o aggiornata e abbiamo un modello chiamato `transactionform.php`. È nel metodo Save che vogliamo acquisire un log.
```php
       // Quindi il codice sopra questo punto verifica e fa ciò che dovrebbe fare e poi, dopo il salvataggio con successo del record, controlliamo l'impostazione del parametro per vedere se è richiesto il logging, passiamo elementi chiave a recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // Attiva il log della transazione se richiesto
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // raccogli informazioni e registra in un nuovo record di log delle azioni
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### File di lingua

Infine, per aiutare con l'elenco dei registri delle azioni nell'area amministrativa di Joomla, vogliamo impostare alcuni elementi chiave di dati da visualizzare nel file di lingua en-GB/com_mycomponent.ini.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="L'utente {username} ha creato una transazione ( {type} )"
```

*Tradotto da openai.com*

