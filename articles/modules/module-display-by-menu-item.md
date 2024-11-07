<!-- Filename: J4.x:Module_Display_by_Menu_Item / Display title: Visualizzazione del Modulo per Voce di Menu  -->

## Introduzione

In Joomla, spesso si verifica il caso che moduli diversi appaiano su pagine diverse. E a volte moduli diversi sono presentati a gruppi di utenti differenti. Il comportamento di visualizzazione dei moduli è controllato da una combinazione di Assegnazione Menu e Permessi di accesso nel modulo di modifica. Di default, un modulo è visualizzato su tutte le pagine e per tutti i gruppi di utenti.

## Accesso

Questo campo si trova nella scheda Modulo del modulo di inserimento dati. Si trova nel pannello di destra e non deve essere confuso con la scheda Permessi. Le opzioni disponibili sono:

- Pubblico - visibile a tutti i gruppi di utenti.
- Ospite - non visibile dopo il login.
- Registrato - visibile solo dopo il login.
- Speciale - visibile solo dopo il login ai gruppi di utenti diversi da Registrato.
- Super Utente - visibile solo a questo gruppo di utenti.

## Assegnazione del Menu

Ci sono quattro opzioni di assegnazione del menu:

- Su tutte le pagine
- Nessuna pagina
- Solo sulle pagine selezionate
- Su tutte le pagine eccetto quelle selezionate

Per le ultime due opzioni viene visualizzato un pannello di Selezione Menu. Inizialmente, i
menu che contiene sono completamente espansi, ma possono essere compressi con il
pulsante **Espandi i Sottoalberi del Menu** *Nessuno*. Poi espandi il menu di
interesse.
![assegnazione del menu del modulo](../../../en/images/modules/module-display-by-menu.png)

Seleziona gli Elementi del Menu per visualizzare o meno il modulo a piacere.

## Esempi

### Breadcrumbs Non sulla Pagina Iniziale

- Apri il modulo Breadcrumbs.
- Seleziona *Su tutte le pagine eccetto quelle selezionate*
- Seleziona *Nessuno* dopo **Assegna a Voci di Menu**
- Trova l'elemento di menu della Pagina Iniziale e seleziona la sua casella di controllo.
- Salva
- Controlla il sito - i breadcrumbs dovrebbero essere presenti su tutte le pagine eccetto la Pagina Iniziale.

