<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Moduli all'interno degli Articoli  -->

## Introduzione

Di solito vuoi associare i moduli agli articoli in qualche modo. I moduli sono solitamente assegnati a posizioni di modulo e le posizioni di modulo appaiono da qualche parte sulla pagina web come determinato dal template. Tuttavia, a volte è utile avere un modulo effettivamente incorporato all'interno di un articolo. Joomla ha un plugin chiamato *Content - Load Modules* per fare ciò. Quando è abilitato, un modulo può essere incorporato in un articolo in tre modi diversi:

```
    {loadposition position,[style]}
    {loadmodule mod_type,the title,[style]}
    {loadmoduleid moduleId}
```

Dove `style` è uno dei valori di Stile Modulo dalla scheda Avanzato del modulo modulo, ad esempio html, outline, table, card o noCard.

## loadposition

Per inserire un modulo all'interno di un articolo, devi pubblicare il modulo in una posizione e caricare quella posizione nell'articolo come segue:

1. Crea un modulo e imposta la sua posizione su ***myposition***. ***myposition*** può essere qualsiasi valore che non entri in conflitto con una posizione di template esistente. Nel modulo di modifica del modulo, digita la posizione ***myposition*** e premi invio invece di selezionarla dall'elenco a discesa.
2. Assegna il modulo a **Tutti** gli oggetti del menu. Questo garantirà che esso appaia sempre, indipendentemente da come il visitatore sia arrivato all'articolo. Il modulo non verrà mostrato a meno che non si utilizzi il comando per caricare il modulo in un articolo.
3. Modifica l'articolo e inserisci il testo ***{loadposition myposition}*** nel punto in cui desideri che appaia il modulo.

**Nota:** Se il plugin *Content - Load Modules* è disattivato, il testo *{loadposition myposition}* verrà mostrato invariato nell'articolo. Inoltre, il nome della posizione dovrebbe essere tutto in minuscolo. La scrittura in CamelCase non funzionerà.

## loadmodule

La sintassi *{loadmodule yyy}* cerca il primo modulo il cui **tipo** corrisponde alla stringa 'yyy'. Quindi, potresti caricare un modulo *mod_login* inserendo {loadmodule login} nel tuo testo. Il tipo non è così evidente! Ad esempio, il Language Switcher è di tipo **languages**. Per trovare il tipo, devi cercare nella lista delle cartelle dei moduli con un file manager/esploratore e rimuovere la parte *mod_* dal nome della cartella.

Se desideri caricare un'istanza specifica di un modulo, perché hai più di un modulo di login ad esempio intitolato come Login 1, Login 2, ecc., devi usare {loadmodule mod_modType, modTitle} dove **mod_modType** sarebbe mod_login e **modTitle** sarebbe il nome/titolo assegnato alla tua istanza di quel modulo. Quindi, nell'esempio sopra, ottieni **{loadmodule mod_login Login 2}**.

Puoi anche aggiungere lo stile utilizzato per il rendering del modulo. Per farlo, aggiungi lo stile come terzo parametro, ad esempio {loadmodule login,Login 2,xhtml}. Se non aggiungi uno stile, allora nessuno verrà usato.

## loadmoduleid

La sintassi *{loadmoduleid z}* cerca il modulo il cui `id` corrisponde al numero `z`. Quindi, potresti caricare il modulo con id 200 inserendo *{loadmoduleid 200}* nel tuo testo. Questa variante non utilizza parametri aggiuntivi come il parametro `style`.

## Pulsante dell'Editor

Se il plugin editor-xtd *Pulsante - Modulo* è attivato, puoi utilizzare il pulsante dell'editor *Modulo* per inserire più facilmente i tag descritti sopra nel testo dell'editor. La lista dei Moduli ha un pulsante nella colonna Titolo per inserire per id e un pulsante nella colonna Posizione per inserire per posizione.

## Moduli all'interno di moduli

È possibile includere un modulo all'interno di un modulo *HTML Personalizzato*. Vengono processati dai plugin di contenuto nello stesso modo degli articoli.

Potrebbero esserci problemi di formattazione poiché lo stile del modulo *HTML Personalizzato* circonderà lo stile del modulo incluso. È questo il motivo per cui il pulsante dell'editor *Modulo* non è disponibile nei moduli di tipo *Personalizzato*.

