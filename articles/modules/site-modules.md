<!-- Filename: J4.x:Site_Modules / Display title: Moduli del Sito -->

## Introduzione

I moduli sono estensioni leggere e flessibili utilizzate per visualizzare frammenti di informazioni in **box** disposti intorno a un componente su una pagina. Un esempio ben noto è il modulo di login. I moduli vengono assegnati per voce di menu, quindi puoi decidere di mostrare o nascondere un modulo a seconda di quale pagina l'utente sta visualizzando.

Alcuni moduli sono collegati ai componenti. Ad esempio, il modulo **ultime notizie** è collegato al componente di contenuto per visualizzare i link agli articoli più recenti. I moduli non necessitano di essere collegati ai componenti. Non devono nemmeno essere collegati a nulla e possono essere semplicemente HTML statico o testo.

Possono esserci più istanze dello stesso modulo. Ad esempio, puoi utilizzare un'istanza del modulo Immagine Casuale per alcune pagine e un'altra istanza per altre pagine, ciascuna utilizzando una cartella di immagini diversa da cui selezionare le immagini.

## Posizioni dei Moduli

I moduli sono assegnati a una posizione su una pagina definita dal modello in uso. La seguente illustrazione mostra un layout schematico del modello Cassiopeia:

![Diagramma delle posizioni del modello Cassiopeia](../../../en/images/modules/cassiopeia-template-positions.png)

E la seguente lista mostra le posizioni dei moduli disponibili per nome:

```xml
    <positions>
        <position>topbar</position>
        <position>sotto-top</position>
        <position>menu</position>
        <position>ricerca</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>principale-top</position>
        <position>principale-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-sinistra</position>
        <position>sidebar-destra</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
```

## Aggiungere un Modulo Core

I moduli core sono quelli forniti con una nuova installazione di Joomla. Ci sono migliaia di moduli aggiuntivi disponibili da fornitori terzi. Supponiamo che desideri mostrare un'immagine casuale per rendere il tuo sito più interessante per i visitatori. Dal menu dell'Amministratore seleziona **Contenuto → Moduli del Sito** per vedere l'elenco dei moduli del sito già in uso:

![Elenco Moduli del Sito](../../../en/images/modules/cassiopeia-modules-list.png)

Seleziona il pulsante Nuovo per vedere un elenco dei moduli del sito disponibili per l'installazione:

![Moduli del Sito disponibili](../../../en/images/modules/cassiopeia-modules-available.png)

Scorri verso il basso e seleziona il modulo Immagine Casuale. Si aprirà il modulo di modifica **Moduli: Immagine Casuale** pronto per essere compilato.

![Modulo immagine casuale](../../../en/images/modules/cassiopeia-module-random-image.png)

- **Titolo** Questo è un campo obbligatorio.
- **Tipo Immagine** Il predefinito è jpg.
- **Cartella Immagini** Inserisci un percorso a una cartella che contenga effettivamente immagini del tipo che hai selezionato.
- **Link** Un URL a cui reindirizzare se l'immagine viene selezionata.
- **Larghezza** Forza tutte le immagini a essere visualizzate con questa larghezza in pixel.
- **Altezza** Lascia vuoto per mantenere il rapporto d'aspetto dell'immagine.
- **Posizione** Seleziona una posizione modulo affinché il modulo appaia effettivamente su una pagina. Nell'illustrazione, è stato selezionato sidebar-right.
- **Salva & Chiudi** Oppure usa il pulsante Aiuto nella barra degli strumenti per scoprire cosa fanno gli altri campi.

## Ordine dei Moduli

Dopo aver salvato, potresti dover cambiare l'ordine dei moduli nella posizione scelta. Procedi come segue:

- Nella lista dei Moduli, seleziona l'icona Ordine della Colonna nell'intestazione della tabella dei moduli, è un triangolo combinato su/giù. Questo ordinerà la tabella e mostrerà i simboli di presa degli elementi, un'ellissi verticale. Selezionala di nuovo per invertire l'ordine di ordinamento! Il simbolo di ordinamento della colonna cambia: triangolo in su per indicare l'ordine di ordinamento normale, triangolo in giù per indicare l'ordine di ordinamento inverso.
- Prendi e trascina l'ellissi di Immagine Casuale per spostarla verso l'alto o verso il basso. Rilascia quando è nella tua posizione preferita.

## Visualizza il Sito

![Visualizzazione del sito del modulo immagine casuale](../../../en/images/modules/cassiopeia-module-random-image-site.png)

Controlla l'aspetto del Sito. In questo caso, potrebbe essere una buona idea centrare l'immagine. Può essere fatto nel seguente modo:

- Torna al modulo di modifica e seleziona la scheda Avanzate.
- Nel campo Classe Modulo inserisci text-center e Salva.
- Visualizza il risultato ricaricando la pagina del Sito.

Tutto fatto?

## Elenco dei Moduli Principali

- **Articoli - Archiviati** Questo modulo mostra un elenco dei mesi del calendario contenenti Articoli Archiviati. Dopo aver modificato lo stato di un Articolo in Archiviato, questo elenco verrà generato automaticamente.
- **Articoli - Categorie** Questo modulo mostra un elenco di categorie da una categoria madre.
- **Articoli - Categoria** Questo modulo mostra un elenco di articoli provenienti da una o più categorie.
- **Articoli - Ultimi** Questo modulo mostra un elenco degli Articoli più recentemente pubblicati e correnti.
- **Articoli - Più letti** Questo modulo mostra un elenco degli Articoli pubblicati che hanno il maggior numero di visualizzazioni.
- **Articoli - Flash di notizie** Il Modulo Flash di notizie mostrerà un numero fisso di articoli da una categoria specifica.
- **Articoli - Correlati** Questo modulo mostra altri Articoli che sono correlati a quello in visualizzazione. Queste relazioni sono stabilite dalle Parole Chiave. Tutte le parole chiave dell'Articolo corrente vengono cercate in relazione a tutte le...
- **Banners** Il Modulo Banner visualizza i Banner attivi dal Componente.
- **Breadcrumbs** Questo modulo mostra i Breadcrumbs.
- **Personalizzato** Questo modulo ti permette di creare il tuo Modulo utilizzando un editor WYSIWYG.
- **Visualizzazione Feed** Questo modulo consente la visualizzazione di un feed sindacato.
- **Footer** Questo modulo mostra le informazioni sul copyright di Joomla!.
- **Selettore di Lingua** Questo modulo mostra un selettore di lingua sul tuo sito web delle lingue dei contenuti disponibili.
- **Ultimi utenti** Questo modulo mostra gli ultimi utenti registrati.
- **Login** Questo modulo visualizza un modulo di accesso con nome utente e password. Mostra anche un link per recuperare una password dimenticata. Se la registrazione degli utenti è abilitata (in Utenti → Gestisci → Opzioni),...
- **Menu** Questo modulo visualizza un menu nel Frontend.
- **Immagine casuale** Questo modulo visualizza un'immagine casuale dalla cartella scelta.
- **Ricerca Intelligente** Questo è un modulo di ricerca per il sistema di Ricerca Intelligente.
- **Statistiche** Il Modulo Statistiche mostra informazioni sull'installazione del tuo server insieme a statistiche sugli utenti del sito web e sul numero di Articoli nel tuo database.
- **Feed di Sincronizzazione** Modulo di Sincronizzazione Intelligente che crea un Feed Sincronizzato per la pagina in cui il Modulo è visualizzato.
- **Tag - Popolari** Questo modulo visualizza i tag utilizzati sul sito in un elenco o in un layout a nuvola. I tag possono essere ordinati per titolo o per numero di elementi taggati e limitati a un periodo di tempo specifico.
- **Tag - Simili** Il Modulo Tag Simili mostra link ad altri elementi con tag simili. È possibile specificare la vicinanza della corrispondenza.
- **Chi è online** Il Modulo Chi è online visualizza il numero di Utenti Anonimi (Ospiti) e Utenti Registrati (utenti connessi) che stanno attualmente accedendo al sito web.
- **Wrapper** Questo modulo mostra una finestra iframe verso una posizione specificata.
