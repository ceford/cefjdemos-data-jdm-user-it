<!-- Filename: J5.x:Improving_SEO_with_Strict_Routing_and_SEF_URLs / Display title: SEO Routing Stricto -->

## Introduzione

L'opzione di Routing Rigido, introdotta in Joomla 5.2, migliora le prestazioni SEO della piattaforma consentendo regole di routing più rigorose utilizzando un interruttore nel plugin *System - SEF*. Aiuta a eliminare i contenuti duplicati imponendo URL più coerenti e reindirizzando i duplicati all'URL corretto con un reindirizzamento 301.

![system sef plugin settings](../../../en/images/seo/seo-system-sef-plugin.png)

### Applicazione dei Suffissi

Attualmente, Joomla consente l'accesso agli URL con o senza suffisso quando questa opzione è abilitata nelle opzioni della *Configurazione Globale*.

L'opzione **Imponi un suffisso tramite reindirizzamento** nel plugin *System - SEF* impone un comportamento coerente del suffisso. Quando è abilitata, reindirizza le richieste GET a un URL con un suffisso se manca. Reindirizzerà anche gli URL con un parametro di formato query all'URL più pulito, sostituendo il suffisso con il parametro di formato dove necessario.

Questa funzionalità è prevista per diventare il comportamento predefinito in Joomla 6.0, dove l'opzione per abilitarla o disabilitarla verrà rimossa, e questa funzionalità sarà integrata nel sistema di routing core. Per ora, questa opzione consente agli utenti di testare il comportamento su sistemi live e di disabilitarla se dovessero sorgere problemi imprevisti durante il periodo di transizione da Joomla 5.1 a 6.0.

## Come Accedere

Per abilitare il routing rigoroso per la SEO:

1. Seleziona l'elemento **Plugin** nel *Cruscotto Home*.
1. Trova e apri il plugin **Sistema - SEF**.
2. Imposta **Instradamento Rigido** su *Sì* per abilitare una gestione più rigorosa degli URL.
3. Imposta **Applicare un Suffisso tramite Reindirizzamento** su Sì o No a seconda della tua preferenza per applicare i suffissi degli URL.

Una volta abilitato, Joomla reindirizzerà automaticamente gli URL duplicati a quello corretto con un reindirizzamento 301, migliorando la SEO consolidando il contenuto sotto un singolo URL autorevole.

## Note aggiuntive

Questa funzionalità è progettata per funzionare come un passaggio preparatorio per ulteriori miglioramenti SEO ed è attivata automaticamente per le nuove installazioni di Joomla 5.2. Prepara il terreno per futuri miglioramenti al sistema di routing di Joomla.  
*Tradotto da openai.com*

