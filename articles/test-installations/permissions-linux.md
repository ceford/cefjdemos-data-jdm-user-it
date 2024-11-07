<!-- Filename: Verifying_permissions / Display title: Permessi dei file: Linux -->

## Introduzione

Le seguenti informazioni sono per i server basati su Linux. Se il tuo server web è un server basato su Microsoft Windows (IIS), dovresti consultare [Permessi: Windows](jdocmanual?article=user/test-installations/permissions-windows).

A seconda della configurazione di sicurezza del tuo server web, i permessi predefiniti raccomandati sono:

- 755 per le directory
- 644 per i file
- 444 per il file `configuration.php` (quando viene salvata una modifica nella Configurazione Globale, Joomla prima cambia il permesso a 644, salva la modifica e poi riporta il permesso a 444)

<div class="alert alert-warning">
Avviso!

Non utilizzare mai 777 a meno che tu non sappia cosa stai facendo! Non utilizzare estensioni che richiedono permessi 777!
</div>

## Come Individuare i Permessi

Esistono diversi metodi disponibili per visualizzare e modificare i permessi dei file o delle cartelle di un sito web. Il file browser del pannello di controllo dell'host o un comune programma di 
[File Transfer Protocol (FTP)](https://en.wikipedia.org/wiki/File_Transfer_Protocol)
dovrebbero ciascuno fornire un metodo per vedere e modificare i permessi dei file e delle cartelle. La linea di comando è utile per coloro che hanno accesso al terminale e familiarità con i comandi di sistema.

A seconda di ciò che stai usando, dovresti vedere qualcosa come questa immagine di una parte del file system root di Joomla, come si vede in cPanel:

![verifica dei permessi in cpanel](../../../en/images/test-installations/verifying-permissions-cpanel.png)

I permessi sono all'estrema destra e preceduti da uno zero per indicare che sono numeri ottali. Dovrebbe esserci un modulo per modificare i permessi di uno o più elementi selezionati:

![cambiamento di permessi in cpanel](../../../en/images/test-installations/verifying-permissions-cpanel-change.png)

In una finestra del terminale, i permessi dei file e delle cartelle sono mostrati come gruppi di lettere piuttosto che numeri (la `d` iniziale indica che l'elemento è una directory):

```sh
drwxr-xr-x   20 ceford  staff     640 14 Oct 22:23 components
-r--r--r--    1 ceford  staff    3485 27 Oct 06:56 configuration.php
drwxr-xr-x    2 ceford  staff      64 20 Oct 14:21 files
-rw-r--r--    1 ceford  staff    6899 30 Sep 09:27 htaccess.txt
drwxr-xr-x   15 ceford  staff     480 24 Oct 12:19 images
```

## Numeri di Permesso

In una visualizzazione delle autorizzazioni nella forma 777, ogni cifra ottale corrisponde a 
tre lettere per tre diversi gruppi di utenti:

- Primo cifra = proprietario (il proprietario dell'elemento - `ceford` nella lista della riga di comando sopra)
- Seconda cifra = gruppo (il gruppo a cui è consentito l'accesso - `staff` nella lista sopra)
- Terza cifra = altri (tutti gli altri su questo computer)

## Significato dei numeri

Ogni cifra ottale è la somma delle autorizzazioni concesse:
```sh
     r = Leggere  = 4
     w = Scrivere = 2
     x = Eseguire = 1
```
Aggiungi i numeri per ciascuna autorizzazione richiesta per un determinato gruppo di utenti:

| Numero "Ottale" | (r)ead | (w)rite | e(x)ecute | Utente o Gruppo o Altri |
|-----------------|--------|---------|-----------|--------------------------|
| 0               | no     | no      | no        | `---` 0+0+0 = 0          |
| 1               | no     | no      | sì        | `--x` 0+0+1 = 1          |
| 2               | no     | sì      | no        | `-w-` 0+2+0 = 2          |
| 3               | no     | sì      | sì        | `-wx` 0+2+1 = 3          |
| 4               | sì     | no      | no        | `r--` 4+0+0 = 4          |
| 5               | sì     | no      | sì        | `r-x` 4+0+1 = 5          |
| 6               | sì     | sì      | no        | `rw-` 4+2+0 = 6          |
| 7               | sì     | sì      | sì        | `rwx` 4+2+1 = 7          |

## Esempi

- 755 è rwx (proprietario), r-x (gruppo) e r-x (altri) o, in altre parole, tutti possono leggere ed eseguire (eseguire) ma solo il proprietario (tu) può apportare modifiche al file. Apparirebbe in questo modo quando è tutto insieme: `-rwxr-xr-x`. Questa è la configurazione normale per le cartelle.
- 644 è rw-, r--, r-- o TUTTI possono leggere il file ma solo il proprietario può scrivere nel file o `-rw-r--r--`. Questa è la configurazione normale per i file.
- 777 o `-rwxrwxrwx` significa che TUTTI possono leggere, scrivere ed eseguire QUALSIASI file.
  <div class="alert alert-warning">
  Questa è una cosa che **NON** vuoi mai consentire sul tuo server/sito web a meno che non sei assolutamente sicuro di sapere cosa stai facendo.
  </div>

Le autorizzazioni sono usate sia per le directory che per i file, ed è per questo che potresti vedere `drwxr-xr-x` dove `d` sta per directory.

Per una spiegazione completa leggi l'articolo di Wikipedia su 
[Permessi del filesystem](https://en.wikipedia.org/wiki/Filesystem_permissions)

*Tradotto da openai.com*

