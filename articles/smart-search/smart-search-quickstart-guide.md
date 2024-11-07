<!-- Filename: Smart_Search_quickstart_guide / Display title: Guida Rapida alla Ricerca Intelligente   -->

## Contesto

La funzione di ricerca è stata presente in Joomla! fin dai suoi primi tempi. Permetteva agli utenti di cercare nel database parole o frasi e restituire i risultati nell'ordine in cui venivano trovati. Quella forma di ricerca è stata rimossa e sostituita da Smart Search, che preindicizza parole significative e utilizza algoritmi di punteggio e filtraggio per aiutare a restituire i migliori risultati. Smart Search è abilitata di default in Joomla 4 e 5.

### Attenzione

Se hai elementi di contenuto che non sono disponibili per la visualizzazione pubblica, la funzione di completamento automatico mostrerà ancora i termini contenuti in quegli elementi di contenuto. Gli elementi di contenuto stessi non possono essere visualizzati e non verranno elencati nei risultati di ricerca, ma se la rivelazione della presenza di una parola o frase in un elemento di contenuto riservato è un problema, dovresti disabilitare il completamento automatico. Per disabilitare il completamento automatico, utilizza la seguente procedura:

1. Accedi all'Amministratore.
2. Seleziona **Componenti → Ricerca Smart**.
3. Seleziona il pulsante della toolbar **Opzioni**.
4. Cambia *Suggerimenti di Ricerca* da **Mostra** a **Nascondi**.
5. Seleziona **Salva & Chiudi**.

## Preparazione dei plugin di Smart Search

Affinché i contenuti siano visualizzati nei risultati di ricerca, devono prima essere indicizzati da uno dei plugin di Smart Search. Prima di avviare l'indicizzatore, è consigliabile esaminare i plugin disponibili e disabilitare quelli che non saranno necessari per il tuo sito. Per esaminare i plugin di Smart Search disponibili, utilizza la seguente procedura:

1. Accedi all'area Amministratore.
2. Seleziona **Plugin** dalla *Home Dashboard*.
3. Filtra i plugin utilizzando l'elemento **finder** dalla lista **- Select Type -**.
4. Rivedi l'elenco dei plugin e disabilita quelli che non saranno necessari per il tuo sito selezionando l'icona del segno di spunta verde nella colonna Stato del plugin. Questo dovrebbe cambiare in una croce/cerchio grigio per indicare che il plugin è disabilitato.

## Esecuzione dell'Indicizzatore

Dopo aver esaminato i plug-in di ricerca, è il momento di avviare l'indicizzatore di Smart Search. Questo strumento analizzerà il contenuto del tuo sito web e costruirà un indice che permetterà ai visitatori del sito di effettuare ricerche rapide e intelligenti. Ci sono due modi per eseguire l'indicizzatore:

* Dal menu **Amministratore / Smart Search / Indice**. Questo è adatto per siti più piccoli.
* Dalla riga di comando. Questo è adatto per siti più grandi e non dovrebbe causare errori di time-out. Tuttavia, siti molto grandi potrebbero davvero aver bisogno di un servizio di ricerca esterno.

### Indicizzazione dall'interfaccia Amministratore

1. Accedi all'Amministratore.
2. Seleziona i menu **Componenti → Smart Search → Indice**.
3. Seleziona il pulsante **Indice** nella barra degli strumenti per avviare l'indicizzatore. Questo farà caricare una finestra modale con alcune informazioni sullo stato dell'indicizzazione e una barra di avanzamento.

A seconda delle dimensioni del tuo sito, l'indicizzazione può richiedere da pochi minuti a qualche ora per essere completata. L'indicizzatore utilizza richieste AJAX per completare il processo complessivo in piccole parti per evitare problemi di timeout e memoria. L'indicizzazione è completa quando la barra di avanzamento scompare e la finestra modale si chiude.

### Indicizzazione dalla CLI

1. Apri una finestra di terminale.
2. Esegui `cd` nella cartella cli nella radice del tuo sito.
3. Usa il seguente comando:<br>
   php joomla.php finder:index
4. Quando l'indicizzatore ha terminato, vai alla pagina Contenuto Indicato di Smart Search dell'Amministratore.

## Contenuto Indicizzato

La pagina del Contenuto Indicizzato elenca tutti i contenuti indicizzati. Se preferisci che alcuni elementi specifici non vengano visualizzati nei risultati di ricerca, puoi rimuoverli dalla pubblicazione nel database di Smart Search selezionando la casella accanto al titolo dell'elemento e poi premendo il pulsante Rimuovi dalla pubblicazione.

**NOTA IMPORTANTE**: Se il tuo sito ha una grande quantità di contenuti, o elementi di contenuto particolarmente grandi, o ha spazio su disco limitato, dovresti leggere [Smart Search su siti di grandi dimensioni](jdocmanual?article=user/smart-search/smart-search-on-large-sites "Smart Search su siti di grandi dimensioni").

## Esposizione della Ricerca Intelligente agli Utenti del Sito

Ora che l'indice di Ricerca Intelligente è pronto, è necessario esporre la Ricerca Intelligente agli utenti del tuo sito web. La Ricerca Intelligente offre due modi per farlo:

### L'Interfaccia del Modulo

La Ricerca Intelligente include un modulo che può essere abilitato per visualizzare un semplice modulo di ricerca su qualsiasi pagina in quasi qualsiasi posizione. Per abilitare il modulo di Ricerca Intelligente, utilizza la seguente procedura:

1. Accedi all'Amministratore.
2. Seleziona la voce di menu Estensioni → Gestione Moduli.
3. Clicca sul pulsante Nuovo nella barra degli strumenti della Gestione Moduli.
4. Seleziona "Modulo Ricerca Intelligente" dall'elenco dei tipi di modulo mostrati.
5. Configura il modulo inserendo almeno un titolo, selezionando la posizione del modulo e regolando le pagine su cui deve essere visualizzato, se desiderato. Ulteriori opzioni di configurazione del modulo sono descritte nella schermata di aiuto del modulo Ricerca Intelligente.
6. Seleziona il pulsante Salva nella barra degli strumenti per pubblicare il modulo.

### L'Interfaccia della Voce di Menu

La Ricerca Intelligente può anche essere collegata tramite una voce di menu di Joomla così che gli utenti possano navigare direttamente al modulo principale di ricerca. Per creare un link di voce di menu alla Ricerca Intelligente, utilizza la seguente procedura:

1. Accedi all'Amministratore.
2. Seleziona la voce di menu Estensioni → Gestione Moduli.
3. Premi il pulsante Nuovo nella barra degli strumenti del Gestione Menu.
4. Clicca sul pulsante Seleziona accanto al campo Tipo Voce di Menu.
5. Seleziona "Ricerca" sotto la voce "Ricerca Intelligente" nell'elenco dei tipi di voce di menu mostrato.
6. Configura la voce di menu inserendo almeno un Titolo di Menu e regolando la voce principale, se desiderato.
7. Seleziona il pulsante Salva nella barra degli strumenti per pubblicare la voce di menu.

## Test, Test, Test

Per testare Smart Search, naviga verso uno degli elementi del menu che hai creato ed inserisci una ricerca nel modulo di ricerca o inserisci una ricerca in una delle istanze del modulo di Smart Search. Dovresti essere indirizzato a un elenco di risultati di ricerca se ne sono stati trovati per la parola o la frase inserita. Se non sono stati trovati risultati, verrà visualizzato un messaggio che indica che non sono stati trovati risultati. Se non sono stati trovati risultati e il sistema ha un suggerimento di ricerca basato sul tuo termine, la frase di ricerca suggerita verrà visualizzata sopra il messaggio che indica che non sono stati trovati risultati.

*Tradotto da openai.com*

