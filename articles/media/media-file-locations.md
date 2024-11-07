<!-- Filename: J6.x:Media_File_Locations / Display title: Posizioni dei File Multimediali -->

## Introduzione

Per impostazione predefinita, Joomla memorizza sia le immagini degli utenti che i file dei documenti nella cartella */images* dell'installazione di Joomla. Qualsiasi link a tali media non viene elaborato direttamente da Joomla. Il server web li invia quando richiesto dal browser.

Se hai molti documenti, potresti volerli conservare in una cartella separata, idealmente una cartella */files* anch'essa nella radice del sito Joomla.

Per impostare una posizione per i file che sia separata dalle immagini, crea prima una nuova cartella nella radice della tua installazione, ad esempio **files**. Ricorda che sarà parte di un link URL, quindi utilizza lettere minuscole e non includere spazi o segni di punteggiatura.

### Plugin FileSystem - Locale

Trova il plugin *FileSystem - Locale* nell'elenco dei plugin e aprilo. Aggiungi la tua cartella *files* appena creata all'elenco dei luoghi in cui puoi conservare i media. Basta fare clic sul pulsante + e selezionare **files** dall'elenco delle cartelle disponibili.

![Plugin File System](../../../en/images/plugins/plugin-group-file-system-local.png)

L'opzione **Crea Miniature** impostata su **Sì** causa la creazione di immagini di piccole dimensioni con un'altezza o una larghezza massima di 200 pixel in media/cache/com_media/thumbs con la stessa struttura di cartelle della cartella media. Dovrebbe aumentare notevolmente la velocità di visualizzazione di una cartella con molte immagini. Non è necessario per i file poiché sono rappresentati da icone.

Assicurati che il plugin sia abilitato. **Salva & Chiudi**.

