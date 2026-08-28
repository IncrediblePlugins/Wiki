# Multiple Locales
The plugin supports multiple locales. If you place multiple locale files in the `Locale` folder (previously called `Language`), the locale will depend on the player's client locale.

# Locale Files
Each language is made up of several files in the `Locale` folder, all sharing the same language code prefix:

| File | Purpose |
|---|---|
| `en-US.yml` | Chat messages, command output, titles, action bars, boss bars |
| `en-US_gui.yml` | Java Edition inventory menus (item names/lore, menu titles) |
| `en-US_gui-bedrock.yml` | Bedrock Edition forms (Geyser/Floodgate) |
| `en-US_dialogs.yml` | Paper's native dialogs (loaded on Paper only) |

For another language, `en-US` is replaced by that language's code across all files, e.g. `de-DE.yml`, `de-DE_gui.yml`, `de-DE_gui-bedrock.yml`, `de-DE_dialogs.yml`.

`theme.yml` defines the shared color scheme (see [Text Formatting](Text-Formatting.md)). It is **not** per-language — there is only one `theme.yml`, shared by every locale. Don't translate or duplicate it.

# Downloading Community Translations
Community translations are downloaded by executing the `/localedownload` command in our Discord server.

The default English (en-US) language is already included in the plugin's file and doesn't need to be downloaded.

# Applying Translations
1. Insert the downloaded files into the `/Locale` folder, which is located in the plugin folder.
2. Set the language in the plugin's `config.yml` to match the language code of the files you added. For example, if you added `de-DE.yml`, `de-DE_gui.yml`, … set:
````yaml
  # Default: English (en-US) - no download required.
  # You can access translations maintained by the community in our Discord: https://discord.gg/B4MAJVk
  # To access translations, other than en-US, execute /localedownload in the Discord server.
  language: 'de-DE'
````


# Locale File not Applying
If you made changes to the locale files, but they are not visible ingame, then one of these mistakes were made:
* Make sure to reload the locale files: ``/<plugin> admin reload`` -> For Lands it would be ``/lands admin reload``
* Check for any YAML format mistakes that you might have made. You can use any online YAML validator to check that or just check your servers startup log for any errors related to parsing a YAML file. If the file has a YAML format mistake, the plugin automatically falls back to the default English locale.
* You have multiple locale files in the ``Locale`` folder and your client locale doesn't match with the one you want to see. The plugin supports multiple locales and sets the locale depending on the players locale and which locales are placed in the ``Locale`` folder.
