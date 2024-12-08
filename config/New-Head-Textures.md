Since 1.20.2 the servers no longer support the old head texture. Now, head textures need to be from an actual minecraft user skin. Majang now stores all skins that a player ever had set. Mojang only allows textures from their texture server. This mainly affects GUI menus. It is recommended to update custom heads to the new skin URL's below, in order to avoid warnings printed to the console.

# New Custom Heads
1. Open your GUI language file located in the `Language` folder of the plugin and search for custom heads. If you don't want to do this and haven't changed anything in the language files anyway, you can just delete the current language file and restart the server. It will generate with the new skin URL's, if you use the latest version of the plugin.

Custom heads have a long material value, like this:
````yaml
management:
  lore:
   - '&8✖ &7Toggle administrator flags like'
   - '   &7trusting players, claiming etc.'
  name: '&6&lManagement Flags'
  material: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMmVjODVhOWVhOTgzZTcwGJlMDIxZWU5NmUxMDg3ZmY4MGU0YjcwODRhMzM2NTFkYjJhMjYyODAxMmMyMzcwZiJ9fX0=
  slots: 30
````

2. You can find custom head skin URL's at: [minecraft-heads.com](https://minecraft-heads.com/custom-heads)
3. Pick the head you want.
4. Then copy the Minecraft-URL ID:\
   ![Copy the Minecraft-URL ID](https://i.imgur.com/KZxu6Jh.png)
5. Add the copied value to the item by setting `material` to `skin:<the copied value>`
````yaml
management:
  lore:
   - '&8✖ &7Toggle administratoral flags like'
   - '   &7trusting players, claiming etc.'
  name: '&6&lManagement Flags'
  material: skin:http://textures.minecraft.net/texture/17e4a316322ff14b8bdc8c9cbe0751f06d1798b22c34929a8cd403811667b37b
  slots: 30
````

**For the plugin Lands, you need to do the same thing for all role icons in roles.yml.**
