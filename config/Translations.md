# Multiple Locales
The plugin supports multiple locales. If you place multiple locale files in the `Language` folder, the locale will depend on the players client locale.

# Downloading Community Translations
1. Community translations can be found in our Discord, by executing the `/translations` command in the Discord server.
2. You'll be asked to sign up at the translations page, to start translating and downloading language files.
3. Execute the command again in the Discord server and provide the requested parameters to complete the account setup.
4. You can download the files by navigating to the project (navigation bar at the top) -> gui or chat -> files -> download translation

The default English (en-US) language is already included in the plugin's file and doesn't need to be downloaded.

# Applying Translations
1. Insert the downloaded files into the `/Language` folder, which is located in the plugin folder.
2. If you for example downloaded a file with the name `lands-chat-de.yml` or `lands-gui-de.yml` then set the language to `de` in the plugin's config.yml file:
````yaml
  # Default: English (en-US) - no download required.
  # You can access translations maintained by the community in our Discord: https://discord.gg/B4MAJVk
  # To access translations, other than en-US, execute /translations in the Discord server.
  language: 'de-DE'
````


# Locale File not Applying
If you made changes to the locale files, but they are not visible ingame, then one of these mistakes were made:
* Make sure to reload the locale files: ``/<plugin> admin reload`` -> For Lands it would be ``/lands admin reload``
* Check for any YAML format mistakes that you might have made. You can use any online YAML validator to check that or just check your servers startup log for any errors related to parsing a YAML file. If the file has a YAML format mistake, the plugin automatically falls back to the default English locale.
* You have multiple locale files in the ``Language`` folder and your client locale doesn't match with the one you want to see. The plugin supports multiple locales and sets the locale depending on the players locale and which locales are placed in the ``Language`` folder.