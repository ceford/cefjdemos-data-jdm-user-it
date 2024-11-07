<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Spostare la Directory di Installazione -->

Molte volte installi Joomla in una sottodirectory e poi vuoi spostarla in una directory di livello superiore, ecco un breve tutorial su come farlo.

Supponiamo che tu abbia installato Joomla nella seguente cartella: public_html/tryjoomla. Ora che sei soddisfatto del sito, vorrai spostarlo in public_html.

1. Sposta tutti i file dalla sottodirectory (cioè,
    public_html/tryjoomla) alla directory di livello superiore (cioè, public_html).
    Puoi utilizzare il tuo client FTP preferito o il pannello di controllo fornito dal tuo servizio di hosting.
2. Scarica e apri il file configuration.php in un editor di testo.
3. Semplicemente rimuovi il nome della cartella tryjoomla dal percorso. Cerca le seguenti righe
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/username/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';
    ```
    Cambia in:
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/administrator/logs';
    var $tmp_path = '/home/username/public_html/tmp';
    var $ftp_root = 'public_html';
    ```
    N.B.: La variabile \$live_site raramente ha bisogno di un valore. Ma se durante l'installazione è stato assegnato un valore, modifica anche quel percorso.
    ```
    var $live_site = 'http://www.example.com/tryjoomla';
    ```
    Cambia in:
    ```
    var $live_site = 'http://www.example.com';
    ```
4. Controlla il file .htaccess del tuo sito. Anche la sottocartella dovrebbe essere rimossa lì. La direttiva RewriteBase dovrebbe essere commentata. Controlla un eventuale RewriteRule che contiene la vecchia sottodirectory.
5. Verifica che nel pannello di controllo del tuo hosting non ci siano ordini di reindirizzamento verso la vecchia sottodirectory.
6. Se hai abilitato la cache, accedi al backend amministrativo (che ora sarà su `http://www.example.com/administrator` e non su `http://www.example.com/tryjoomla/administrator`). Vai a
    Sistema / Cache e cancella tutti i file della cache.

*Tradotto da openai.com*
