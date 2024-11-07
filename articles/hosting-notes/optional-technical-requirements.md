<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Requisiti Tecnici Opzionali -->

Questa pagina elenca i requisiti tecnici *opzionali* che non sono richiesti per installare ed eseguire Joomla!, ma sono necessari per alcune API interne. L'elenco è stato creato per Joomla 4.

| Elemento                  | Descrizione                                                                                                                                     |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **Applicazione**          |                                                                                                                                                 |
| JApplicationDaemon        | Richiede `ext/pcntl` e `ext/posix` di PHP                                                                                                       |
| **Archivio**              |                                                                                                                                                 |
| BZ2                       | Richiede `ext/bz2` di PHP                                                                                                                       |
| GZip                      | Richiede `ext/zlib` di PHP                                                                                                                      |
| Zip                       | Richiede `ext/zip` o `ext/zlib` di PHP                                                                                                          |
| **Cache**                 |                                                                                                                                                 |
| APC                       | Richiede `ext/apc` di PHP su PHP 5.3 o 5.4, `ext/apcu` su PHP 5.5 o 5.6, non supportato su PHP 7.x (Nota: QUESTO DEVE ESSERE VERIFICATO)       |
| APCu                      | Richiede `ext/apcu` di PHP su PHP 5.3+                                                                                                          |
| CacheLite                 | Richiede il pacchetto PEAR Cache_Lite (testato su 1.7.16, funzionerà con 1.8)                                                                   |
| Memcache                  | Richiede `ext/memcache` di PHP e un server Memcache (Nota: l'estensione Memcache non è compatibile con PHP 7.x)                                |
| Memcached                 | Richiede `ext/memcached` di PHP e un server Memcached                                                                                           |
| Redis                     | Richiede `ext/redis` di PHP e un server Redis                                                                                                   |
| Wincache                  | Richiede `ext/wincache` di PHP (solo Windows)                                                                                                   |
| XCache                    | Richiede `ext/xcache` di PHP                                                                                                                    |
| **Adattatori Client**     |                                                                                                                                                 |
| LDAP                      | Richiede `ext/ldap` di PHP                                                                                                                      |
| HTTP/Curl                 | Richiede `ext/curl` di PHP                                                                                                                      |
| HTTP/Socket               | Richiede che la funzione `fsockopen()` di PHP sia abilitata                                                                                    |
| HTTP/Stream               | Richiede la funzione `fopen()` di PHP e `allow_url_fopen` abilitato                                                                            |
| **Crittografia**          |                                                                                                                                                 |
| JCrypt                    | Richiede `ext/mcrypt` di PHP per tutti i cifrari eccetto il SodiumCipher che richiede `ext/sodium`                                             |
| JKeychain                 | Richiede `ext/openssl` di PHP                                                                                                                   |
| **Database**              |                                                                                                                                                 |
| Microsoft SQL Azure       | Richiede `ext/sqlsrv` di PHP (l'estensione PHP 5.x supporta solo Windows, una versione compatibile con Linux dell'estensione è disponibile per PHP 7.x)|
| Microsoft SQL Server      | Richiede `ext/sqlsrv` di PHP (l'estensione PHP 5.x supporta solo Windows, una versione compatibile con Linux dell'estensione è disponibile per PHP 7.x)|
| MySQL                     | Richiede `ext/mysql` di PHP (non supportato su PHP 7.x)                                                                                        |
| MySQLi                    | Richiede `ext/mysqli` di PHP                                                                                                                    |
| Oracle                    | Richiede `ext/pdo` di PHP con supporto Oracle (disponibile solo per 3PD; il CMS non funzionerà con esso)                                        |
| PDO MySQL                 | Richiede `ext/pdo` di PHP con supporto MySQL                                                                                                    |
| PostgreSQL                | Richiede `ext/pgsql` di PHP                                                                                                                     |
| SQLite                    | Richiede `ext/pdo` di PHP con supporto SQLite (disponibile solo per 3PD; il CMS non funzionerà con esso)                                        |
| **Immagine**              |                                                                                                                                                 |
|                           | Richiede `ext/gd` di PHP                                                                                                                        |
|                           | Richiede `ext/fileinfo` di PHP                                                                                                                  |
| **Sessione**              |                                                                                                                                                 |
| APC                       | Richiede `ext/apc` di PHP su PHP 5.3 o 5.4, `ext/apcu` su PHP 5.5 o 5.6, non supportato su PHP 7.x (Nota: QUESTO DEVE ESSERE VERIFICATO)       |
| Memcache                  | Richiede `ext/memcache` di PHP e un server Memcache (Nota: l'estensione Memcache non è compatibile con PHP 7.x)                                |
| Memcached                 | Richiede `ext/memcached` di PHP e un server Memcached                                                                                           |
| Wincache                  | Richiede `ext/wincache` di PHP (solo Windows)                                                                                                   |
| XCache                    | Richiede `ext/xcache` di PHP                                                                                                                    |
| **MIGLIORAMENTI OPZIONALI**|                                                                                                                                                 |
| **Stringa**               |                                                                                                                                                 |
| mbstring                  | Abilita `ext/mbstring` di PHP per la libreria phputf8 per utilizzare funzioni native                                                           |

*Tradotto da openai.com*
