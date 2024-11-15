# General
The GUI file is located under `/plugins/<plugin>/Language` whereas `<plugin>` needs to be replaced with the plugin name. For Bedrock client forms, please see [this page](Bedrock-Forms.md).
You can place multiple locales in the plugin's Language folder to display different locales depending on the player's locale.

# PlaceholderAPI Placeholders
PlaceholderAPI placeholders are supported in all menus, titles, items and commands.

# Remove a Menu from `/<cmd> menu`
Add `menu-cmd: false` to the menu.
If you want to disable an item, look [here](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#disable-items).

# Hex Colors
You can use hex colors everywhere. Example: `#4287f5Test` - `Test` will be colored with `#4287f5`

# Slots
You can combine slot ranges. This includes slots for items and slots for list entries. Example:
````yaml
slots: 
  - '1-5'
  - '7'
  - '8-9'
````
It's exactly the same for the list menus entries definitions:
````yaml
entries: 
  - '1-5'
  - '7'
  - '8-9'
````

# Item Types
## Entry
Item keys starting with the `entry_` prefix apply to list menus in the defined entries ranges.

## Child
Child items appear as feedback when clicking on specific items. For example, letting a player know that they can't untrust a claim owner.
These items are temporary and will disappear after `1.5 + 1.5 * lore length` seconds.

## Refresh
These items trigger a complete refresh of the menu when clicked. In the default configuration, they're mostly used for pagination or sorting lists.

## Placeholder
Item keys starting with the `placeholder_` prefix are placeholders.

# Common Sounds
In this section, you can define sounds that apply to a range of items.
````yaml
# These are applied to all items starting with the defined prefix.
common_sounds:
  # Play a sound when the item is set in the menu.
  set:
    # Each item starting with [item_type]_failure_<name> will have this sound set.
    # You can still override the "sound_set" for any item in their sections.
    failure: ENTITY_VILLAGER_NO
  # Play a sound when the item is clicked.
  set:
    failure: ENTITY_VILLAGER_NO
````


# Common Items Section
The common section lets you define items that will apply to every menu.
Items in the default configuration may not apply to every menu. Only menus that they're meant to apply. In the default configuration, all menus have the same size of 45. Therefore, this size is specified here. You can override any item or setting of the common section in the menu of your choice, by following the instructions here:
[How to add your own items.](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#add-your-own-items-to-a-menu)

````yaml
common:
  size: 45
  entries: 10-36
  # Automatically correct slots if menus, that inherit items from this section, have a smaller size?
  # If this is disabled, items, which slots go over the menu size, will be set to slot 0 instead.
  # To manually override the slots for a common item in a menu, 
  # just define this item in the custom section of the menu.
  auto-correct: true
  items:
    default:
      back:
        name: '&c&lBack'
        lore:
        - '&8✖ &7Go back to'
        - '   &7{back}.'
        material: RED_STAINED_GLASS_PANE
        slots: 37
      refresh_page_previous:
        name: '&c&lPrevious Page'
        lore:
        - '&8✖ &7Go to previous page:&3 {previous}'
        material: ARROW
        slots: 39
      refresh_page_next:
        name: '&a&lNext Page'
        lore:
        - '&8✖ &7Go to next page:&3 {next}'
        material: ARROW
        slots: 44
      placeholder_1:
        material: GRAY_STAINED_GLASS_PANE
        slots: 1-45
````

# Optional Item Parameters
All of our GUI menus feature full customization of the whole item language and also positions etc.
Here are some optional item parameters, which can be added to items:

## Disable Items:
Add `enabled: false` to the item.

## Set custom Model-Data:
Add `model-data: NUMBER` to the item.

## Set Item Amount
Add `amount: NUMBER` to the item.

## Display as enchanted
Add `enchanted: true` to the item.

## Specific enchantments
The format is as follows: `namespace:enchantment:level`\
Whereas, `namespace` is either "minecraft" for vanilla enchantments or a custom namespace for enchantments from 3rd party plugins. A custom namespace depends on which one the 3rd party plugin developer chose. `enchantment` equals the enchantment name. `level` is optional.
````yaml
carrot:
  name: 'A sharp Carrot'
  enchants:
   - 'minecraft:sharpness'
  material: 'CARROT'
````

## Click Sound
Play a sound when a player clicks on the item.
The `<volume>` and `<pitch>` parameters are optional and may be replaced with the sound's preferred volume and pitch.
````yaml
item:
  name: 'Name'
  lore:
   - 'Lore'
  material: STONE
  slots: 26
  sound_click: 'BLOCK_NOTE_BLOCK_BASS:<volume>:<pitch>'
````

## Set Sound
Plays a sound when the item is set in the menu. This is especially useful for temporary items, that display failures. The `<volume>` and `<pitch>` parameters are optional and may be replaced with the sound's preferred volume and pitch.
````yaml
      child_failure_page_next:
        sound_set: ENTITY_VILLAGER_NO:<volume>:<pitch>
````

## Execute Commands at Click
This supports PlaceholderAPI placeholders.
````yaml
item:
  name: 'Name'
  lore:
   - 'Lore'
  material: STONE
  slots: 26
  commands:
   - 'say test'
````

## Execute Command as Console
You can execute a command as the console by wrapping it into `[C]cmd[/C]`. Replace `cmd` with the command of your choice. Warning: Only do this if you know what the command does. The console has all permissions.

## Open Menu
If you want to open a specific menu for a player, you can use `/<plugin> menu <menu> [args]`. This may not be available for all plugins.

## Close Menu
If you want to close a menu for a player, you can use the `/<plugin> menu close` command. Just replace `<plugin>` with the name of the plugin. Example: `/lands menu close`.

# Add your own Items to a Menu
1. Add the `custom` section to the menu in your GUI file.
2. Configure the in the same format as default items. You can also override items from the [common section](https://github.com/Angeschossen/General/wiki/GUI-Menus/#common-section).
````yaml
main:
  title: '&8Main Menu'
  items:
    default:
      lands:
        name: '&2&lYour Lands'
        lore:
         - '&8✖ &7Manage your lands:'
         - '   &7This includes your own lands'
         - '   &7and lands, in which you''re'
         - '   &7trusted.'
         - ''
         - '    &8• &7Own: {own}'
         - '    &8• &7Trusted: {trusted}'
        material: GRASS_BLOCK
        slots: 20
        
    custom:
      my-item:
        name: 'Name'
        lore:
         - 'Lore'
        material: STONE
        slots: 26
````

# Conflicting Slot Ranges
If you get a warning in your console that items have conflicting slot ranges, you need to edit your GUI file. Find the conflicting items and edit their slots in a way that they don't overlap and don't exceed the size of the menu. Otherwise, items might not display correctly.

# Custom Head Textures
Just use `skin:<minecraft-url>` as the material for an item. Example:
````yaml
item:
  name: 'Name'
  lore:
   - 'Lore'
  material: skin:http://textures.minecraft.net/texture/18c0ca8fae701314330fdfdded3445e4542a3597b70d38f47d75111eb04104b8
  slots: 26
````

You can find the URL on pages like [minecraft-heads.com](https://minecraft-heads.com/). Example:
![](https://imgur.com/nENavTq.png)
