Messages file: `/plugins/<plugin>/Language`
You can place multiple locales in the plugin's "Language" folder to display different locales depending on the player's client locale.

# Display a Message
## As a Title
Just add `#t#` in front of the message.\
Example: 
```yaml
pvp-warning: '#t#[config]in:10,stay:60,out:5[/config]&cYou entered a pvp zone.[newline]Subtitle (optional)[newline]Actionbar (optional)'
```

Whereas `in` is the fade in time, `stay` the stay time and `out` the fade out time. These are provided in ticks (20 ticks = 1 second) and are optional. This title would fade in half a second, stay for 3 seconds and fade out for 0.25 seconds. The times in this example are the default ones.

## As an Actionbar
Just add `#a#` in front of the message.\
Example: 
```yaml
pvp-warning: `'#a#&cYou entered a pvp zone.'
```

## As a Bossbar
Just add `#b#` in front of the message.\
```yaml
Example: pvp-warning: `'#b#[config]color:green,style:solid,time:6[/config]&cYou entered a pvp zone.'`
```
Whereas color, style and time are optional configuration options. This bossbar would be solid, green and would last 6 seconds. Click [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/boss/BarColor.html) to see a list of available colors.

# Hex Colors
You can use hex colors by just adding the hex color code in front of any text.\
Example: `#4287f5SomeFancyName` where `#4287f5` is the hex color code and `SomeFancyName` the colored text.

# PlaceholderAPI
You can use placeholders from 3rd party plugins via PlaceholderAPI in chat messages and [GUI menus](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#placeholderapi-placeholders).

# Clickable Chat Messages
You can make every chat message clickable. Means you can set a hover, command or suggested command (copy to cmd input). Please note that this is not applicable to general strings like prefix etc.

## Configure Custom Text:
* Syntax for custom text:
```yaml
[T]Custom text[/T]
```
* Hover:
```yaml
[T]Custom text[H]This is a hover[/H][/T]
```
* Execute command:
```yaml
[T]Custom text[H]This is a hover[/H][C]Lands help[/C][/T]
```
* Suggest command:
```yaml
[T]Custom text[H]This is a hover[/H][SC]Lands help[/SC][/T]
```

***

#### Example Usage:
```yaml
[T]&7Player&3 {player} &7invited you to join their land&2 {land}&7.[H]&7Click to open your invites menu.[/H][C]lands invites[/C][/T] &7Taxes:&c 
${tax}

  [T]&2Accept &8[&8CLICK&8][H]&7Click here to accept this invite.[/H][C]lands accept {land}[/C][/T]
  [T]&cDeny &8[&8CLICK&8][H]&7Click here to deny this invite.[/H][C]lands deny {land}[/C][/T]
```

#### Will display as:
![Result of the example above.](https://i.imgur.com/BeOkyZs.png)

# Disable messages
Example: Disabling land enter messages in Lands:
```yaml
    enter:
      land: '#t#&2&l{land}[newline]&3{title}'
      safezone: '#t#&2&l{land}[newline]{title}'
```
Set them to an empty string:
```yaml
    enter:
      land: ''
      safezone: ''
```
The welcome messages won't display anymore.

# Disable the prefix for a specific Message
Just insert `[noprefix]` in front of the message. Example:
```yaml
      info: |
        [NoPrefix]
        &7&m━━━━━━━━━<━&r &5&lRent Area &7&m━>━━━━━━━━━
        [T]&7Land:&a {land} &8[&8CLICK&8][H]&7Click here to visualize this area.[/H][C]lands view here[/C][/T]
         &7Area:&6 {area}
         &7Cost:&c {cost} &7each {time}
         &8Max time: {max}
        &7&m━━━━━━━━━<━&r &5&lRent Area &7&m━>━━━━━━━━━
```

# Filter Swear Words and forbidden Names
Edit the `swear-words` list in your language file. They are case-insensitive.
Example:
```yaml
swear-words:
  - 'test'
  - 'test2'
```
