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
