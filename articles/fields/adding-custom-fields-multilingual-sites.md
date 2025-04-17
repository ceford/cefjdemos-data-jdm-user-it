<!-- Filename: J3.x:Adding_custom_fields/Multilingual_Sites / Display title: Siti Multilingue -->

## Introduzione

Se hai un sito multilingue, puoi mostrare le etichette e le descrizioni dei campi e dei gruppi di campi nella lingua dell'utente. Per fare ciò:

1. Definisci il Titolo e la Descrizione del tuo gruppo di campi come costanti linguistiche.
2. Definisci l'Etichetta e la Descrizione del tuo campo come costanti linguistiche.
3. Imposta tali costanti linguistiche come sostituzioni per ciascuna delle tue lingue.

Nel seguente esempio, viene creato un gruppo di campi e un campo Contatto per le preferenze personali di un contatto. Il gruppo di campi è chiamato Preferiti e il campo di esempio è chiamato Auto. Chiaramente, possono essere aggiunti altri campi per altre cose preferite, come cibo o film.

Per seguire questo esempio, si presume che tu abbia impostato un sito multilingue come descritto nel tutorial [Siti Multilingue](jdocmanual?article=user/languages/setup-a-multilingual-site).

## Costanti di Linguaggio

Le costanti di linguaggio sono segnaposto che vengono sostituiti dai valori di linguaggio quando una pagina viene resa. Le costanti e i loro valori sono memorizzati in file di linguaggio, come ad esempio JPATH_SITE/languages/en-GB/com_contact.ini e JPATH_SITE/administrator/languages/en-GB/com_contact.ini, rispettivamente per il frontend e il backend. Per convenzione, la maggior parte delle costanti di linguaggio inizia con il nome dell'estensione tutto in maiuscolo, ad esempio COM_CONTACT_...

Le sovrascritture del linguaggio sono sostituzioni definite dall'utente per costanti e valori di linguaggio esistenti o costanti e valori completamente nuovi, come in questo esempio. Sono tutte memorizzate in file singoli, uno per le pagine del Sito e un altro per le pagine dell'Amministratore:
```
SITE_ROOT/language/overrides/en-GB.override.ini
SITE_ROOT/administrator/language/overrides/en-GB.override.ini
```
È importante rendere uniche le nuove costanti di linguaggio definite dall'utente per evitare di sovrascrivere le costanti esistenti. Ad esempio:

COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES="Preferiti"
COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION="Auto preferita, film, ecc."
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR="Auto Preferita"
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION="A volte utilizzata come domanda di sicurezza"

Se c'è qualcosa di errato nella sintassi di un file di linguaggio, non verrà caricato e tutte le costanti in esso contenute potrebbero apparire nelle pagine di output. E si noti che un file è ordinato in ordine alfabetico.

## Definire gli Overrides

È importante creare gli overrides per l'inglese (GB). Joomla carica prima i file di traduzione en-GB e poi sovrascrive i valori con un file di lingua selezionato. Questo garantisce che gli utenti non debbano mai vedere una costante di testo. Se manca un valore tradotto, l'inglese apparirà nel risultato. Questo può sembrare strano, ma è meglio che vedere una costante piuttosto lunga che di solito interrompe i layout.

Dal menu dell'Amministratore:

* Seleziona **Sistema / Pannello di gestione / Overrides lingua**
* Seleziona **Inglese (Regno Unito) - Sito** dalla lista *Seleziona Lingua & Cliente*
* Seleziona il pulsante **Nuovo** dalla barra degli strumenti.
* Nel campo **Costante di Lingua** inserisci *COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES*
* Nel campo **Testo** inserisci il valore *Favourites*
* Seleziona la casella di controllo **Per Entrambe le Posizioni**. Questo creerà gli overrides sia per le pagine del Sito che dell'Amministratore.
* Seleziona **Salva & Nuovo** dal menu a discesa *Salva & Chiudi*.
* Ripeti per ciascuna delle altre costanti richieste.
* Seleziona **Chiudi** dopo che l'ultima voce è stata salvata.
* Ripeti per ciascuna delle lingue installate.

Lo screenshot seguente mostra un esempio di creazione di un override per una costante della lingua tedesca.

![Creazione di un override in tedesco](../../../en/images/fields/fields-overrides-creation-de.png)

## Definizione del Gruppo di Campi

Dal menu dell'Amministratore:

* Seleziona la voce di menu **Componenti / Contatti / Gruppi di Campi**.
* Seleziona il pulsante **Nuovo** dalla Toolbar.
* Nel campo Titolo inserisci la costante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES.
* Nel campo Descrizione inserisci la costante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION.
* Seleziona **Salva & Chiudi** dalla Toolbar.

## Definizione del Campo

Per selezionare un'auto preferita, potresti fornire un elenco a discesa di auto che definisci, o un elenco a discesa di auto ottenuto da una tabella di database, o un elenco di pulsanti radio con etichette che definisci. In questo caso, un semplice campo di inserimento testo permetterà l'inserimento di qualsiasi marca e modello di auto dall'intera storia mondiale dell'industria automobilistica.

Dal menu Amministratore:

* Seleziona la voce di menu **Componenti / Contatti / Campi**.
* Seleziona il pulsante **Nuovo** dalla barra degli strumenti.
* Nel campo Titolo inserisci la costante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR
* Nel campo Tipo seleziona **Testo (text)** se non è già selezionato.
* Nel campo Descrizione inserisci la costante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION
* Nel campo **Gruppo di Campi** (alla destra) seleziona il Gruppo di Campi che hai creato.
* Seleziona **Salva & Chiudi** dalla barra degli strumenti.

## Modificare un Contatto

Con l'inglese selezionato prima dell'accesso come Amministratore, il modulo di inserimento dati del contatto dovrebbe contenere una scheda con il nome inglese del tuo gruppo di campi e i campi in quel gruppo con valori in inglese.

![Inserimento dati in inglese](../../../en/images/fields/fields-overrides-entry.png)

Con il tedesco selezionato prima dell'accesso come Amministratore, dovresti vedere le traduzioni tedesche delle tue costanti linguistiche:

![Inserimento dati in tedesco](../../../en/images/fields/fields-overrides-entry-de.png)

Avvertenza: traduzione tramite translate.google.co.uk!

## Visualizza un Contatto

In inglese:

![Visualizzazione dei dati in inglese](../../../en/images/fields/fields-overrides-display.png)

E in tedesco:

![Visualizzazione dei dati in tedesco](../../../en/images/fields/fields-overrides-display-de.png)

*Tradotto da openai.com*

