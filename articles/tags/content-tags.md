<!--
{
    "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
    "title": "Tag di contenuto",
    "description": " ",
    "author": ""
}
-->

## Introduzione

I tag offrono un modo semplice ed efficiente per organizzare e visualizzare i contenuti. 
Il **componente Tag** consente di utilizzare singoli tag in diversi tipi di 
contenuto, inclusi articoli, categorie, contatti e feed di notizie. Consente inoltre di creare tag principali e secondari.

A differenza delle **categorie** di Joomla, in cui è possibile assegnare un'unica categoria
a un elemento, è possibile assegnare più tag a un singolo elemento, ma non è
obbligatorio assegnare tag agli elementi.

Quando a un elemento viene assegnato un tag specifico, facendo clic sul pulsante del tag nei
contenuti che visualizzano i tag si accede a una pagina che mostra un elenco di
tutti gli elementi a cui è stato assegnato quel determinato tag. Per questo
motivo, i tag vengono spesso utilizzati per presentare elenchi di contenuti *filtrati*.

I tag possono essere aggiunti in diversi punti, offrendo flessibilità nella loro creazione.

## Considerazioni

Prima di iniziare, valutare lo scopo dei tag nel sito web, soprattutto
se altre persone aggiungeranno contenuti. Se non vengono aggiunti e gestiti
correttamente, i tag possono diventare controproducenti. Tra i problemi comuni vi sono
l'aggiunta di nuovi tag non necessari da parte degli autori dei contenuti e i nomi dei tag
con errori di ortografia. Alcuni amministratori del sito possono scegliere di modificare le autorizzazioni di accesso in modo che
solo utenti specifici possano aggiungere nuovi tag.

La schermata seguente mostra i tag utilizzati in un sito contenente articoli sui
siti patrimonio dell'umanità dell'UNESCO. In questo caso ogni tag ha un colore distintivo. 

![la pagina dell'elenco dei tag](../../../en/images/tags/content-tags/01-tags-example.png)

Quando vengono creati, i tag vengono visualizzati come collegamenti negli elementi a cui sono assegnati. 
Gli stili e le posizioni dei tag sono definiti dal template del sito. Spesso
vengono visualizzati come pulsanti o etichette.

La visualizzazione dei tag può essere disattivata per singoli articoli o per tutti gli articoli! Questo
può sembrare illogico, ma è una funzione utile quando i tag vengono utilizzati, ad esempio,
per filtrare i contenuti in base a casi d'uso specifici.

## L'elenco dei tag

- Selezionare **Componenti → Tag** dal menu dell'amministratore.

Questa schermata mostra i tag in una struttura utilizzata per un sito multilingue.
Ogni lingua ha un elenco di tag con un tag della lingua come elemento principale. 
Il tag principale viene utilizzato nei moduli *Tag popolari* e *Tag simili*.

![la pagina dell'elenco dei tag](../../../en/images/tags/content-tags/02-tags-list.png)

Indipendentemente dal modo in cui vengono creati, i tag sono disponibili in questo elenco.

- Selezionare il pulsante **Nuovo** nella barra degli strumenti per creare un nuovo tag.
- Selezionare il **Titolo** di un tag per modificarne uno esistente.

### La scheda Dettagli tag

![modulo di modifica del tag, scheda delle opzioni con classi CSS bootstrap](../../../en/images/tags/content-tags/03-edit-tag-details-tab.png)

- **Titolo** Questo è l'unico campo *obbligatorio*. 
- **Alias** Viene creato dal titolo al momento del salvataggio.
- **Descrizione** È sempre consigliabile aggiungere una descrizione. Viene visualizzata nei
  moduli dell'amministratore e può essere utile quando sono in uso molti tag.
- **Principale** Lasciare impostato su *Nessuno* se si tratta di un tag che non ha un elemento principale. Oppure scegliere un
  tag principale dall'elenco per rendere questo un tag secondario.
- **Stato** Questo campo è impostato su *Pubblicato* per impostazione predefinita. Può essere impostato su
  *Non pubblicato*, *Archiviato* o *Cestinato*.
- **Accesso** Il livello di accesso è Pubblico per impostazione predefinita.
- **Nota** e **Nota sulla versione:** Se necessario, è possibile aggiungere note.
- **Salva e chiudi** Se si stanno creando più tag, è possibile selezionare **Salva e nuovo** per creare un nuovo tag.

### La scheda Opzioni

- **Layout** Potrebbero essere disponibili diversi layout tra cui scegliere; è anche possibile creare un layout personalizzato con un override del template.
- **Classe CSS per il collegamento del tag** Per impostazione predefinita, i tag vengono visualizzati come pulsanti blu. È possibile inserire qui le dichiarazioni di classe per personalizzare l'aspetto dei tag e assegnare colori diversi a tag diversi. Esempio: `bg-danger-subtle border border-danger` sono classi Bootstrap che producono un pulsante rosa con un bordo rosso.
- **Immagine teaser e immagine completa** Impostare le immagini per il tag: un'immagine teaser per l'elenco dei tag e/o un'immagine completa per la pagina del tag.

![modulo di modifica del tag, scheda delle opzioni con classi CSS bootstrap](../../../en/images/tags/content-tags/04-edit-tag-options-tab.png)

### La scheda Pubblicazione

- Impostare i metadati per la pagina del tag ai fini dell'ottimizzazione per i motori di ricerca (SEO).

## Metodi alternativi di creazione

### Da un articolo

È possibile aggiungere nuovi tag durante la creazione o la modifica di un articolo. Nella
scheda Contenuto dell'articolo, nel **Campo Tag**, inserire il nome del nuovo tag e
premere **Invio** per salvare e assegnare il tag all'articolo.

### Da una categoria

I tag possono essere aggiunti durante la creazione o la modifica di una categoria. Nella scheda **Categoria**
inserire il nome del tag nel **Campo Tag** e premere **Invio** per creare
e assegnare il nuovo tag.

### Da un contatto

I tag possono essere aggiunti durante la creazione o la modifica di un contatto. Nella 
scheda **Nuovo/Modifica contatto**, inserire il nome del tag nel **Campo Tag** e premere 
**Invio** per creare e assegnare il nuovo tag. È inoltre possibile aggiungere nuovi tag durante la creazione delle categorie di contatti.

### Da un feed di notizie

I tag possono essere aggiunti durante la creazione o la modifica di un nuovo feed di notizie. Nella scheda 
**Nuovo/Modifica feed di notizie**, inserire il nome del tag nel **campo Tag** e premere
**Invio** per creare e assegnare il nuovo tag. È inoltre possibile aggiungere nuovi tag durante 
la creazione delle categorie dei feed di notizie.

## Gestione dei tag

Ovunque vengano aggiunti nuovi tag in Joomla, questi compariranno nell'elenco dei tag.
Utilizzare l'elenco dei tag per trovare, aprire e modificare le impostazioni dei tag.

È possibile manipolare l'elenco in diversi modi:

- Cercare un tag utilizzando nel campo di ricerca una parte o tutto il titolo o l'alias.
- Riordinare l'elenco utilizzando il trascinamento per ottimizzare l'ordine di visualizzazione.
- Pubblicare o sospendere la pubblicazione dei tag utilizzando il pulsante nella colonna Stato.
- Selezionare uno o più tag e utilizzare il pulsante **Azioni** per Pubblicare, Sospendere la pubblicazione, Archiviare, Registrare o Cestinare i tag selezionati.
- Selezionare uno o più tag e utilizzare il pulsante **Azioni → Batch** per impostare la Lingua o il Livello di accesso.

## Visualizzazione dei tag

Una volta creati, i tag sono disponibili per l'uso nei contenuti e in moduli come **Tag popolari** e **Tag simili**. Gli esempi seguenti mostrano come potrebbero apparire in un sito che utilizza il template predefinito **Cassiopeia**.

![tag visualizzati in un articolo e nei moduli dei tag popolari e dei tag simili](../../../en/images/tags/content-tags/05-tag-modules-site-view.png)

Quando si seleziona uno dei tag, si viene indirizzati a una pagina che elenca
tutti gli elementi assegnati a quel particolare tag:

![esempio dell'utilizzo dei tag nel sito con un labrador nero](../../../en/images/tags/content-tags/06-items-with-cultural-site-tag.png)

L'elenco degli elementi è un elenco filtrato dei contenuti del sito web con il tag selezionato.
Viene fornita una casella di filtro per facilitare la ricerca degli elementi man mano che l'elenco cresce. 
È inoltre possibile impostare il numero di risultati da visualizzare in un'unica schermata.

## Configurazione dei tag

I singoli tag ereditano le impostazioni dalle opzioni del componente Tag. Selezionare il pulsante 
**Opzioni** nella barra degli strumenti della pagina dell'elenco dei tag per visualizzare le opzioni predefinite
disponibili per i tag.

Le opzioni di configurazione del componente Tag possono essere sostituite a livello di elemento di contenuto e/o di voce di menu.

## Suggerimenti

- Ricordare che i tag vengono utilizzati in più tipi di contenuto.
- È possibile aggiungere più di un tag a un elemento.
- Utilizzare il pulsante Guida della barra degli strumenti in caso di dubbi.

*Tradotto da openai.com*