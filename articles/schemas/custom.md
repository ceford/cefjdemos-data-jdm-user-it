<!-- Filename: Localhost / Display title: Schema.org - Personalizzato -->

## Scopo

Il plugin dello schema personalizzato viene utilizzato per inserire informazioni personalizzate in formato JSON-LD grezzo. Non è un tipo di Schema Org.

Apri un modulo di modifica dell'articolo e seleziona la scheda Schema per selezionare un tipo di Schema e impostare i dati per quel tipo. Se un tipo di Schema non è presente nell'elenco, è possibile che il suo Plugin sia disabilitato. I valori da inserire in ciascun campo sono per lo più evidenti.

Questo è un esempio di rich snippet creato manualmente:

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Your Article Title",
  "description": "A brief description of the article.",
  "timeRequired": "PT5M"
}
```

La proprietà *timeRequired* rappresenta il tempo di lettura stimato nel formato di durata ISO 8601. In questo caso, PT5M significa *5 minuti*.

## Screenshot d'Esempio

Di seguito è riportato un esempio di campo schema personalizzato in un modulo di modifica articolo.

![A custom schema edit form](../../../en/images/schemas/edit-schema-custom.png)

*Tradotto da openai.com*

