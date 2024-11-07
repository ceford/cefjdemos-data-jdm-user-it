<!-- Filename: Enabling_the_Login_Form_module / Display title: Modulo di Accesso  -->

## Metodi di Accesso al Sito

Ci sono due modi per permettere agli utenti registrati di accedere al frontend di un sito web. C'è un elemento di menu **Modulo di Accesso** che si trova nel gruppo di elementi di menu Utenti. È necessario impostare i suoi permessi di *Accesso* su *Ospite*. È necessario un secondo elemento di menu *Logout* con i suoi permessi di *Accesso* impostati su *Registrato*.

L'alternativa è il modulo **Modulo di Accesso**. È installato per impostazione predefinita nella posizione *sidebar-right* in una nuova installazione di Joomla. Questo modulo può essere spostato in un'altra posizione, non pubblicato, cestinato e cancellato. Le azioni successive si applicano a un'istanza del modulo e non al codice del modulo. È quindi possibile creare un nuovo modulo *Modulo di Accesso* o fare un duplicato, magari per l'uso in template diversi. Il modulo Modulo di Accesso cambia la sua visualizzazione dopo l'accesso per presentare un pulsante *Logout*.

## Il Modulo del Form di Login

Per pubblicare un modulo del Form di Login non pubblicato:

* Seleziona **Contenuto → Moduli del Sito** dal menu dell'Amministratore.
* Individua il modulo **Form di Login**.
* Se l'icona di **Stato** è una spunta verde all'interno di un cerchio, è già abilitato. Se l'icona di Stato è una croce grigia, è attualmente disabilitato. Seleziona l'icona per abilitare il modulo.
* Se il modulo *Form di Login* non è presente nell'elenco, imposta le Opzioni di Filtro, seleziona il campo - *Seleziona Stato* - su *Tutti* o *Cestinati* per vedere se è stato cestinato. In tal caso, può essere pubblicato selezionando la sua icona del cestino.
* Se il modulo del Form di Login manca, creane uno nuovo.

Per creare un nuovo Form di Login o un secondo Form di Login:

* Seleziona **Contenuto → Moduli del Sito** dal menu dell'Amministratore.
* Seleziona il pulsante **Nuovo** dalla Barra degli Strumenti.
* Dall'elenco dei Moduli, seleziona l'elemento **Login**.
* Compila il modulo di inserimento dati *Moduli: Login*.
  - Inserisci un Titolo univoco.
  - Seleziona una posizione nel template o crea una posizione denominata per l'uso in un articolo.
  - Compila gli altri campi come opportuno.
* **Salva & Chiudi**
* Verifica che il modulo appaia correttamente nel frontend del sito.

## Per assegnare il modulo di modulo di accesso a pagine web selezionate

Puoi far apparire il modulo di modulo di accesso su una o più pagine assegnandolo a Voci di Menù selezionate. Questo viene fatto utilizzando i campi nel gruppo di Assegnazione Menù nella schermata di Modifica Modulo:

- Seleziona la scheda **Assegnazione Menù**.
- L'elenco **Assegnazione Modulo** ha quattro opzioni:
  - **Su tutte le pagine**: Il modulo di modulo di accesso apparirà su tutte le pagine.
  - **Nessuna pagina**: Il modulo di modulo di accesso non apparirà su nessuna pagina.
  - **Solo sulle pagine selezionate**: Apparirà un elenco di tutti i menù e le voci di menù sul tuo sito. Il modulo di modulo di accesso apparirà sulle pagine selezionate in questo elenco.
  - **Su tutte le pagine tranne quelle selezionate:** Il modulo di accesso apparirà su tutte le pagine non selezionate.
- **Selezione Menù**: Mostra un elenco di tutti i Menù e Voci di Menù dai quali è possibile selezionare uno o più elementi. Questo campo è utilizzato solo se il campo **Menù** è impostato su **Seleziona Voci di Menù dall'elenco**.

  ![assegnazione menù del modulo](../../../en/images/modules/modules-login-menu-assignment.png)

## Personalizzare il modulo di accesso

Se desideri modificare l'aspetto del modulo di accesso, puoi aggiungere stili, sia stili Bootstrap che stili personalizzati definiti nel tuo file user.css del template. Aggiungi gli stili nella scheda **Avanzate** del modulo: modifica accesso.

Se desideri modificare le informazioni mostrate nel modulo di accesso, puoi creare un override del template. Consulta la sezione su
[Template Overrides](jdocmanual?article=user/templates/template-overrides)
per ulteriori dettagli.

*Tradotto da openai.com*

