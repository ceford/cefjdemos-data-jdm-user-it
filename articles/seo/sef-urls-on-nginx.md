<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: URL SEF su Nginx -->

## Introduzione

Gli URL SEF (Search Engine Friendly), leggibili da umani o puliti sono URL che hanno senso sia per gli esseri umani sia per i motori di ricerca, poiché spiegano il percorso verso la pagina particolare a cui fanno riferimento. Joomla! è in grado di creare e interpretare URL in qualsiasi formato, inclusi gli URL SEF. Questo non dipende dalla riscrittura degli URL eseguita dal server web, quindi funziona anche se Joomla! gira su un server diverso da Apache con il modulo mod_rewrite. Gli URL SEF seguono un certo schema fisso, ma l'utente può definire un breve testo descrittivo (alias) per ogni segmento dell'URL.

Internamente, la parte locale di un URL SEF (la parte dopo il nome del dominio) è chiamata percorso. Creare e processare URL SEF è quindi chiamato routing, e il codice pertinente è chiamato router.

Questo articolo tratta degli URL SEF sotto il popolare server web open-source Nginx.

## Passaggi per server NginX¶

- Aggiungi il seguente codice alla configurazione del tuo server (vhost) nel file nginx.conf:

```
    # Supporto per URL puliti (detti anche URL amichevoli per i motori di ricerca)
    location / {
       try_files $uri $uri/ /index.php?$args;
    }
```
- Se quanto sopra non funziona, aggiungi il seguente codice alla configurazione del tuo server nel file nginx.conf: (Questo ha funzionato con nginx 1.4.6 su Ubuntu.)
```
    server {
      ....
      location / {
      expires 1d;

      # Abilita URL SEF di joomla all'interno di Nginx
      try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```
- Effettua il login al tuo Backend e apri la Configurazione Globale
- Abilita l'opzione **URL amichevoli per i motori di ricerca** e Salva. Questa opzione converte gli URL dal formato nativo di Joomla! al formato SEF. Verifica che il tuo sito funzioni correttamente. I tuoi URL dovrebbero ora apparire come `http://www.example.com/index.php/the-­news/1-­latest­-news/1­-welcome­-to­-joomla`. Se il tuo sito non funziona correttamente, consulta [Perché il tuo sito si incasina quando attivi gli URL amichevoli per i motori di ricerca?](https://docs.joomla.org/Why_does_your_site_get_messed_up_when_you_turn_on_SEF_(Search_Engine_Friendly_URLs)%3F)
- Abilita l'opzione **Utilizza URL rewriting di Apache mod_rewrite** e Salva. Questa opzione utilizza la funzione Apache mod_rewrite per eliminare la parte *index.php* dall'URL. Verifica che il tuo sito funzioni correttamente. I tuoi URL dovrebbero ora apparire come `http://www.example.com/the-­news/1­-latest-­news/1-­welcome-­to­-joomla`. Se questa opzione causa errori, consulta [Come verificare se il mod rewrite è abilitato sul tuo server](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server). Se non è abilitato e hai accesso al file `apache/conf/httpd.conf`, apri quel file e verifica che la riga `LoadModule rewrite_module modules/mod_rewrite.so` non sia commentata. Se necessario, rimuovi il commento dalla riga e riavvia il server web Apache. Se *mod_rewrite* non può essere abilitato, lascia disabilitata questa opzione. Non importa se lasci il file `.htaccess` rinominato.
- *Se pensi che sia necessario*, abilita **Aggiungi suffisso agli URL** e *Salva*. Questa opzione aggiunge `.html` alla fine degli URL. Ci sono opinioni diverse sulla necessità o utilità di questa funzione. I motori di ricerca sembrano non preoccuparsi se i tuoi URL terminano con `.html` o meno.
- Apri il Plugin Manager e abilita il plugin **Sistema - SEF**. Questo plugin aggiunge supporto SEF ai link nei tuoi articoli Joomla. Funziona direttamente sull'HTML e non richiede un tag speciale.

*Tradotto da openai.com*

