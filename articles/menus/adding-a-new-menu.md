<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Aggiunta di un nuovo menu  -->

## Introduzione

Affinché i contenuti siano accessibili sul tuo sito Joomla!, gli elementi devono essere assegnati a un Menu. Un'installazione standard di Joomla! crea un **Menu Principale** per te. In molti casi, utilizzerai solo un menu, ma puoi averne più di uno. Questo ti permette di creare Menu per diversi tipi di contenuto, contenuti nascosti, contenuti specifici per ruolo utente e altro ancora.

Ci sono tre passaggi nella creazione di un menu utilizzabile:

1. Creare il Menu. Questo è un contenitore per gli Elementi del Menu.
2. Creare un Modulo del Menu. Questo permette il posizionamento del Menu su una pagina.
3. Creare gli Elementi del Menu. Questi sono gli elementi selezionabili dagli utenti che portano a pagine specifiche.

Questo screenshot mostra i menu disponibili in un sito Multilingue. In un'installazione iniziale di Joomla, c'è un unico *Menu Principale*.

![Elenco dei menu](../../../en/images/menus/menus-manage.png "Elenco dei menu")

L'elenco ti consente di selezionare uno qualsiasi dei pulsanti verdi o rossi per andare direttamente all'elenco degli elementi del menu in quel menu e stato.

Questo tutorial copre i passaggi coinvolti nella creazione di un Menu su un sito Joomla!.

## Creare un Nuovo Menu

Usa uno dei seguenti passaggi per creare un nuovo menu:

- Dal menu Amministratore seleziona l'icona *Dashboard Menu* per accedere alla dashboard dei menu, quindi seleziona **Gestisci**. Oppure...
- Dal menu Amministratore espandi la sezione *Menu* e poi seleziona **Gestisci**.
- Seleziona il pulsante **+ Nuovo** nella barra degli strumenti.
- Nel modulo di inserimento dati del menu completa i seguenti campi:
  - **Titolo**: Un titolo appropriato per il menu. Questo è usato per identificare il menu nel Gestore Menu.
  - **Nome Unico**: Questo dovrebbe essere un nome di identificazione unico usato da Joomla! per identificare questo menu. Gli spazi non sono consentiti, ma puoi usare il carattere '-' come in resources-menu.
  - **Descrizione**: Anche se non è richiesta, è spesso utile in un sito con molti menu. Appare sotto il *Titolo* nell'elenco dei menu come illustrato sopra.<br>
    ![Nuovo Menu](../../../en/images/menus/menus-new.png "Nuovo Menu")
- **Salva & Chiudi**

Nell'elenco dei Menu il menu appena creato ha un pulsante etichettato **Aggiungi un modulo per questo menu**, che rappresenta la fase successiva nella creazione del menu. Potresti iniziare ad aggiungere le voci di menu e tornare a creare il modulo del menu in seguito.

## Creare un Modulo per il Menu

Nell'elenco dei Menu, la colonna *Moduli Collegati* consente di selezionare qualsiasi modulo menu esistente a scopo di modifica. Puoi dare un'occhiata e poi *Chiudere* senza apportare alcuna modifica. Per il tuo nuovo menu, seleziona il pulsante **Aggiungi un modulo per questo menu** per aprire un riquadro modale contenente il modulo di inserimento dati del Modulo Menu.

![Modulo di inserimento dati del Modulo Menu](../../../en/images/menus/menus-module.png "Modulo di inserimento dati del Modulo Menu")

Campi da completare:

* Il campo **Titolo** è obbligatorio, quindi crea un titolo descrittivo.
* Il pulsante **Mostra Titolo** sulla destra viene utilizzato per *Mostrare* o *Nascondere* il titolo del modulo, una funzione comune a tutti i moduli.
* Il campo **Seleziona Menu** dovrebbe mostrare il nome del Menu che hai appena creato.
* Il campo **Posizione** viene utilizzato per selezionare una posizione nel tuo template dove vuoi che appaia il tuo menu.
* Seleziona **Salva & Chiudi** una volta che le informazioni essenziali sono state aggiunte.

Ci sono molte opzioni tra cui scegliere nel modulo *Impostazioni di modifica del modulo*. Sono menzionate nella schermata di Aiuto disponibile nel modulo *Modulo: Modifica*. Questo è lo stesso modulo ma in una pagina normale piuttosto che in un riquadro modale. Accedici attraverso il menu Amministratore, percorso Contenuto / Moduli Sito per la lista dei Moduli Sito.

Nota: ottenere che il Menu appaia come desideri dipende dallo stile del tuo template.

## Aggiungere Elementi al Menu

Per creare i collegamenti nel tuo menu, è necessario aggiungere **Elementi del Menu**. In Joomla esistono molti tipi di *Tipi di Elementi del Menu* e i componenti di terze parti possono aggiungerne di nuovi. In questo tutorial verrà aggiunto un collegamento a un singolo articolo.

Puoi creare un articolo in anticipo oppure puoi crearne uno durante il processo di creazione del menu. In entrambi i casi, l'articolo deve esistere prima che un elemento del menu possa essere creato per esso. In questo esempio, l'articolo sarà anche chiamato *Risorse*. È destinato a contenere un elenco di collegamenti a file PDF.

Nell'elenco **Menu**, dalla colonna **Elementi del Menu** seleziona l'icona per il menu appena creato, *Risorse* in questo esempio. Inizialmente, non ci sono elementi nel menu, quindi l'elenco dirà semplicemente *Nessun Risultato Trovato*.

- Seleziona il pulsante **Nuovo** dalla Barra degli Strumenti per creare un nuovo elemento del menu.
- Nel campo **Titolo** aggiungi il titolo che vuoi appare nel Menu.
- Nel campo **Tipo di Elemento del Menu** seleziona il pulsante **Seleziona** per aprire una finestra modale contenente un elenco di componenti. Ognuno ha un elenco a discesa che rivela un elenco di tipi di elementi del menu disponibili.
  - Seleziona **Articoli** quindi **Singolo Articolo**.
- Nel campo **Seleziona Articolo**: **Sia:**
  - Usa il pulsante **Seleziona** per selezionare un articolo esistente. Si aprirà un elenco di articoli tra cui scegliere. **Oppure:**
  - Usa il pulsante **Crea** per creare un nuovo articolo. Tutto ciò che devi inserire è il titolo dell'articolo. È probabilmente meglio lasciare i contenuti dettagliati per dopo.
- Controlla che il campo **Menu** sia impostato sul nuovo Menu.
- Il campo **Stato** dovrebbe essere impostato su **Pubblicato**.
- Seleziona **Salva & Chiudi**.

![Modulo di inserimento dati dell'elemento del menu](../../../en/images/menus/menus-single-article.png "Modulo di inserimento dati dell'elemento del menu")

Aggiungi altri Elementi del Menu al nuovo Menu secondo necessità.

Una volta che gli elementi sono stati aggiunti al Menu, controlla che il Menu sia visualizzato sul sito web nella posizione corretta.

![Visualizzazione del menu](../../../en/images/menus/menus-display.png "Visualizzazione del menu")

*Tradotto da openai.com*

