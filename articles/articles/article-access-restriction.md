<!-- Filename: J6.x:Article_Access_Restriction / Display title: Articolo: Restrizioni di Accesso  -->

## Introduzione

Ci sono diversi motivi per limitare l'accesso agli articoli su un sito web. Alcuni contenuti possono essere riservati a utenti specifici, come i membri di un comitato. Oppure, il sito potrebbe contenere contenuti commerciali a pagamento. Joomla offre un potente sistema di Lista di Controllo Accesso (ACL) per limitare l'accesso. È descritto in un articolo separato su [Controllo Accessi](jdocmanual?article=user/users/access-control) nella sezione Utenti di questo manuale.

Questo articolo descrive l'implementazione della restrizione di accesso nel modulo *Articolo: Modifica*. 

## Restrizione per Livello di Accesso

Joomla fornisce i Livelli di Accesso mostrati nello screenshot seguente:

![Livelli di accesso utente](../../../en/images/articles/article-access-user-groups.png)

I livelli di accesso appaiono nella scheda *Contenuto* del modulo *Articolo: Modifica*.

- **Pubblico** Può essere visualizzato da tutti - sia dagli utenti che hanno effettuato l'accesso sia da quelli
  che non hanno effettuato l'accesso.
- **Ospite** Questo livello di accesso limita l'accesso agli utenti che **NON** hanno effettuato l'accesso.
- **Registrato** Questo livello limita l'accesso agli utenti che hanno effettuato l'accesso.
  Un articolo con *Accesso* impostato su *Registrato* richiederà un login sul
  front-end prima che l'articolo possa essere visualizzato.
- **Speciale** Questo livello limita l'accesso agli utenti che hanno effettuato l'accesso e
  fanno parte di un gruppo utente specifico diverso da Registrato. Inoltre, è
  possibile differenziare contenuti che alcuni utenti connessi possono accedere
  mentre altri no. Tipicamente, questo potrebbe essere un sito web dove sono richiesti abbonamenti
  per accedere a contenuti aggiuntivi.
- **Super Utenti** Impostare questo livello significa che solo un Super Utente può accedere
  all'articolo. Questo potrebbe essere utilizzato per articoli sulla gestione del sito.

Nota che questa lista riguarda **la visualizzazione** o il permesso di visualizzare i contenuti.
Puoi creare livelli di accesso aggiuntivi e gruppi utente per personalizzare chi può
vedere cosa.

## Restrizione Parziale per Leggere di Più

A volte potresti voler limitare l'accesso a un articolo ma consentire l'accesso senza restrizioni a un'anteprima dell'articolo. Questo è un modo comune per implementare l'accesso a pagamento a contenuti commerciali. Procedura:

- Trova l'articolo da limitare parzialmente nella lista degli *Articoli* e aprilo per la modifica.
- Inserisci un *Interruzione di Pagina* dopo il primo paragrafo. Lo strumento di Interruzione di Pagina si trova verso il basso della lista *Contenuto CMS* nel modulo di modifica degli articoli di TinyMCE.
- Imposta il livello di *Accesso* dell'articolo su *Registrato*.
- Seleziona **Salva & Chiudi** nella barra degli strumenti.

### Limitazione dell'accesso agli Articoli individualmente

Apri la voce di menu *Categoria Blog* o *Articoli In Evidenza* dove apparirà l'articolo.

- Nella scheda **Opzioni**, imposta **Link Non Autorizzati** su **Sì**. Si trova in fondo alla lista delle Opzioni.
- Seleziona **Salva & Chiudi** nella barra degli strumenti.

### Limitazione dell'accesso agli Articoli Globalmente

* Imposta le Categorie rilevanti al livello di visualizzazione *Pubblico*, altrimenti le voci di menu non saranno visibili agli utenti che non hanno effettuato l'accesso.
* Imposta gli articoli nelle Categorie rilevanti al livello di visualizzazione Registrato. Questo può essere fatto selezionando gli articoli e utilizzando il pulsante *Batch*.
* Vai a **Contenuto → Articoli → Opzioni**
* Imposta **Link Non Autorizzati** su **Sì** nella scheda Articoli. Se impostato su Sì, i link ai contenuti registrati saranno mostrati anche se non hai effettuato l'accesso. Dovrai accedere per poter visualizzare l'intero articolo.

**Nota:** Il testo in un articolo senza un'interruzione *Leggi di Più* è considerato tutto come testo introduttivo. Se hai un articolo che dovrebbe essere limitato solo agli utenti registrati ma non ha un Leggi di Più, allora l'intero articolo sarà visibile a tutti gli utenti. Quindi, aggiungi un Leggi di Più all'articolo!

*Tradotto da openai.com*

