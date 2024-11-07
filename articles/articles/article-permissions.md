<!-- Filename: J6.x:Access_Control / Display title: Articolo: Modifica - Autorizzazioni -->

## Introduzione

Joomla offre un sofisticato sistema di *Controllo degli Accessi* basato su *Livelli di Accesso* e *Gruppi di Utenti*. È descritto nell'articolo su [Controllo degli Accessi](jdocmanal?article=user/users/access-control) nella sezione *Utenti* di questo manuale.

La descrizione qui riguarda la scheda *Permessi* del modulo *Articolo: Modifica*. Le sue impostazioni possono sembrare insolite a meno che non siate familiari con il sistema di Controllo degli Accessi di Joomla.

## Screenshot

![La scheda delle autorizzazioni dell'articolo con autore selezionato](../../../en/images/articles/articles-edit-permissions-tab.png)

Può essere sorprendente che un Autore non sembri avere il permesso di modificare un articolo!

## Gruppi Utenti Frontend e Backend

Se non hai familiarità con i gruppi di utenti standard di Joomla, è utile sapere che *Autore*, *Editore* e *Editore* sono gruppi di utenti frontend. Non possono effettuare il login al backend. Il loro lavoro di creazione, modifica e pubblicazione degli articoli viene svolto con i moduli di modifica degli articoli frontend. *Manager* e *Amministratore* sono gruppi di utenti con accesso sia al frontend che al backend e possono modificare gli articoli utilizzando i moduli di modifica backend o frontend.

## Accesso Modifica Autore

Perché nel modulo dei Permessi il campo *Modifica* appare come **Non Consentito (ereditato)** per il gruppo Author?

C'è una spiegazione semplice. Se chiudi il modulo di modifica e vai alla pagina *Articoli: Opzioni* tramite il pulsante *Opzioni* nella barra degli strumenti della lista *Articoli*, la scheda *Permessi* mostra che un membro del gruppo Author ha permessi aggiuntivi: *Crea* e *Modifica Proprio*. Questi sono i permessi che consentono a un autore di creare articoli e modificare i propri articoli.

Quindi, i permessi nel modulo *Articoli: Modifica* non consentono a un membro del gruppo Author di modificare articoli creati da qualcun altro.

