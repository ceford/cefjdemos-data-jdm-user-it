<!-- Filename: J4.x:Getting_Started:_Adding_a_Category / Display title: Aggiungere una Categoria  -->

## Introduzione

I proprietari di siti web con più di un certo numero di articoli dovrebbero pensare a come presentare al meglio i contenuti per facilitare la navigazione. Ad esempio, se hai uno zoo, un museo, una collezione di minerali o semplicemente un grande giardino, potresti dover descrivere circa 1000 esemplari. Un articolo per ogni esemplare, con fotografie, necessita di una certa struttura organizzativa. Se gli articoli fossero file, probabilmente li organizzeresti in una gerarchia di file. In un CMS, gli articoli non sono file, ma le categorie forniscono una struttura ad albero simile. Esempio:

| Categoria  | Sotto-categorie                          |
|------------|------------------------------------------|
| Mammiferi  | Scimmie antropomorfe, Scimmie, Ungulati, Cani, Gatti |
| Rettili    | Serpenti, Lucertole, Coccodrilli, Tartarughe |
| Anfibi     | Rane, Rospi                              |
| Uccelli    | Rapaci, Anatre, Gabbiani, Fringuelli, Cince |
| Artropodi  | Ragni, Farfalle, Api, Locuste            |
| Pesci      | Squali, Salmoni, Merluzzi, Aringhe, Sgombri |

Le sotto-categorie potrebbero avere ulteriori sotto-categorie. Una profondità massima gestibile sembra essere circa sette. Per la tabella sopra, un museo potrebbe aggiungere più categorie principali:

```text
natura -> vita -> animali -> mammiferi...
natura -> vita -> piante -> alberi...
natura -> minerali...
storia -> egitto...
scienza -> astronomia...
scienza -> chimica...
```

Immagina quanti esemplari possiede un museo nazionale o di una piccola città!  

## Tipi di Voci di Menu

Esistono diversi tipi di voci di menu progettati per funzionare con le categorie:

- **Blog di Categoria** Questo è un layout di pagina che presenta uno o due
  assaggi di articoli iniziali, spesso con la larghezza totale della pagina, seguiti da diversi altri
  assaggi di articoli in due o tre colonne e infine un meccanismo di paginazione per collegarsi
  ad altri articoli nella stessa categoria. L’assaggio è il contenuto prima
  di un'interruzione di pagina, spesso i primi uno o due paragrafi. Una pagina *Home* di un sito è 
  spesso un blog di categoria che include *Tutte le Categorie*. Un layout *Articoli in Primo Piano* 
  è simile a un blog di categoria ed è spesso utilizzato anche come pagina principale.
- **Elenco di Categoria** Questo è un layout a lista che mostra un elenco di
  articoli in una categoria. Può essere visualizzato con un filtro di ricerca per consentire
  di cercare articoli per Titolo, Autore, Visualizzazioni, Tag o Mese di pubblicazione.
- **Elenca Tutte le Categorie in un Albero di Categorie di Articoli** Questo layout elenca un 
  albero delle categorie a partire da un genitore scelto. Ogni ramo è comprimibile ed è più utile
  per strutture di alberi delle categorie grandi e complesse.

Le voci di menu sono trattate in un articolo successivo.

## Creare una Categoria

Il seguente esempio utilizza una categoria Mammiferi ispirata all'elenco sopra per dimostrare come creare una nuova Categoria:

![Modulo di modifica della categoria](../../../en/images/getting-started/article-category-edit.png)

- Seleziona la voce **Contenuti** dal menu dell'Amministratore per espanderla.
- Seleziona l'icona **+** accanto alla voce di menu *Categorie* per aprire il modulo di modifica della Categoria.
- Il modulo **Articoli: Nuova Categoria** ha un solo campo obbligatorio: il *Titolo*, in questo caso *Mammiferi*.
- Il campo **Descrizione** è facoltativo, ma è consigliabile compilarlo poiché viene utilizzato in alcuni elenchi. Suggerimento:<br>
  *I mammiferi sono animali a sangue caldo che partoriscono piccoli vivi.*
- Il campo **Genitore** specifica se questa è una categoria principale (-Nessun Genitore-) o una sottocategoria selezionata dall'elenco delle categorie.
- **Salva e Chiudi** per tornare alla pagina dell'elenco **Articoli: Categorie**.

Questa categoria è ora disponibile per l'uso con gli articoli.

*Tradotto da openai.com*

