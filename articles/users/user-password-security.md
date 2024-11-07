<!-- Filename: J5.x:Enhancing_Password_Security_with_Symbolic_Characters / Display title: Sicurezza della Password Utente  -->

## Introduzione

Nel modulo *Utenti: Opzioni*, nella scheda *Opzioni Password*, i valori minimi per *Numeri*, *Simboli*, *Maiuscole* e *Minuscole* sono tutti impostati su 0 per impostazione predefinita. Per una maggiore sicurezza, questi valori dovrebbero essere impostati su 1. Le nuove password o quelle modificate devono quindi includere uno di ciascuno di questi caratteri.  

## Simboli

L'*Open Worldwide Application Security Project* (OWASP) raccomanda che tutti i caratteri speciali disponibili su una tastiera standard statunitense siano riconosciuti e accettati quando si impostano i requisiti per le password.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Non è ovvio, ma questo elenco include il carattere spazio.

[OWASP: Caratteri Speciali delle Password](https://owasp.org/www-community/password-special-characters)

Prima della versione 5.2, questi simboli potevano essere usati nelle password, ma alcuni di essi non erano riconosciuti come simboli ai fini della convalida delle password:
```
@[]£^+±~<>/'",.
```

*Tradotto da openai.com*

