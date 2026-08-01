# Text Formatting (MiniMessage)

All text in the locale files — chat messages, GUI item names and lore, Bedrock
forms and dialogs — is written in [Adventure MiniMessage](https://docs.papermc.io/adventure/minimessage/)
format.

> **The old `&` / `§` color codes are gone.** Legacy `&c`, `§a`, and the
> `#4287f5SomeText` hex-prefix format are no longer used for the plugin's own
> output. If you copy an old example that uses `&`-codes, it won't color the
> text — convert it to MiniMessage (`<red>...`) instead.

## Colors

Wrap the text you want to color in a tag:

```yaml
name: '<red>This is red</red> and <#4287f5>this is a custom hex color'
```

* Named colors: `<red>`, `<green>`, `<gray>`, `<gold>`, … (the full
  [MiniMessage color list](https://docs.papermc.io/adventure/minimessage/format/#color)).
* Hex colors: `<#4287f5>` (or `<color:#4287f5>`).
* Gradients / rainbow: `<gradient:#ff0000:#0000ff>text</gradient>`,
  `<rainbow>text</rainbow>`.

A tag stays active until the end of the line or until it is closed/overridden.
You can close a color explicitly with `</red>` or reset everything with
`<reset>`.

## Decorations

| Tag | Effect | Turn back off |
|---|---|---|
| `<b>` | **Bold** | `<!b>` |
| `<i>` | *Italic* | `<!i>` |
| `<u>` | Underline | `<!u>` |
| `<st>` | ~~Strikethrough~~ | `<!st>` |
| `<obf>` | Obfuscated | `<!obf>` |

The negated forms (`<!b>`, `<!st>`, …) switch a single decoration off without
closing the surrounding color tag the way `<reset>` would.

## Line breaks

Use `<newline>` (or its alias `<br>`) for a line break:

```yaml
message: '<gray>First line<newline>Second line'
```

In **GUI item lore**, `<newline>` also splits the value into separate lore
lines, so you can write a whole multi-line lore on one YAML line. (You can still
use a normal YAML list of lines instead — both work.)

## Literal `<`

Because `<` starts a tag, a `<` that should appear as visible text must be
escaped as `\<`. A plain `>` only needs escaping when it would close a tag that
is actually open. This almost only comes up in decoration (e.g. arrows); normal
text never needs it.

## Theme Color Tokens: `<t:token>`

Instead of hardcoding a color like `<red>`, the default locale files reference a
named **theme token** with `<t:name>`:

```yaml
denied: '<t:error>You can''t do that here.'
```

`error`, `success`, `regular`, `regular_value`, … are tokens defined once in
`Locale/theme.yml`. Changing a token's color there re-colors **every** message
that uses it, across all locale files, without editing the messages themselves —
this is the recommended way to re-theme a plugin.

```yaml
# Locale/theme.yml
theme:
  tokens:
    error: '<red>'          # change this to recolor every <t:error> message
    success: '<green>'
    regular: '<gray>'
```

* A token's value is full MiniMessage syntax, so it can carry decorations too:
  `heading: '<gold><b>'`.
* Only color/decoration tags are allowed in a token value — not `<click>`,
  `<hover>` or gradients.
* `theme.yml` also has `theme.gui`, `theme.dialog` and `theme.bedrock` sections
  that override specific tokens **for that surface only** (e.g. dialogs and
  Bedrock forms render on dark panels, so body text may need to be white there
  instead of gray). This is applied automatically — the same `<t:regular>` tag
  works everywhere.
* `theme.yml` is **not** per-language. It is shared by every locale; never
  duplicate or translate it.

### Closing a token

`</t>` closes the nearest open `<t:...>` and returns to the previous style.
Closing an outer tag also closes any tags still open inside it, so
`<t:heading><b>Text</t>` closes both the color and the bold at once.

## Placeholders: `<v:name>`

Dynamic values (a land name, a cost, a player) are inserted with the namespaced
`<v:name>` tag:

```yaml
welcome: '<t:regular>Welcome to <t:regular_value><v:land></t>, <v:player>!'
```

> **Placeholders are `<v:name>`, not `{name}`.** The old `{name}` / `{player}`
> curly-brace style has been replaced. Which placeholder names are available
> depends on the message — use the names already present in the default value
> for that key.

An unknown `<v:name>` doesn't crash; it just renders as literal text, so a typo
shows up as visible `<v:whatever>` in-game rather than an error.

### PlaceholderAPI

PlaceholderAPI placeholders still use the `%name%` form and work in messages,
GUI menus, item names/lore, titles and commands:

```yaml
owner: '<t:regular>Owner: <t:regular_value>%owner%'
```
