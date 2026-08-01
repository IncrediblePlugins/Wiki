# Messages

Message files live in `/plugins/<plugin>/Locale` (the folder was previously
called `Language`). The chat/command messages are in the main locale file, e.g.
`en-US.yml`. You can place multiple locales in the folder to display different
languages depending on the player's client locale.

All values are written in **MiniMessage** format — see
[Text Formatting](Text-Formatting.md) for colors, decorations, theme tokens
(`<t:...>`) and placeholders (`<v:...>`). This page covers the message-specific
tags: titles, action bars, boss bars, clickable text and prefix control.

# Display a Message

By default a value is sent as a normal chat message. A tag at the start of the
value changes how it is delivered instead.

## As a Title

Start the value with `<title>` (optionally with fade timings
`<title:in:stay:out>`). Use `<subtitle>` and `<actionbar>` inside the same value
to split it into the title, subtitle and action-bar parts.

```yaml
pvp-warning: '<title:10:60:5><t:error>You entered a pvp zone.<subtitle><t:regular>Watch out!'
```

`in` is the fade-in time, `stay` the stay time and `out` the fade-out time,
given in ticks (20 ticks = 1 second) and optional. This example fades in over
half a second, stays for 3 seconds and fades out over 0.25 seconds.

## As an Action Bar

Start the value with `<actionbar>`:

```yaml
pvp-warning: '<actionbar><t:error>You entered a pvp zone.'
```

## As a Boss Bar

Start the value with `<bossbar:color:style:time>`:

```yaml
pvp-warning: '<bossbar:green:solid:6><t:error>You entered a pvp zone.'
```

`color`, `style` and `time` (seconds) are optional. This boss bar is green,
solid and lasts 6 seconds. See the list of
[bar colors](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/boss/BarColor.html)
and [bar styles](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/boss/BarStyle.html).

# Colors & Placeholders

Colors, hex colors, theme tokens (`<t:...>`) and placeholders (`<v:...>`,
`%papi%`) all work in messages — see [Text Formatting](Text-Formatting.md).

# PlaceholderAPI

You can use placeholders from 3rd party plugins via PlaceholderAPI in chat
messages and [GUI menus](GUI-Menus.md), with the usual `%placeholder%` syntax.

# Clickable Chat Messages

Make text clickable or hoverable with MiniMessage's `<click>` and `<hover>`
tags. (Note: this doesn't apply to plain strings like the prefix.)

* **Hover text:**
  ```yaml
  msg: '<hover:show_text:"<t:regular>This is a hover"><t:cmd>Hover me</hover>'
  ```
* **Run a command on click:**
  ```yaml
  msg: '<click:run_command:"/lands help"><t:cmd>Click to run</click>'
  ```
* **Suggest a command (put it in the chat box):**
  ```yaml
  msg: '<click:suggest_command:"/lands help"><t:cmd>Click to suggest</click>'
  ```
* **Open a URL:**
  ```yaml
  msg: '<click:open_url:"https://example.com"><t:cmd>Open link</click>'
  ```

You can nest them, and combine with colors/placeholders:

```yaml
invite: |-
  <t:regular>Player <t:regular_value><v:player></t> invited you to join
  <t:entity_land><v:land></t>.
  <hover:show_text:"<t:regular>Click to accept."><click:run_command:"/lands accept <v:land>"><t:success>[Accept]</click></hover>
  <hover:show_text:"<t:regular>Click to deny."><click:run_command:"/lands deny <v:land>"><t:error>[Deny]</click></hover>
```

> The text **inside the quotes** of `run_command` / `suggest_command` /
> `open_url` is a literal command/URL — don't wrap it in color tags. Only the
> visible text between `>` and `</click>` is styled.

# Disable a Message

Set the value to an empty string. For example, to disable the land enter/leave
title messages:

```yaml
enter:
  land: ''
  safezone: ''
```

The messages won't display anymore.

# Disable the Prefix for a specific Message

Put `<noprefix>` at the very start of the value:

```yaml
info: |-
  <noprefix><t:decoration><st>━━━━━━━━━<━</st> <t:regular_heading>Rent Area</t> <t:decoration><st>━>━━━━━━━━━</st>
  <hover:show_text:"<t:regular>Click to visualize."><click:run_command:"/lands view here"><t:regular>Land: <t:regular_value><v:land></click></hover>
  <t:regular>Cost: <t:cost><v:cost></t> each <t:time><v:time></t>
```

# Verbose / In-game-only content

* `<verbose>...</verbose>` — only shown when verbose mode is enabled for the
  recipient.
* `<ingame>...</ingame>` — only shown to in-game recipients (never in external
  outputs like a Discord bridge).

Keep these tag pairs; the text inside is normal message text.

# Filter Swear Words and forbidden Names

Edit the `swear-words` list in your locale file. Entries are case-insensitive.

```yaml
swear-words:
  - 'test'
  - 'test2'
```
