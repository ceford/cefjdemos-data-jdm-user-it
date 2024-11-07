<!-- Filename: J4.x:Switching_Templates / Display title: Modifica dei modelli   -->

## Template del sito e dell'amministratore

Joomla 4 viene fornito con un unico template del sito, Cassiopeia, e un unico template dell'amministratore, Atum. Puoi ottenere template aggiuntivi dai fornitori di template di terze parti, sia gratuiti che a pagamento, e puoi creare i tuoi template, più facilmente come template child.

È improbabile che tu voglia utilizzare un template dell'amministratore alternativo, quindi questo articolo copre solo i template alternativi del sito. A scopo illustrativo, è stato creato un template child con un tema verde come descritto nell'articolo sui template child. Inoltre, il sito utilizzato per l'illustrazione ha installato i dati di esempio per il test.

## Stile del Modello Predefinito

Uno dei tuoi modelli deve essere contrassegnato come predefinito. Viene utilizzato per tutte le pagine ad eccezione delle singole pagine che specificano un modello alternativo. Per impostare il modello predefinito:

- Seleziona **Sistema → Pannello Modelli → Stili Modello del Sito** dal menu Amministratore.
- Seleziona uno dei pulsanti nella colonna Predefinito.

![pagina elenco stili modelli sito](../../../en/images/templates/switch-templates-styles-list.png)

Dai un'occhiata al tuo sito per vedere che tutte le pagine stanno utilizzando il modello predefinito.

## Utilizzo di uno Stile Alternativo

Joomla consente di selezionare uno stile per una pagina specifica tramite l'assegnazione del menu. La selezione può essere effettuata dal modulo Stile del Template o dal modulo di modifica del Menu. I metodi producono lo stesso risultato. Il primo metodo è più conveniente per la selezione di un gruppo di voci di menu appartenenti allo stesso menu.

### Metodo di Assegnazione del Menu al Template

Dalla lista Stili dei Template:

- Seleziona uno stile che **non** sia impostato come predefinito. La stella gialla indica lo stile predefinito.
- Seleziona la scheda Assegnazione Menu.
- Seleziona singole voci di menu o attiva tutte le voci di un menu.
- Salva

![scheda assegnazione menu modifica stile template](../../../en/images/templates/switch-templates-styles-edit-style-menu-assignment.png)

In questo esempio, tutte le voci di menu nel menu `Main Menu Testing` sono state selezionate. Torna al tuo sito e seleziona una qualsiasi delle voci di menu che dovrebbe utilizzare il template selezionato.

### Metodo dei Dettagli del Menu

Questo metodo viene utilizzato per impostare il template per singole voci di menu.

- Seleziona **Menu → \[Nome del Menu\]** dal menu Amministratore.
- Seleziona un link di una voce di menu dalla colonna Titolo per aprire il modulo di modifica.
- Nel campo **Stile del Template**, seleziona lo stile di template desiderato.
- Salva

![modulo di modifica voce menu template stile selezione](../../../en/images/templates/switch-templates-styles-edit-menu-style.png)

Torna al tuo sito e seleziona la voce di menu modificata per verificare che sia visualizzata con lo stile di template selezionato.

*Tradotto da openai.com*

