<!-- Filename: J4.x:Media:_Options / Display title: Media: Opzioni -->

## Introduzione

La pagina *Media: Opzioni* viene utilizzata per controllare il caricamento e l'archiviazione dei media, sia immagini che file. **Attenzione:** ci sono implicazioni di sicurezza associate con alcuni tipi di file - una possibile via d'accesso per un hacker.

Per accedere al modulo *Media: Opzioni*, selezionare il pulsante **Opzioni** nella Toolbar della pagina Media. I campi sono ben commentati e forniti con valori predefiniti che dovrebbero essere adatti per quasi tutti i siti. Di solito, è necessario utilizzare il modulo delle opzioni solo se si desidera mantenere separati i File dalle Immagini o se si dispone di un formato di file insolito non incluso nell'elenco predefinito.

## Screenshot

![Il modulo Opzioni media](../../../en/images/media/media-options.png)

## Percorso verso File e Cartelle

Questi sono elementi separati nel modulo di configurazione, ma entrambi puntano alla cartella *images* in una nuova installazione di Joomla. Se desideri archiviare separatamente media non immagini (ad esempio PDF, fogli di calcolo e file di testo), segui i passaggi seguenti:

1. Crea una cartella chiamata *files* nella radice della tua installazione di Joomla.
2. Abilita il plugin *FileSystem - Local* e configuralo, come descritto nell'articolo su [Posizioni dei File Multimediali](jdocmanual?article=user/media/media-file-locations).
3. Inserisci il nome della cartella, *files*, nel campo *Path to Files Folder* del modulo Opzioni Multimediali.

Nel modulo Opzioni, inserisci il nome della cartella nel campo **Percorso verso la Cartella dei File**. Assicurati di non utilizzare il nome di una cartella principale esistente di Joomla.

Una volta configurato, sarai in grado di scegliere tra le cartelle immagini e file nella parte Local della vista Media.

![La pagina media](../../../en/images/media/media-sample-data-cassiopeia.png)

## Tipi di Immagini o Documenti Aggiuntivi

Potresti scoprire che un'Immagine o un Documento non può essere caricato. In tal caso, verifica che
la sua estensione sia tra le *Estensioni Consentite*, che la sua estensione sia tra
i *Tipi di Estensioni Legali* per il media e che sia tra i
*Tipi di MIME Legali* (potresti dover cercare queste informazioni). Tutti e tre devono essere corretti
o il caricamento verrà negato.
*Tradotto da openai.com*

