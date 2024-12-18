## My players can't claim or trust members, because it says that their limit is 0. What is wrong?
If it says that, then this is definitely the case. Please make sure your permissions plugin is setup correctly (eg. groups, inheritance).
You can get a list of Lands permissions a player has by executing `/lands listperms <player>`.

***

## Where can I toggle wilderness flags or convert regular lands into admin/server lands?
This will open a menu where you can toggle wilderness flags and convert regular lands into admin/server lands: `/lands admin menu`

***

## Some players/lands have unlimited claims. How can I prevent that?
The land owner has lands.chunks.* or op.

***

## Claim Costs not Working
If you configured claim costs in config.yml, but they don't apply, it's because one of these reasons:
* They have free chunks via the ``lands.free.chunks.<number>`` permission or they have op.
* Their claim amount is lower than the initial claim-radius in config.yml.
* Claimblocks, that claim when being placed down, always claim for free.

***

## How can I restrict fly to players claims?
Just give them access to your /fly command and make sure to not give them fly bypass permissions.\
Also the fly flag needs to be enabled for their flag in their claim. To toggle fly in wilderness, use `/lands admin menu`.

***

## How can I set visualisations to display permanently?
Set the visualisation duration to -1 and if you want to automatically enable it on server join, make sure to enable the join option too:
```yaml
# /lands view visualization
view:
  # Should Lands display land borders automatically once the player joins?
  # NOTE: You can set duration_9 (below) to -1 to make the visualization permanent.
  join: false
  # Duration of land view.
  # Time unit is seconds. You can make this permanent by setting the value to -1
  duration_9: 60
```


***

## My players can't toggle settings. What is wrong?
You did not give them the required permissions. Lands will always display you permission hints, if the player is missing  a permission.


***

## Where can I edit the messages and GUI menus?
In the `/plugins/Lands/Language` folder.

***

## My players are allowed to pvp, even though pvp is disabled?
You have combat tagging enabled:
```yaml
# Specified combat settings which do not affect wars.
combat:
  # Combat tagging
  # If a player attacks a other player he will by tagged for x seconds so that, regardless of land settings,
  # other players can attack him.
  # 0s = disabled
  tag-time: 15s
  # Should players, which are members in a common land, be able to fight in wilderness?
  # NOTE: This option requires server restart / reload.
  ally-wilderness: true
```

***

## How can I deny / allow claiming in specific WorldGuard areas?
Use this command: `/region flag [region] lands-claim <deny or allow>`\
By default this flag will be set to deny.

***

## How can I set claim (permission) limits per world?
Toggle the `claim-limits-per-world` option in config.
Example: If you set the permission lands.chunks.5 for your players, they will be able to claim 5 chunks in each claim world instead of 5 chunks in general. This then can be combined with your permissions plugin per world permissions, which would allow you to set different claim limits per world. This only applies for claim permissions: lands.chunks.NUMBER, lands.ownlands.NUMBER

***

## How can I prevent swear words to be taken for land, role or area names?
Edit the `swear-words` list in your chat locale file.

***

## How can I disable the selection or info tool?
* If you want to prevent players from using the tool at all, just set ``usage`` to ``false`` in the config file.
* If you want to disable them receiving the item when they join for the first time, set ``slot`` to a value lower than 1.
* If you want the tool to be unique and therefore not responding to vanilla items, assign a random `model-data` in the GUI file to the item: [Link](https://wiki.incredibleplugins.com/general/menus/gui-menus#set-custom-model-data)

The relevant config section:
````yaml
  # Give players items at first join.
  # The item appearance can be edited in the GUI language file.
  first-join-items:
    # The selection tool allows them to claim.
    selection:
      # Setting the slot or the amount of an item to a value lower than 1, will not give the item on first join.
      slot_4: 1
      amount: 1
      # If disabled, players won't be able to use this item at all.
      usage: true
    # The info tool shows information about a claim when clicking on it.
    info:
      slot_5: 2
      amount_2: 1
      usage_2: true
    # The camp block creates a temporary claim at placement.
    camp:
      slot_6: 3
      amount_3: 1
      usage_3: true
    # Claim blocks claim the chunk they were placed into permanently, until the player unclaims the chunk.
    claim_block:
      slot_7: 4
      amount_4: 1
      usage_4: true
````

***

## How can I prevent land members attacking each other?
In general, you should leave that decision up to the land itself. They can toggle the attack player flag in their land menu. But as a server admin you can force it by editing [roles.yml](https://wiki.incredibleplugins.com/lands/configuration/roles-and-their-flags) and restrict PvP in wilderness as well. The following option disables PvP for members of the same land in wilderness.
````yaml
    # Should players, which are members in a common land, be able to fight in wilderness?
    # NOTE: This option requires server restart / reload.
    ally-wilderness: false
````

## How can I change the default land enter and leave titles?
These can be changed in the language file:
````yaml
      enter:
        land: '#t#[config]in:5,stay:40,out:2[/config]&2&l{land}[newline]&3{title}'
        camp: '#t#[config]in:5,stay:40,out:2[/config]&2&l{land}[newline]&3{title}'
        admin: '#t#[config]in:5,stay:40,out:2[/config]&2&l{land}[newline]{title}'
        pvp-warning: '#a#&cYou entered a pvp zone.'
      leave:
        land: '#t#[config]in:5,stay:30,out:2[/config]&2&lWilderness[newline]&7Feel the wild'
        camp: '#t#[config]in:5,stay:30,out:2[/config]&2&lWilderness[newline]&7Feel the wild'
        admin: '#t#[config]in:5,stay:30,out:2[/config]&2&lWilderness[newline]&7Feel the wild'
````

The placeholder `{title}` will be replaced by the title that is set by the land in their menu. The default title can be found in the same file as well:
````yaml
    title:
      land: '&7%level% &7of&3 %owner%&7.'
      camp: '&7Camp of&3 %owner%&7.'
      admin: '&7This land belongs to the server.'
````
The default title only applies to new land creations. Existing lands can change the title in their land menu.