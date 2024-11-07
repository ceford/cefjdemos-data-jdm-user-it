<!-- Filename: Robots.txt_file / Display title: Il file robots.txt -->

## Informazioni sui Robot

I robot web, noti anche come crawler, web wanderer o spider, sono programmi che attraversano il web automaticamente. Tra i numerosi utilizzi, i motori di ricerca li utilizzano per indicizzare il contenuto del web.

Il file robots.txt implementa il [Protocollo di Esclusione dei Robot](https://it.wikipedia.org/wiki/Robots_exclusion_standard), che consente a un amministratore del sito di definire quali parti del sito non devono essere ispezionate da specifici user agent dei robot. Ad esempio, l'accesso al contenuto delle pagine pubbliche è normalmente consentito, ma l'accesso alle directory cgi, private e temporanee, che non dovrebbero avere pagine indicizzate, è spesso vietato.

## Dove Posizionare il File *robots.txt*

Un file standard *robots.txt* è incluso nella root di Joomla. Il file
*robots.txt* deve risiedere nella root del dominio o del sottodominio e
deve essere chiamato `robots.txt`.

### Joomla in una Sottodirectory

Un file robots.txt situato in una sottodirectory non è valido. I robot
controllano questo file solo nella root del dominio. Se il sito Joomla è
installato in una sottodirectory come *example.com/joomla/*, il file
*robots.txt* **deve** essere spostato nella root del sito
*example.com/robots.txt*.

**Nota:** Nel file robots.txt, il nome della sottodirectory **deve** precedere tutti
i percorsi di Joomla non consentiti. Ad esempio, la regola di non consentire per la
directory `/administrator/` **deve** essere cambiata in `Disallow: /joomla/administrator/`.

## Contenuto di *robots.txt* di Joomla

Questa è il contenuto di un [file standard di robots.txt di Joomla](https://raw.githubusercontent.com/joomla/joomla-cms/refs/heads/5.2-dev/robots.txt.dist):

```
# Se il sito Joomla è installato all'interno di una cartella
# es. www.esempio.com/joomla/ allora il file robots.txt
# DEVE essere spostato nella root del sito
# es. www.esempio.com/robots.txt
# E il nome della cartella joomla DEVE essere prefisso a
# tutti i percorsi.
# es. la regola Disallow per la cartella /administrator/ DEVE
# essere cambiata in
# Disallow: /joomla/administrator/
#
# Per maggiori informazioni sullo standard robots.txt, vedi:
# https://www.robotstxt.org/orig.html

User-agent: *
Disallow: /administrator/
Disallow: /api/
Disallow: /bin/
Disallow: /cache/
Disallow: /cli/
Disallow: /components/
Disallow: /includes/
Disallow: /installation/
Disallow: /language/
Disallow: /layouts/
Disallow: /libraries/
Disallow: /logs/
Disallow: /modules/
Disallow: /plugins/
Disallow: /tmp/
```

## Esclusione dei robot

Puoi escludere delle directory o bloccare i robot dal tuo sito aggiungendo una
regola Disallow al file *robots.txt*. Ad esempio, per impedire a qualsiasi
robot di visitare la directory */tmp*, aggiungi questa regola:

    Disallow: /tmp/

Vedi anche:

- [Blocca l'accesso ai tuoi contenuti](https://support.google.com/webmasters/topic/4598466?hl=it&amp;ref_topic=9427949)
  presso il Centro assistenza di Google.

## Verifica della Sintassi

Per la verifica della sintassi, puoi utilizzare un validatore per i file *robots.txt*. Prova uno di questi:

- [Testa il tuo <em>robots.txt</em> con il tester di robots.txt](https://support.google.com/webmasters/answer/6062598) su Google.
- [<em>robots.txt</em> Checker](http://www.searchenginepromotionhelp.com/m/robots-text-tester/robots-checker.php) di Search Engine Promotion Help.

### Informazioni Generali

- [The Web Robots Pages](http://www.robotstxt.org/) è il sito principale per *robots.txt*.
- [A Standard for Robot Exclusion](http://www.robotstxt.org/orig.html) è lo standard originale.
- [Specifiche del meta tag Robots, data-nosnippet e X-Robots-Tag](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

*Tradotto da openai.com*

