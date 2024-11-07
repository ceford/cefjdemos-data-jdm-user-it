<!-- Filename: Keyboard_Shortcuts / Display title: Scorciatoie da Tastiera  -->

## Introduzione

La tastiera può essere utilizzata nell'interfaccia amministrativa per richiamare alcune delle azioni solitamente eseguite con un mouse o un pad. Ad esempio, ci sono scorciatoie da tastiera per salvare la pagina corrente, andare alla *Dashboard principale* o aprire un modulo di *Opzioni*.

C'è una panoramica di tutte le scorciatoie, aperta dalla selezione sequenziale dei tasti **J** e **X** (non contemporaneamente e senza utilizzare il tasto Shift generalmente usato per le maiuscole). A meno che non si cambino le impostazioni del plugin, è necessario premere i tasti entro 2 secondi.

La funzione è abilitata per impostazione predefinita. Può essere disabilitata o configurata sotto **Amministratore → Sistema → Plugin → Sistema - Scorciatoie da Tastiera**. Attualmente l'unica configurazione disponibile è il timeout: per quanto tempo il sistema attende il prossimo input di tasti. Per impostazione predefinita, attende 2000 millisecondi (2 secondi).

## Scorciatoie predefinite in Joomla

- J + A - Salva il contenuto corrente
- J + S - Salva e chiudi
- J + Q - Annulla la pagina corrente
- J + N - Premere il pulsante *Nuovo*
- J + F - Imposta il focus sul campo di ricerca
- J + O - Vai alle opzioni
- J + H - Si apre la finestra di aiuto (potrebbe attivare un avviso di pop-up del browser)
- J + M - Attiva/disattiva la barra dei menu
- J + X - Mostra un elenco di scorciatoie disponibili
- J + D - Vai direttamente alla Home Dashboard

## Scorciatoie di Terze Parti - Informazioni per Sviluppatori

Altri sviluppatori possono aggiungere le proprie scorciatoie. Il plugin Joomla chiama l'Evento *onLoadShortcuts*, che può essere utilizzato anche da altri plugin. L'evento deve essere aggiunto alla lista di *getSubscribedEvents* all'interno del plugin. La funzione assegnata potrebbe apparire così:

```php
public function onLoadShortcuts(EventInterface $event): void {
   $shortcuts = $event->getArgument('shortcuts');
   $exampleShortcuts = array('example' => (object)['shortcut' => 'E', 'title' => 'Grande Esempio', 'selector' => '#menu-collapse']);
   $event->setArgument('shortcuts',  array_merge($shortcuts, $exampleShortcuts));
}
```

Presta attenzione alla parte di array_merge: se le scorciatoie già esistenti non vengono unite con quelle nuove, le vecchie vengono sovrascritte.

Gli sviluppatori possono fornire un array con oggetti scorciatoia:

    { shortcut: stringa, selector: stringa, title: stringa }

- La *Scorciatoia* deve essere un input da tastiera, separato da un più, ad es. `Y` o `ALT + Z + 7` (attualmente non c'è davvero nessun filtraggio). Tieni presente che ogni sequenza di scorciatoia inizierà con **J**.
- I *Selettori* sono selettori CSS o URL per specificare il target. Quando si tratta di un elemento di input, la scorciatoia dà il focus come avviene per il campo di ricerca. Altrimenti l'elemento verrà cliccato o verrà chiamato l'URL.
- Il *Titolo* verrà visualizzato nella panoramica. Potrebbe essere ad esempio il nome del target.

## Motivi per l'utilizzo di J + X

Alcuni potrebbero chiedersi perché si sia deciso di utilizzare scorciatoie sequenziali o la **J** come inizio invece di Ctrl o qualcos'altro. I motivi principali sono l'accessibilità e l'evitare interruzioni da parte di altri software. Ad esempio, *Ctrl + S* sarebbe comodo per salvare un articolo, ma è già utilizzato dai browser. Lo stesso può accadere per gli screen reader o i gestori di password. Quindi l'opzione più sicura era utilizzare qualcosa di specifico per Joomla come la **J** all'inizio.

Un altro problema è che non è sempre possibile premere più di un tasto alla volta. Windows ha la modalità Sticky Key per questo, ma funziona solo per tasti modificatori come Shift, Ctrl e Alt. Quindi il plugin utilizza l'input sequenziale fin dall'inizio, rendendolo utilizzabile da più persone anche senza l'aiuto delle modalità del sistema operativo.

*Tradotto da openai.com*

