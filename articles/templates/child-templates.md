<!-- Filename: J4.x:Child_Templates / Display title: Template Figli -->

## Introduzione

I template figlio utilizzano tutti i file dei loro template genitore, ad eccezione di qualsiasi file con lo stesso nome che inserisci nel template figlio. I file del template figlio non sono influenzati dagli aggiornamenti di Joomla. Quindi potresti inserire il tuo file index.php in un template figlio e far sì che esso fornisca qualcosa di molto diverso dal template predefinito, come posizioni di modulo aggiuntive o sovrascritture alternative delle estensioni.

Uno scenario esempio: supponiamo che tu voglia che alcune delle tue pagine appaiano con un tema blu, i colori predefiniti di Cassiopeia, e altre pagine appaiano con un tema verde. Un modo semplice per fare ciò è con un template figlio che utilizza il proprio foglio di stile user.css.

## Esempio Lavorato

A partire da **Sistema → Pannello Modelli → Modelli del Sito**

- Seleziona *Dettagli e File di Cassiopeia*.
- Seleziona il pulsante *Crea Modello Figlio*.
- Compila il popup di dialogo del Modello Figlio e seleziona il pulsante Crea Modello Figlio:

![modulo di creazione modello figlio](../../../en/images/templates/child-templates-create-green.png)

La selezione di Cassiopeia - Default nel campo Stili di Modello Aggiuntivi sembra superflua (è un bug?).

- Seleziona *Chiudi* dalla Toolbar per chiudere il modulo del modello padre.
- Seleziona il nuovo modello, *Dettagli e File Cassiopeia_green*, dall'elenco dei Modelli.

A questo punto c'è una struttura di cartelle ma solo un file: templateDetails.xml. Quel file può essere modificato se desideri cambiare aspetti della configurazione del modello, ad esempio posizioni del modello da aggiungere o rimuovere.

### Crea un file user.css

- Seleziona il pulsante *Nuovo File* nella Toolbar.
- Nel modulo *Crea o Carica un nuovo file* assicurati di selezionare la cartella `css`
- Compila il nome del file con `user`. NON aggiungere un suffisso!
- Seleziona il Tipo di File `.css`.
- Seleziona il pulsante *Crea*.

![form creazione user css del modello figlio](../../../en/images/templates/child-templates-create-green-user-css.png)

Il file user.css è vuoto, pronto per inserire alcuni stili personalizzati. Inserisci il seguente codice per iniziare il tema verde:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
    a, a:hover, a:focus {
      color: darkgreen;
    }
    .btn-info {
        background-color: darkgreen;
        border-color: #30638d;
        color: #fff;
    }
    .btn-primary, .btn-primary:focus, .btn-primary:hover {
        background-color: darkgreen;
        border-color: var(--cassiopeia-color-hover);
    }

    .btn-check:focus + .btn-info, .btn-info:focus, .btn-info:hover {
        background-color: darkgreen;
        border-color: #264f71;
        color: #fff;
    }
```
Potrebbe essere necessario tornare a questo file user.css per aggiungere ulteriori stili in seguito.

- Seleziona *Salva e Chiudi* oppure, separatamente, *Salva* e quindi *Chiudi File*.
- Seleziona *Chiudi* per chiudere il modulo Personalizza.

### Elemento del Menu

A questo punto è necessario un elemento del menu per utilizzare il modello figlio. Una nuova installazione di Joomla 4 ha il Menu Principale nella posizione della barra laterale destra con un elemento al suo interno. Sembrano adatti per un nuovo elemento del menu.

- Seleziona **Menu → Menu Principale** dal menu dell'Amministratore.
- Seleziona il pulsante *Nuovo* dalla Toolbar.
- Inserisci un titolo adatto, *Articoli in Primo Piano Verdi* sembra appropriato in questo caso.
- Seleziona il pulsante **Tipo di Voce del Menu → Seleziona**.
- Seleziona un tipo di voce del menu dalla finestra di dialogo popup Tipo di Voce del Menu - Articoli in Primo Piano in questo esempio.
- Seleziona *cassiopeia_manual - Default* dal campo modulo Stile del Modello.

![modulo di modifica dell'elemento del menu del modello figlio](../../../en/images/templates/child-templates-create-green-menu-item.png)

- Ai fini della seguente schermata, il Layout del Blog è stato impostato su Articoli in Primo Piano: 0, Articoli di Introduzione: 3 e Direzione Multicolonna: Orizzontale.

### Vista Sito

- nella pagina Home del tuo sito seleziona il nuovo elemento del menu creato.

![sito che mostra il modello di tema verde personalizzato](../../../en/images/templates/child-templates-green-site-result.png)

### Modifica lo Stile

- Seleziona **Sistema → Pannello Modelli → Stili dei Modelli del Sito** dal menu dell'Amministratore.
- Seleziona *Cassiopeia_green - Default* dall'elenco degli Stili.
- Cambia il Nome dello Stile in *Cassiopeia Verde*. Questo semplicemente riordina il nome come appare negli elenchi.
- Seleziona *Salva e Chiudi*.

