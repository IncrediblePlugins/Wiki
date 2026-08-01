# Dialogs

Dialogs are Paper's native pop-up windows, used for confirmation prompts and
text inputs (for example, entering a player name or confirming an action). On
supported servers they replace the older chat-input prompts and confirmation
GUIs with a proper form window.

They are configured in the `..._dialogs.yml` file (e.g. `en-US_dialogs.yml`) in
the `/plugins/<plugin>/Locale` folder.

> **Requirements:** dialogs are only used on **Paper** (or a Paper fork),
> version **1.21.9 or newer**. On Spigot, older Paper versions, or for Bedrock
> players (via Geyser/Floodgate), the plugin falls back to chat input or a
> [Bedrock form](Bedrock-Forms.md)/GUI instead — so the `_dialogs.yml`
> file simply isn't loaded there.

All text is written in **MiniMessage** — see [Text Formatting](../config/Text-Formatting.md)
for colors, theme tokens (`<t:...>`) and placeholders (`<v:...>`). Dialogs render
on a dark panel, so `theme.yml`'s `theme.dialog` section adjusts the tokens for
that surface automatically; you use the same `<t:regular>` tags as everywhere
else.

# Structure

Each dialog is one entry under `dialogs:`, made up of an optional set of
`bodies` (descriptive text/icons), `inputs` (fields the player fills in) and
`buttons` (actions).

```yaml
dialogs:
  land_create:
    title: '<t:regular_heading>Create a New Land'
    bodies:
      info:
        text: '<t:regular>Creating this land will cost you<t:cost> <v:cost></t>.'
    inputs:
      name:
        label: Name
      tag:
        label: Tag
    buttons:
      confirm:
        label: '<t:positive>Create'
        tooltip: 'Click here to create a new land.'
      discard:
        label: '<t:negative>Discard'
        tooltip: 'Click to discard the land creation.'
```

## Title
`title` is the text shown at the top of the dialog window.

## Bodies
`bodies` are the descriptive blocks shown above the inputs. Each body has:

| Key | Description |
|---|---|
| `text` | The body text (MiniMessage). |
| `enabled` | Set to `false` to hide this body. Defaults to `true`. |
| `item` | *(optional)* An icon shown next to the text. Uses the same item format as [GUI items](GUI-Menus.md) (`material`, `hide-tooltip`, etc.). Add `decorations: true` to show the item's tooltip decorations. |

```yaml
bodies:
  tag:
    text: '<t:regular>The tag is the short version of your land''s name.'
    item:
      material: NAME_TAG
      hide-tooltip: true
```

## Inputs
`inputs` are the fields the player fills in. Every input has a `label`. The
`type` selects the field kind (defaults to `text` if omitted):

### Text (default)
A single-line text field.

```yaml
name:
  label: Name
  initial: ''        # optional: pre-filled text
  max-length: 32     # optional: maximum characters
```

### Boolean
A checkbox. Accepted type names: `boolean`, `bool`, `checkbox`.

```yaml
notify:
  type: boolean
  label: Notify members
  initial: true      # optional: checked by default
```

### Number range
A slider. Accepted type names: `number-range`, `range`, `slider`, `float`.

```yaml
days:
  type: number-range
  label: Days
  label-format: '<v:label>: <v:value>'   # how the slider label renders
  start: 0        # minimum
  end: 30         # maximum
  step: 1         # optional: increment
  initial: 0      # optional: starting value
```

In `label-format`, `<v:label>` is the input's `label` and `<v:value>` is the
currently selected number.

## Buttons
`buttons` are the actions at the bottom of the dialog. Each button has:

| Key | Description |
|---|---|
| `label` | The button text (MiniMessage). |
| `tooltip` | Hover text describing the action. |
| `width` | *(optional)* Button width in pixels. Defaults to `100`. |

```yaml
buttons:
  confirm:
    label: '<t:positive>Confirm'
    tooltip: 'Click here to confirm your input.'
  discard:
    label: '<t:negative>Discard'
    tooltip: 'Click to discard your input.'
    width: 150
```

By convention, confirm/accept actions use the `positive`/`success` theme tokens
and cancel/discard actions use `negative`/`error`.
