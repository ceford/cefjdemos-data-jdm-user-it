<!-- Filename: J4.x:How_to_Show_a_Calendar_Month_List_of_Archived_Articles_Using_a_Module / Display title: Articoli Archiviati  -->

## Introduzione

Archiviare gli articoli è uno dei modi in cui Joomla! aiuta a gestire gli articoli di un sito web, poiché contribuisce a ridurre il disordine nel backend. Ma quali visitatori del sito dovrebbero essere in grado di accedere agli articoli archiviati?

Un modo per farlo è mostrare un elenco mensile di articoli archiviati utilizzando uno dei Moduli core di Joomla. In questo esempio, un **Modulo Articoli Archiviati** sarà impostato per essere visualizzato nella barra laterale del sito web.  

## Creare il Modulo *Articoli - Archiviati*

Usa uno dei seguenti metodi:
* Seleziona l'elemento **Moduli** dalla Dashboard principale. Oppure...
* Seleziona **Contenuti / Moduli del sito** dal menu dell'Amministratore.
* Seleziona l'elemento **Articoli Archiviati** dalla lista dei Moduli (Sito).

Questo creerà il nuovo modulo e aprirà il modulo per la configurazione.

## Configurazione del Modulo

Per l'uso standard del modulo sono richieste solo alcune impostazioni:

- **Titolo** Inserisci un nome per il modulo.
- **\# di Mesi** Imposta il numero di mesi che desideri visualizzare. Questi
appariranno come link sul frontend. Puoi impostarli utilizzando le frecce su/giù oppure
inserendo direttamente un numero nel campo.
- **Mostra/Nascondi Titolo** Scegli se mostrare o meno il titolo attivando/disattivando
l'opzione *Mostra* o *Nascondi*.
- **Posizione** Imposta una posizione dove desideri visualizzare il modulo sul
frontend. Le posizioni sono dettate dal tuo template. Questo esempio utilizza la
posizione *Barra Laterale Destra* del template Cassiopeia di Joomla.
- **Stato** Di default, lo stato del modulo è **Pubblicato**. Altre opzioni sono
**Non Pubblicato** e **Cestinato**.
- **Inizio Pubblicazione** Puoi programmare l'inizio della pubblicazione del
modulo.
- **Fine Pubblicazione** Puoi programmare quando interrompere la pubblicazione del
modulo.
- **Accesso** Se desideri controllare chi può vedere il modulo sul
frontend, puoi scegliere un livello di accesso.
- **Ordinamento** Usato per controllare dove il modulo è visualizzato all'interno
della posizione che hai selezionato. Ad esempio, potresti avere un numero di
moduli nella barra laterale e voler che questo sia in cima o in fondo – o
da qualche parte tra gli altri nella barra laterale. All'inizio può essere un po' confuso poiché 
il campo mostra una posizione numerata e un nome di modulo. Il nome
può essere un modulo non pubblicato. È importante ricordare che il
numero più basso sarà in cima e il numero più alto sarà in fondo.
- **Nota** Può essere utile utilizzare il campo delle note se, ad esempio, stai
utilizzando lo stesso tipo di modulo in diversi posti.

### Tab Assegnazione Menu

Di default, il modulo sarà pubblicato **Su tutte le pagine**.

In alternativa, puoi scegliere tramite un elenco a discesa **Nessuna pagina**, **Solo
sulle pagine selezionate** o **Su tutte le pagine tranne quelle selezionate**. Le
ultime due opzioni ti forniscono un albero di menu con i menu utilizzati sul
sito web dove puoi selezionare/deselezionare le pagine.

### Altre Impostazioni

La scheda **Avanzate** ha impostazioni relative al layout del modulo quando viene
visualizzato.

La scheda **Permessi** ti permette di controllare cosa i gruppi di utenti possono fare con
il modulo.

## Pubblicazione del Modulo

Quando sei pronto, seleziona il pulsante **Salva e Chiudi**.

Il modulo verrà pubblicato nella barra laterale del sito web e mostrerà un elenco di link determinato dal numero di mesi da visualizzare impostato nel modulo.

![Esempio di Modulo Articoli Archiviati](../../../en/images/modules/modules-archived-articles.png "Esempio di Modulo Articoli Archiviati")

## Suggerimenti

Più articoli archiviati hai, maggiore sarà il numero di link visualizzati dal modulo. Potrebbe essere più appropriato limitare il numero di link utilizzando categorie oppure puoi usare più moduli di Articoli Archiviati denominati di conseguenza.

*Tradotto da openai.com*

