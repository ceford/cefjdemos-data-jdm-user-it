<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Campo nota",
    "description": " ",
    "author": ""
}
-->

## Scopo

Il tipo di campo modulo nota consente di creare titoli, testi, descrizioni e persino riquadri di avviso. Consente inoltre di organizzare le impostazioni delle estensioni, separandole con titoli utili. Oppure di aggiungere descrizioni per determinate impostazioni (senza dover ricorrere ai tooltip). O di aggiungere qualsiasi altro testo desiderato.

## Creazione del campo

### Scheda Generale

![Creazione del campo nota](../../../en/images/fields/adding-custom-fields-note-field/01-fields-note-edit.png)

- **Tipo** Numero, che non può essere modificato dopo la selezione.
- **Nome** Il nome univoco del campo.
- **Etichetta** Un'etichetta traducibile per il campo.
- **Descrizione** Una descrizione facoltativa e traducibile del campo.
- **Usa solo nel sottoformulario** *Sì* o *No*.
- **Intestazione della nota** Verrà visualizzata nel modulo di inserimento dati.
- **Contenuto della nota** Il testo della nota.
- **Classe della nota** Qualsiasi classe esistente o nuova. L'impostazione predefinita *alert alert-info* produce un riquadro di avviso Bootstrap.
- **Tag dell'intestazione** Selezionare dall'elenco dei livelli di intestazione.
- **Mostra pulsante di chiusura** Questo campo controlla la visualizzazione di una "x" per chiudere la nota. Accetta il valore "true" (per gli avvisi) oppure il valore per l'attributo data-dismiss dell'icona di chiusura di Bootstrap.

### Scheda Opzioni

- **Visualizzazione automatica** Se e dove visualizzare il campo:
    - **Dopo il titolo**
    - **Prima del contenuto visualizzato**
    - **Dopo il contenuto visualizzato**
    - **Non visualizzare automaticamente**
- **Layout** un elenco dei layout disponibili.
- **Visualizza nel frontend** *Sì* o *No*.

## Inserimento dati

Nel modulo di inserimento dati, il campo nota appare tra gli altri campi come testo formattato in base alle scelte di stile impostate nel campo. Potrebbe contenere istruzioni o informazioni.

![Inserimento dati del campo numero](../../../en/images/fields/adding-custom-fields-note-field/02-fields-note-data-entry.png)

**Suggerimento:** Utilizza il meccanismo di ordinamento dei campi per ordinare la posizione della nota tra gli altri campi. Puoi avere diversi campi Nota per fornire struttura e informazioni ai tuoi campi.

## Visualizzazione dei dati

Se *Visualizza nel frontend* è impostato su *Sì*, il campo Nota appare tra gli altri campi nel frontend. Potrebbe contenere informazioni generali comuni a un gruppo di articoli.

*Tradotto da openai.com*