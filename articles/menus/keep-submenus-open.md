<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Mantieni aperti i sottomenu",
    "description": " ",
    "author": ""
}
-->

Un modulo menu può essere utilizzato per visualizzare un menu orizzontale (solitamente nella parte superiore della pagina) o un menu verticale (solitamente in una barra laterale, a sinistra o a destra). In un menu orizzontale (superiore) non è desiderabile mantenere aperto il sottomenu. Per questo motivo, il comportamento predefinito di un modulo menu consiste nel chiudere i sottomenu al caricamento della pagina.

## Comportamento dell'opzione *aperto*

Tuttavia, in un menu verticale (barra laterale), spesso è desiderabile lasciare aperto un sottomenu quando contiene la voce di menu attiva. In Joomla 6.0 è stata introdotta una nuova classe CSS, `nav-active-open`, specificamente per consentire il controllo dell'apertura automatica dei sottomenu al caricamento della pagina per la voce di menu attiva. L'impostazione di questa classe consente ora di ottenere questo risultato. La classe viene impostata nel modulo tramite il backend.

![impostazione della classe del menu nel backend per nav-active-open per mantenere aperto il menu attivo](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## Come creare un menu della barra laterale senza il toggle a discesa

Se vuoi mantenere aperti tutti i sottomenu, non hai bisogno di un toggle a discesa. Usa invece un [override del template](jdocmanual?article=user/templates/template-overrides).

Questo è il modo in cui viene realizzato questo particolare override del template:

1. Inizia selezionando Sistema → Template → Template del sito nel menu Amministratore, quindi seleziona l'elemento Dettagli e file di Cassiopeia. Si aprirà il modulo Template: Personalizza (Cassiopeia).

2. Passa alla scheda Crea override e seleziona mod_menu:

![selezione dell'override del template del modulo menu](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

In questo modo tutti i file di layout del menu verranno copiati dal modulo menu nell'override. Torna quindi alla scheda Editor.

3. Nella scheda Editor, espandi le voci sotto HTML → mod_menu. Qui troverai il file `default.php`. Apri il file e copiane il contenuto in un luogo sicuro. Chiudi il file.

4. Crea un nuovo file nella cartella html → mod_menu. Il nome non deve contenere un carattere di sottolineatura. In questo esempio il nuovo file si chiama `treedefault.php`. Questo consente di selezionare il layout del menu predefinito oppure questo layout alternativo in uno qualsiasi dei moduli menu. Nell'elenco seguente dei file di override, l'originale è evidenziato in rosso e la nuova alternativa è evidenziata in verde.

![scheda di modifica dell'override mod_menu - apertura di default.php](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Modifica il nuovo file di layout. I passaggi seguenti sono elencati in ordine inverso per
preservare i numeri di riga durante il processo di modifica:

Modifica la riga 104 in modo che contenga quanto segue:

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Questo mantiene aperto il menu e aggiunge il rientro ai sottomenu.

Sostituisci le righe 98 - 101 con `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Rimuovi le righe 93 - 94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Rimuovi le righe 66-71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Rimuovi le righe 15 - 20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Questo è il file di override `treedefault.php` completo:

```
<?php

/**
 * @package     Joomla.Site
 * @subpackage  mod_menu
 *
 * @copyright   (C) 2009 Open Source Matters, Inc. <https://www.joomla.org>
 * @license     GNU General Public License version 2 or later; see LICENSE.txt
 */

defined('_JEXEC') or die;

use Joomla\CMS\Helper\ModuleHelper;
use Joomla\CMS\Language\Text;

$tagId      = $params->get('tag_id', '') ?: 'mod-menu' . $module->id;
$id         = ' id="' . htmlspecialchars($tagId, ENT_QUOTES, 'UTF-8') . '"';
$startLevel = (int) $params->get('startLevel', 1);

// The menu class is deprecated. Use mod-menu instead
?>
<ul<?php echo $id; ?> class="mod-menu mod-list nav <?php echo $class_sfx; ?>">
<?php foreach ($list as $i => &$item) {
    $itemParams = $item->getParams();
    $class      = 'nav-item item-' . $item->id;

    if ($item->id == $default_id) {
        $class .= ' default';
    }

    if ($item->id == $active_id || ($item->type === 'alias' && $itemParams->get('aliasoptions') == $active_id)) {
        $class .= ' current';
    }

    if (in_array($item->id, $path)) {
        $class .= ' active';
    } elseif ($item->type === 'alias') {
        $aliasToId = $itemParams->get('aliasoptions');

        if (count($path) > 0 && $aliasToId == $path[count($path) - 1]) {
            $class .= ' active';
        } elseif (in_array($aliasToId, $path)) {
            $class .= ' alias-parent-active';
        }
    }

    if ($item->type === 'separator') {
        $class .= ' divider';
    }

    if ($item->deeper) {
        $class .= ' deeper';
    }

    if ($item->parent) {
        $class .= ' parent';
    }

    echo '<li class="' . $class . '">';

    switch ($item->type) :
        case 'separator':
        case 'component':
        case 'heading':
            require ModuleHelper::getLayoutPath('mod_menu', 'default_' . $item->type);
            break;
        default:
            require ModuleHelper::getLayoutPath('mod_menu', 'default_url');
            break;
    endswitch;

    // The next item is deeper.
    if ($item->deeper) {
        // Check type - add only on first level
        // @todo aria-label - set in menu item ???
        if ((int) $item->level === $startLevel) {
            switch ($item->type) {
                case 'heading':
                case 'separator':
                    break;

                default:
                    break;
            }
        }
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
    } elseif ($item->shallower) {
        // The next item is shallower.
        echo '</li>';
        echo str_repeat('</ul></li>', $item->level_diff);
    } else {
        // The next item is on the same level.
        echo '</li>';
    }
}
?></ul>
```

## Risultato

Il risultato è un elenco semplice, senza funzionalità di toggle per il modulo menu della barra laterale, illustrato qui a sinistra:

![risultato con override del template - elenco semplice senza pulsanti e funzionalità di toggle](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Tradotto da openai.com*
