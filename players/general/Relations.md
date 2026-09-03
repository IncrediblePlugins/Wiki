# Relations

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where land/nation commands took an explicit
> `/land <land> ...`/`/nation <nation> ...` argument instead of acting on your edit land/nation
> automatically.

Relations decide whether another land or nation is neutral, allied, or an enemy.

# Allies

Allies are friendly lands or nations. Depending on your server settings, allies may be able to help in wars, share some access, or appear with ally colors in menus and nametags.

To send an ally request from your edit land:

`/lands relation ally add <land or nation>`

To remove an ally:

`/lands relation ally remove <land or nation>`

The other side may need to accept an ally request before the alliance becomes active.

# Enemies

Enemies are hostile lands or nations.

Some servers require you to mark a land or nation as an enemy before declaring war on it.

To mark another land or nation as an enemy from your edit land:

`/lands relation enemy add <land or nation>`

To request peace or remove the enemy relation:

`/lands relation enemy remove <land or nation>`

# Nation Relations

If your land is part of a nation, the nation may manage relations for its member lands.

The command works the same way as land relations, just under `/nations relation ...`:

* `/nations relation ally add <land or nation>`
* `/nations relation ally remove <land or nation>`
* `/nations relation enemy add <land or nation>`
* `/nations relation enemy remove <land or nation>`

# Menu

You can also manage relations through `/lands relation`, `/nations relation`, or the relations button in the land or nation menu.
