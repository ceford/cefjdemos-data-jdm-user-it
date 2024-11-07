<!-- Filename: J4.x:Article_Links / Display title: Articolo: Modifica - Collegamenti   -->

## Collegamenti Accessibili

Seleziona un collegamento in un documento e il tuo browser apre il documento collegato, sia nella stessa finestra, in una nuova finestra o in una nuova scheda. Una persona che utilizza un lettore di schermo potrebbe navigare solo tramite collegamenti, quindi il testo dei collegamenti deve essere significativo.

Il seguente è un esempio di **buona pratica** perché indica chiaramente a cosa porterà il collegamento:

- Per saperne di più, leggi il nostro [Manifesto](#)

Il seguente è un esempio di **cattiva pratica** perché non dà alcuna indicazione sulla natura della destinazione e potrebbe essere uno di diversi collegamenti simili nella stessa pagina:

- Per saperne di più, clicca [qui](#)

Per saperne di più sui collegamenti accessibili, vedi questo articolo su [Creare collegamenti validi e accessibili](https://www.a11yproject.com/posts/creating-valid-and-accessible-links/).

## Collegamenti Incorporati

Questo articolo riguarda i collegamenti incorporati nel contenuto di un articolo. Esiste un articolo separato sull'uso della scheda [Immagini e Collegamenti](jdocmanual?article=user/articles/article-images-and-links) per includere collegamenti associati a un articolo.

I collegamenti incorporati in un articolo possono essere verso altre pagine all'interno del sito (collegamenti interni) o verso altri siti (collegamenti esterni). La procedura per inserire i due tipi è diversa. Ciascuno è descritto di seguito.

## Inserire un Collegamento Interno

Il processo per inserire un collegamento a un articolo nello stesso sito web è semplice:
- Scrivi la frase che contiene il testo del link. Per esempio:

  *Per ulteriori informazioni, consulta la pagina sui Rane.*
- Seleziona il testo del link: *Rane*

Il collegamento può essere a un singolo articolo o a un elemento di menu per un blog di categoria,
una lista di categorie o articoli in evidenza.

### Un Collegamento a un Singolo Articolo

- Seleziona *Articolo* dal menu a discesa *Contenuto CMS*.
- Seleziona il titolo dell'articolo richiesto dalla finestra di dialogo Articolo. 
- Salva l'articolo e verificane il funzionamento utilizzando il pulsante Anteprima nella barra degli strumenti.

### Un Collegamento a un Elemento di Menu

- Seleziona *Menu* dal menu a discesa *Contenuto CMS*.
- Seleziona l'elemento di Menu richiesto dalla finestra di dialogo Menu. 
- Salva l'articolo e verificane il funzionamento utilizzando il pulsante Anteprima nella barra degli strumenti.

## Inserire un Link Esterno

Per un link esterno è meglio copiare il link dalla barra degli URL del browser. 
A tale scopo è utile avere finestre o schede separate aperte per il 
modulo *Articoli: Modifica* del tuo sito e il sito remoto a cui stai creando un collegamento.
Procedura:

- Trova o crea una frase che contenga il testo da utilizzare come testo del link. 
  Ad esempio:

  *Per ulteriori informazioni, visita l'articolo di Wikipedia sulle Green Tree Frogs.*
- Seleziona la parola o le parole da collegare, in questo caso *Green Tree Frogs*.
- Quindi utilizza uno dei seguenti metodi: 
  - Seleziona **Inserisci → Link** dal menu Testo Articolo (la prima barra degli strumenti
    in cima alla scheda Contenuto).
  - Fai doppio clic sul testo selezionato per aprire un piccolo menu a comparsa che 
    contiene un'icona di link da selezionare.

Entrambi i metodi apriranno una finestra di dialogo Inserisci/Modifica Link da compilare come segue:

- Nel campo *URL*, incolla il link copiato dalla barra dell'URL della finestra di destinazione.
- Il campo *Testo da visualizzare* dovrebbe contenere il testo selezionato
  prima di aprire la finestra di dialogo. In caso contrario, qualsiasi testo digitato qui verrà
  inserito nell'articolo quindi deve essere qualcosa che abbia senso nel contesto. Promemoria: evita *Fai clic qui* o *Leggi di più*.
- Il campo *Titolo* crea un attributo Title per il link ma il suo utilizzo
  da parte dei browser è incoerente e controverso per quanto riguarda l'accessibilità.
  In caso di dubbio, lascialo vuoto.
- Il campo *Rel* ha diverse opzioni. In caso di dubbio, lascialo impostato su
  *Nessuno*. È disponibile un elenco di opzioni nell'articolo delle *mdn web docs* su 
  [HTML attrributo: rel](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel).
- Il campo *Apri link in...* è una scelta semplice tra
  *Finestra corrente* e *Nuova finestra*. Le impostazioni del browser controllano
  se ciò risulta in una nuova finestra separata o in una nuova scheda.
- Salva l'articolo e prova utilizzando il pulsante Anteprima nella barra degli strumenti.

## Verifica dei link

Nella visualizzazione del sito della pagina, controlla che il link abbia un aspetto buono e funzioni correttamente. 
Provalo anche con un lettore di schermo!

## Rimuovere un Link

Ci sono diversi modi per rimuovere un link. Metodo 1:
- Clicca sul link.
- Seleziona l'icona con i puntini di sospensione (...) per aprire il menu espanso dell'editor.
- Seleziona l'icona *Remove Link*.
- Salva. Il testo rimane ma il link scompare.

Metodo 2:
- Fai doppio clic sul link.
- Seleziona l'icona Link nel piccolo popup.
- Nella finestra di dialogo Inserisci/Modifica Link, elimina il contenuto del campo URL.
- Salva. Il testo rimane ma il link scompare.

Metodo 3:
- Cancella il testo contenente il link. Il link e il testo scompaiono entrambi.

Metodo 4:
- Seleziona il link.
- Seleziona il pulsante TinyMCE Edit / Link.
- Nella finestra di dialogo Inserisci/Modifica Link, elimina il contenuto del campo URL.
- Salva. Il testo rimane ma il link scompare.

## Modificare un Collegamento

Utilizzando uno dei metodi descritti sopra per aprire la finestra di dialogo Inserisci/Modifica Collegamento, incolla un nuovo URL di collegamento. Ricorda: è sempre meglio copiare l'URL dalla barra degli indirizzi di una finestra o scheda del browser che visualizza la pagina di destinazione e incollarlo nel campo URL del modulo Inserisci/Modifica Collegamento.

*Tradotto da openai.com*

