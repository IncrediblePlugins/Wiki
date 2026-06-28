# Claiming and Worlds

This page covers claim worlds, land creation, claim shape rules, claim blocks, player tools, random teleport, and related admin settings.

Note: The option lists on this page highlight the most important config options. They are not complete lists; check your generated config file for every available option.

# Claim Worlds

Claim worlds are configured in `config.yml` under `general.claim-worlds_list`.

Entry format:

`<world>:<claiming>:<min-height>:<max-height>`

Examples:

* `world`: enables player claiming in `world` with the full server height.
* `world:true:30:319`: enables player claiming from Y 30 to Y 319.
* `world:false`: only staff with `lands.admin.disabled-features` can claim there.

Admin lands always use the full world height.

Changing claim worlds requires a server reload or restart.

# Basic Mode

`basic-mode` disables advanced systems such as wars, nations, upkeep, and taxes. Use it only if the server should focus on simple claiming and trusting.

# Land Creation

Land creation is configured in `land.creation`.

Important options:

* `land.creation.force`: require `/lands create` before players can claim.
* `land.creation.costs`: cost for `/lands create`.
* `land.creation.claim-radius`: chunks claimed for free when a land is created.
* `land.creation.mainblock.enabled_3`: place a main block for new lands.
* `land.creation.mainblock.reposition-costs`: cost to move the main block.
* `land.creation.random-color`: give new lands a random name color.

Land name and tag rules are configured in `land.name` and `land.tag`.

# Claim Distance and Shape

Claim restrictions are configured in `land`.

Important options:

* `land.chunk-distance.mode_3`: distance mode. Available values are `SQUARE`, `EUCLIDEAN`, and `DIAMOND_SHAPE`.
* `land.chunk-distance.land_2`: buffer around lands that are not in a nation.
* `land.chunk-distance.nation`: buffer around lands that are in a nation.
* `land.force-near.enabled_2`: require claims to be near existing claims.
* `land.force-near.treat-as-new`: treat a far-away claim as a new land if possible.
* `land.shape.enabled_17`: deny thin or linear claim shapes.
* `land.shape.min-compactness`: required compactness ratio.
* `land.shape.min-chunks`: minimum land size before the shape check applies.
* `land.prevent-encirclement.enabled_9`: prevent claims that fully block another land from expanding.
* `land.prevent-encirclement.check-radius`: radius used for encirclement checks.
* `land.leave-unclaim`: unclaim chunks if the player who supplied the chunks leaves and the owner no longer has enough claim limit.

The role flag `LAND_CLAIM_BORDER` lets trusted players claim inside another land's border buffer when their role has that flag.

# Claim Limits

Use `player-limits.yml` for new servers. The old numbered permissions still exist, but the limits file is the recommended system.

Related options:

* `land.claim-limits-per-world`: makes chunk and owned-land limits apply per claim world.
* `chunk.initial-world`: restricts a land to the world where it was first created.

Useful admin commands:

* `/lands admin player <player> limits`
* `/lands admin land <land or *> limits`
* `/lands admin limits refresh`
* `/lands admin limits migrate confirm`

# Claim Blocks

Claim blocks are configured in `land.claimblock`.

Important options:

* `land.claimblock.only-owner`: only the player the item was created for can use it.
* `land.claimblock.ignore-max`: claim blocks do not count against the player's chunk limit.
* `land.claimblock.refund`: refund the claim block when a claim-block chunk is unclaimed.

Give claim blocks with `/lands admin player <player> give claimblock <radius> <amount> [silent]`.

If you do not want command claiming, remove `lands.command.claim`. If you do not want claim-block claiming, do not give players claim blocks.

# Auto Claim and Selection

Auto claim is configured in `chunk.auto-action`.

Important options:

* `chunk.auto-action.enabled_14`: enables `/lands claim auto` and `/lands unclaim auto`.
* `chunk.auto-action.stop_time`: stops auto action after this time.

Selection size is controlled by limits. The legacy numbered node is `lands.selection.<number>`, and the recommended system is `player-limits.yml`.

Sub areas are configured in `sub-area`.

# First Join Items

First join items are configured in `general.first-join-items`.

Available item groups:

* `selection`: lets players select chunks and areas.
* `info`: shows claim information when clicked.
* `camp`: creates a temporary camp when placed.
* `claim_block`: permanently claims chunks when placed.

Set the slot or amount below `1` to stop giving an item on first join. Set `usage` to `false` to disable that item type.

Use `/lands admin player <player> give first-join-items` to give enabled first-join items again.

# Map and Visualization

The player map is configured in `visualization.map`.

Important options:

* `visualization.map.claim`: lets players claim by clicking the map.
* `visualization.map.length`: chat map width.
* `visualization.map.height_2`: chat map height.

Border particles are configured in `visualization.type` and `visualization.view`.

Useful player commands:

* `/lands map`
* `/lands map chat`
* `/lands map link`
* `/lands view`
* `/lands view here`
* `/lands view stay`
* `/lands view disable`

# Random Teleport

Random teleport is configured in `random-teleport`.

Important options:

* `random-teleport.wild-worlds_list`: worlds and distance ranges for `/lands wild`.
* `random-teleport.world-perms`: use world-specific permissions such as `lands.command.wild.world`.
* `random-teleport.backup`: fallback world if the player's current world is not configured.
* `random-teleport.rtp-cooldown_time`: command cooldown.
* `random-teleport.costs_4`: teleport cost.
* `random-teleport.extensive-check`: load the destination chunk to check biome safety.

Make sure each random-teleport world has a useful `/setworldspawn`, because distances are measured from world spawn.

Staff can random-teleport another player with `/lands wild <world> <player> [skip-cooldown]`.

Permission: `lands.admin.command.wild`

# Unstuck

`/lands unstuck` teleports a player from a claimed chunk to the nearest wilderness location.

Configure it in `unstuck`.

Important options:

* `unstuck.unstuck-cooldown_time`: command cooldown.
* `unstuck.allow-movement`: whether the player may move during teleport preparation.

# Storage

Land storage is configured with `land.storage`.

If enabled, players can use `/lands storage`.

They can also access storage through the land main block barrel.

Disabling storage deletes all stored items, so take care when changing this option on an existing server.

# WorldGuard and Region Managers

Lands registers the WorldGuard flag `lands-claim`.

Use `/region flag <region> lands-claim <allow or deny>` to allow or deny claiming in a WorldGuard region.

Relevant options:

* `integration.manager.WorldEdit.enabled_7`: restrict WorldEdit use in lands where the player is not trusted.
* `integration.manager.global-regions`: apply `lands-claim` to global regions. Use this only if you want to control wilderness claiming through global region flags.

For FAWE, also configure FAWE region restrictions. Players with `fawe.lands` may bypass Lands restrictions.

# Admin Maintenance

Useful commands:

* `/lands admin resetworld <world> confirm`: deletes all claims and land spawns in a world.
* `/lands admin import <plugin>`: imports claims from a supported claim plugin.
* `/lands admin menu`: manages wilderness flags and admin lands.

Claiming, command, bypass, and staff permissions are listed on the [Permissions](../permissions/Permissions.md) page.
