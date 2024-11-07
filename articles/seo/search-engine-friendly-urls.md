<!-- Filename: Search_Engine_Friendly_URLs / Display title: URL amichevoli per i motori di ricerca  -->

## Percorsi e Rotte

Gli URL SEF hanno senso sia per gli esseri umani che per i motori di ricerca perché spiegano il percorso verso la pagina particolare a cui puntano. Un **percorso** è la posizione di un file in una struttura ad albero di directory o la sua simulazione nel codice. Internamente, la parte locale di un URL SEF (la parte dopo il nome di dominio) è chiamata **rotta**. La creazione e l'elaborazione degli URL SEF è quindi denominata **routing**, e il codice pertinente è chiamato **router**.

Gli URL amici dei motori di ricerca possono essere attivati con i seguenti passaggi:
* Nella **Configurazione Globale**
    - impostare l'opzione **URL Amici dei Motori di Ricerca** su **Sì**.
    - Impostare l'opzione **Usa Riscrittura URL** su **Sì**
    - Opzionale: Impostare l'opzione **Aggiungi Suffisso all'URL** su **Sì**.
* Nella radice del sito, rinominare htaccess.txt in .htaccess se si utilizza un server Apache, o consultare la documentazione esterna per NginX o altri server.

Un esempio di routing può essere visto nell'effetto incrementale che queste modifiche hanno sull'URL della pagina Blog della Categoria **Articoli** nei dati di esempio.

- Con gli URL SEF disattivati nella Configurazione Globale e .htaccess disabilitato, l'URL è qualcosa come `https://www.example.com/index.php?option=com_content&view=category&layout=blog&id=16&Itemid=125` e il breadcrumb mostra:<br>
 *Sei qui: Home / Layout di Esempio / Articoli*
- Con gli URL SEF attivati ma senza riscrittura URL, diventa:
  `https://www.example.com/index.php/sample-layouts/articles`
- Con entrambi gli URL SEF attivi, Riscrittura URL attiva e .htaccess abilitato diventa
  `https://www.example.com/sample-layouts/articles.html` (Aggiungi Suffisso all'URL impostato su Sì).

## Numeri negli URL non-SEF

Nella parte dell'URL che dice `id=16&Itemid=125`, i numeri sono i
parametri necessari per individuare l'URL interno e mostrare la pagina richiesta. In
questo caso, il primo numero è l'ID di una Categoria e il secondo numero
è l'ID dell'elemento di menu Blog Categoria per quella Categoria.

*Tradotto da openai.com*

