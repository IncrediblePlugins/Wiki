Bedrock players can join Java Edition Minecraft servers with the help of the
[Geyser and Floodgate](https://geysermc.org/) plugins.

# Menus Are Auto-Generated for Bedrock

When **Floodgate is installed**, the plugin automatically renders every GUI menu
as a native **Bedrock form** for Bedrock players — you do **not** configure a
separate Bedrock menu file. The same menu you edit in `..._gui.yml`
([GUI Menus](GUI-Menus.md)) is projected onto a Bedrock form on the fly:

* An item's **name** becomes the button text.
* An item with a **single action** becomes a **direct button** that runs it.
* An item with **multiple actions** (or one explicitly marked `bedrock.detail:
  true`, see below) becomes a button that opens an **auto-generated sub-form**:
  the item's lore is the content, and each action is its own button.
* A **decorative** item (no action) shows no button.

Java players keep seeing the normal inventory menu; only Bedrock players get the
form. This can be turned off with `general.bedrock-forms: false` in the config,
in which case Bedrock players see the Java inventory through Geyser instead.

> The old `..._gui-bedrock.yml` file is **no longer needed** to configure your
> menus — they come from `..._gui.yml` now. (The file still exists only for a
> couple of internal built-in forms like the confirmation prompt.)

# Improving Bedrock Compatibility in the Locale

A menu written well for Java usually projects fine to Bedrock, but a few tags in
`..._gui.yml` make the Bedrock forms noticeably better. All of these are edited
in the **normal Java GUI file**, per item.

## Click Actions: `<action:...>`

A Bedrock form can't "left-click vs right-click" a single button — each action
needs its own button. Declare an item's actions in its `lore` with the
`<action:intent>` marker so the plugin knows how to turn them into buttons and
what to label them:

````yaml
entry_land:
  name: <t:entry_heading><v:land>
  lore: '<t:user_content><v:title></t><newline><action:primary><label>Teleport
    to Spawn</label><desc><t:regular>Warps you to the land spawn.</desc></action><newline><action:remove><label>Delete
    Land</label></action>'
  bedrock:
    detail: true
````

* Intents: `primary` (left-click), `secondary` (right-click), `tertiary`
  (shift + left), `quaternary` (shift + right), `remove` (drop).
* `<label>` — the short button caption (on Java it appears after the click word;
  on Bedrock it's the button text). **Always give an action a `<label>`** — a
  missing one falls back to the raw intent name (e.g. `primary`) on the Bedrock
  button.
* `<desc>` — extra explanatory lines (Java: below the label; Bedrock: part of
  the sub-form content).
* The click word itself ("Left Click", "Drop") is added **only on Java**, from
  the translatable `value.click.<intent>` entry — it is never shown on Bedrock,
  so don't hardcode "Left click to…" text in the label.

## Show Lore on Bedrock: `bedrock.detail`

By default a single-action item becomes a plain button and its **lore is not
shown** on Bedrock (a button has no tooltip). If the lore carries information a
Bedrock player needs to read — a description, stats, an inbox message — set
`bedrock.detail: true`. The item then opens a sub-form that displays the lore as
content, with a button for the action and a Back button:

````yaml
entry_object:                       # an inbox message
  name: <t:regular_heading>#<v:id></t> <t:regular_value><v:date></t>
  lore: '<t:user_content><v:message></t><newline><action:primary><label>Remove</label></action>'
  bedrock:
    detail: true
````

## Put Dynamic Values in the Name

A Bedrock button shows the item **name**, not its lore. If a value like a
current toggle state or filter must be visible on the button, put its `<v:...>`
placeholder in the `name`, not only in the `lore`:

````yaml
refresh_filter:
  name: <t:regular_heading>Filter by Type:</t><t:regular_value> <v:type></t>
  lore: <t:regular>Cycle through message types.
````

## Per-Item Bedrock Overrides: the `bedrock:` block

Any item may carry a `bedrock:` block to tune just the Bedrock rendering:

````yaml
back:
  name: <t:regular_heading>Back
  bedrock:
    detail: false            # true = open a sub-form showing the lore (default false)
    name: 'Back'             # shorter button caption for Bedrock only
    lore: 'Return to the previous menu.'   # Bedrock-only content/description text
    icon:
      type: path             # "path" (resource pack) or "url" (default)
      path: 'textures/blocks/stone.png'
````

* `name` / `lore` — override the button caption / sub-form content on Bedrock
  only, without changing the Java item.
* `icon` — give the button an image. Use `type: url` with an image URL, or
  `type: path` with a texture path from a resource pack (sample pack:
  <https://github.com/Mojang/bedrock-samples/releases>).

## Hide Java-Only Hints in Chat: `<java>...</java>`

In **chat messages** (`..._messages.yml`), clickable hints like a `[CLICK]`
label only make sense on Java. Wrap them in `<java>...</java>` so they show for
Java players and are stripped for Bedrock players (who can't use the click):

````yaml
view: '<t:regular>Open the map: <java><t:click>[CLICK]</t></java>'
````

# Theme Colors on Bedrock: `theme.bedrock`

Bedrock forms don't render on the same background as Java tooltips: the **content
panel is dark** while **buttons are light-gray**. `theme.yml` has a
`theme.bedrock` section that overrides individual [theme tokens](../config/Text-Formatting.md#theme-color-tokens-ttoken)
**for the Bedrock surface only** — the same `<t:...>` tag automatically resolves
to these values on Bedrock and to the base values everywhere else.

````yaml
# Locale/theme.yml
theme:
  bedrock:
    # Content is on a dark panel -> brighter body text reads better.
    regular: '<white>'
    # Headings label the light-gray buttons, where bold + bright gold washes
    # out. Drop <b> and use a dark, high-contrast color instead.
    regular_heading: '<black>'
    entry_heading: '<black>'
    success_heading: '<dark_green>'
    error_heading: '<dark_red>'
````

> **Bedrock forms only support the 16 named colors, not hex.** An `<#rrggbb>`
> value renders as black on a form, so use named colors (`<dark_gray>`,
> `<black>`, `<dark_green>`, …) in the `theme.bedrock` section.

`theme.bedrock` is never touched by plugin updates, so your customizations
survive. It is shared by every language — don't translate or duplicate it.

# Spatial Menus Stay as Inventories

A few menus are spatial grids that can't become a linear list of buttons — for
example the chunk **map**. Those keep rendering as a Java inventory (shown to
Bedrock players through the Geyser container) instead of a form. This is
automatic; there is nothing to configure.

# Confirmation & Chat-Input Forms

With Floodgate installed, confirmation prompts open a dedicated confirm form, and
chat inputs (e.g. typing a player's name) open a native input dialog, instead of
requiring the Bedrock player to type in chat.

# If Bedrock Menus Don't Open

Make sure Floodgate is installed and configured correctly. Follow the Floodgate
installation instructions for both "Paper / Spigot" and "Proxy Servers" (if you
use a proxy): <https://wiki.geysermc.org/floodgate/setup>
