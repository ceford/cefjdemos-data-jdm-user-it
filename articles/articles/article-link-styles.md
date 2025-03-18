<!-- Filename: J5.x:Add_a_class_selector_to_the_create_link_dialog / Display title: Articolo: Modifica - Stili di link -->

## Descrizione

Classi di collegamento personalizzate aggiunte alle opzioni dell'editor TinyMCE consentono di trasformare rapidamente un collegamento di un articolo in un pulsante o di aggiungere altri effetti visivi senza dover modificare direttamente il codice HTML.

### Passaggi per usare il selettore di classe

1. Dalla Dashboard Home, vai alla lista dei Plugin e trova il plugin TinyMCE.
2. Apri il plugin TinyMCE e con la scheda Plugin selezionata scorri fino in fondo.
3. Aggiungi classi alla *Lista Classi Collegamento*. Ad esempio, classi di Bootstrap per creare pulsanti eleganti. Potrebbe essere necessario scorrere la lista da sinistra a destra o cambiare l'ingrandimento dello schermo per vedere i pulsanti di aggiunta, rimozione e ordinamento alla fine.
4. Salva e Chiudi.

![Set link classes in tinymce](../../../en/images/articles/article-edit-link-style-tinymce.png)

Puoi trovare esempi di modelli che utilizzano nativamente Bootstrap nella [documentazione ufficiale di Bootstrap](https://getbootstrap.com/docs/5.3/components/buttons/).

Ecco alcune classi che puoi utilizzare per le varianti dei pulsanti Bootstrap:

- `btn btn-primary` per un pulsante primario
- `btn btn-secondary` per un pulsante secondario
- `btn btn-success` per un pulsante di successo
- `btn btn-danger` per un pulsante di pericolo
- `btn btn-warning` per un pulsante di avviso
- `btn btn-info` per un pulsante di informazione
- `btn btn-light` per un pulsante chiaro
- `btn btn-dark` per un pulsante scuro
- `btn btn-link` per un pulsante di collegamento

#### Alternative al Pulsante Contorno

Puoi anche utilizzare le varianti dei pulsanti con contorno:

- `btn btn-outline-primary` per un pulsante primario contornato
- `btn btn-outline-secondary` per un pulsante secondario contornato
- … (ecc.)

#### Per le dimensioni dei pulsanti, aggiungi queste classi

- `btn-lg` per un pulsante grande
- `btn-sm` per un pulsante piccolo

**Esempio:** `btn btn-dark btn-lg` (un grande pulsante scuro)

## Creare un collegamento in un articolo

1. Apri un articolo e seleziona del testo, una parola o una frase, per la creazione di un link.
2. Seleziona l'icona del Link che appare quando selezioni del testo.
3. Inserisci l'URL per il link.
4. In fondo alla finestra di dialogo per la creazione del link, seleziona una delle classi configurate.
5. Salva il Link.
6. Salva l'Articolo.
7. Anteprima dell'Articolo.

![Apply link style in an article](../../../en/images/articles/article-edit-link-style-apply.png)

E questo è un esempio in cui la classe del pulsante di collegamento è stata impostata su `btn btn-sm btn-outline-info` e il testo collegato è *Bootstrap*:

![Preview of a custom Link Button](../../../en/images/articles/article-edit-link-style-preview.png)

## Uso avanzato: Applicazione di classi personalizzate

Questa funzionalità non è limitata alle classi di Bootstrap. È possibile applicare anche le proprie classi CSS personalizzate per esigenze specifiche. Ad esempio, è possibile aggiungere un'icona prima del link con un effetto hover. Questo rende facile stilizzare i link senza dover modificare il codice sorgente dell'articolo.  
*Tradotto da openai.com*

