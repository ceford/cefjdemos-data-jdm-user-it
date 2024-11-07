<!-- Filename: J4.x:Administrator_Modules / Display title: Moduli Amministratore   -->

## Introduzione

Il modello Amministratore di Atum è fornito con un set completo di
moduli Amministratore installati e configurati per l'uso quotidiano. L'illustrazione seguente mostra le posizioni della Dashboard Home per indicare
dove si trovano i moduli.

![posizioni dashboard home di atum](../../../en/images/modules/atum-template-positions.png)

Nell'illustrazione sopra, i pannelli sono istanze del modulo Icona Rapida
collegato ai plugin di icona rapida.

### Note su alcune posizioni dei moduli

- **Custom Top** è sopra il banner ed è utile se si desidera
  pubblicare un menu personalizzato o un modulo personalizzato contenente un messaggio importante. Ad esempio, per avvertire gli amministratori che il sito chiuderà
  a breve per la manutenzione del sistema.
- **Status** è per le icone mostrate allineate a destra nel Banner.
- **Menu** si trova nella barra laterale sinistra dello schermo Atum.
- **Toolbar** è sopra l'area del contenuto principale nei schermate di lista e modifica
  ma non è presente nelle schermate della dashboard.
- **Top** è sotto la Barra degli Strumenti ma sopra qualsiasi Messaggio di Sistema e
  contenuto del componente.
- **Bottom** è sotto il contenuto del componente.
- **Debug** è sotto tutto.

Posizioni del modello Atum per nome

```xml
  <positions>
    <!-- usato direttamente nel modello -->
    <position>bottom</position>
    <position>cpanel</position>
    <position>customtop</position>
    <position>debug</position>
    <position>icon</position>
    <position>login</position>
    <position>menu</position>
    <position>sidebar</position>
    <position>status</position>
    <position>title</position>
    <position>toolbar</position>
    <position>top</position>
  </positions>
```

## Aggiungi un Modulo Personalizzato

Potresti voler aggiungere un modulo personalizzato per avvisare gli amministratori di qualche problema del sistema. Seleziona **Contenuto → Moduli Amministratore** dal menu Amministratore. La lista dei moduli installati è piuttosto lunga:

![lista moduli admin atum](../../../en/images/modules/atum-admin-modules-list.png)

Seleziona il pulsante Nuovo e poi il modulo Personalizzato. Nel modulo di modifica Moduli: Personalizzato inserisci un Titolo, un messaggio Personalizzato e seleziona una Posizione per il modulo. Nell'esempio sotto è stata selezionata la posizione in alto. Inoltre, nel campo Classe Modulo della scheda Avanzato, sono stati inseriti alcuni stili per centrare il testo e fornire un po' di margine: **alert alert-warning text-center**. Salva per vedere il risultato. Chiudi per vedere il risultato nella pagina dell'elenco dei moduli.

![modulo sistema messaggio personalizzato atum](../../../en/images/modules/atum-admin-module-system-message.png)

Quando hai finito con il messaggio, puoi semplicemente selezionare il pulsante Stato nell'elenco dei moduli per non pubblicare il modulo.  

## Elenco dei Moduli Amministratore

- **Log delle Azioni - Ultimi** Questo modulo mostra un elenco delle azioni più recenti.
- **Menu Dashboard Amministratore** Questo modulo visualizza un sottomenu per amministratori.
- **Menu Amministratore** Questo modulo visualizza un modulo di menu per amministratori.
- **Articoli - Ultimi** Questo modulo mostra un elenco degli articoli creati più di recente.
- **Personalizzato** Questo modulo ti consente di creare il tuo modulo usando un editor WYSIWYG.
- **Visualizzazione Feed** Questo modulo consente di visualizzare un feed sindacato.
- **Collegamento Frontend** Questo modulo mostra un link al frontend ed è destinato ad essere visualizzato nella posizione 'stato'.
- **Informazioni sulla Versione di Joomla!** Questo modulo visualizza la versione di Joomla! ed è destinato ad essere visualizzato nella posizione 'stato'.
- **Utenti Connessi** Questo modulo mostra un elenco degli utenti connessi.
- **Modulo di Login** Questo modulo visualizza un modulo di login con nome utente e password. Non dovrebbe essere disattivato.
- **Informazioni di Supporto per il Login** Questo modulo visualizza alcuni link utili ai siti di supporto Joomla sulla schermata di login.
- **Messaggi** Questo modulo mostra il conteggio dei messaggi privati ed è destinato ad essere visualizzato nella posizione 'stato'. Viene visualizzato solo quando ci sono messaggi da leggere.
- **Stato Multilingue** Questo modulo mostra lo stato dei parametri multilingue ed è destinato ad essere visualizzato nella posizione 'stato'.
- **Articoli Popolari** Questo modulo mostra un elenco degli articoli più popolari pubblicati che sono ancora attuali. Alcuni di quelli mostrati potrebbero essere scaduti anche se sono i più recenti.
- **Messaggi post installazione** Questo modulo mostra un contatore e un link ai messaggi post installazione più recenti. Viene visualizzato solo quando ci sono messaggi da leggere.
- **Dashboard della Privacy** Il modulo Dashboard della Privacy mostra informazioni sulle richieste di privacy.
- **Controllo dello Stato della Privacy** Il modulo Controllo dello Stato della Privacy mostra informazioni sullo stato della privacy dei tuoi siti.
- **Icone Rapide** Questo modulo mostra Icone Rapide che sono visibili nella Home Dashboard (pagina iniziale dell'area amministratore)
- **Dati di Esempio** Questo modulo ti permette di installare dati di esempio.
- **Statistiche** Il modulo Statistiche mostra informazioni sulla tua installazione del server insieme alle statistiche sugli utenti del sito e il numero di articoli nel tuo database.
- **Titolo** Questo modulo mostra il Titolo del Componente della Barra degli Strumenti.
- **Barra degli Strumenti** Questo modulo mostra le icone della barra degli strumenti utilizzate per controllare le azioni in tutta l'area Amministratore.
- **Menu Utente** Questo modulo mostra il Menu Utente ed è destinato ad essere visualizzato nella posizione 'stato'.

