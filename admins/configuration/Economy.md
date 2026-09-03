# Economy

This page covers the Lands economy systems that server owners usually need to tune together: banks, claim costs, taxes, upkeep, rent payments, and nation economy.

Note: The option lists on this page highlight the most important config options. They are not complete lists; check your generated config files for every available option.

# Economy Provider

Configure the provider in `config.yml` under `integration.economy`.

Available providers:

* `integration.economy.vault.enabled_10`: use Vault and a Vault economy plugin.
* `integration.economy.exp.enabled_15`: use player experience.
* `integration.economy.items`: use the configured currency item if no other provider is enabled or available.

Taxes require Vault economy. If you use item or experience economy, keep taxes disabled.

The display format is configured in `general.eco-format`.

# Global Collection Schedule

Taxes, land upkeep, and nation upkeep use `economic` in `config.yml`.

Important options:

* `economic.interval.days_2`: days between collections.
* `economic.interval.time`: time of day for collection.
* `economic.interval.change-cooldown_time`: minimum time between a tax or upkeep change and the next collection.
* `economic.insufficient-altert_time`: how early Lands warns about missing funds.

If you synchronize claims across servers with Redis, only the Redis master server should run these tasks. Configure this with `database.redis.master`.

# Land Bank

Land banks are configured in `land.bank`.

Important options:

* `land.bank.enabled_13`: enables land banks and the `/lands bank deposit`, `/lands bank withdraw`, and `/lands bank balance` commands.
* `land.bank.max-balance`: maximum money a land can hold. `0` disables the cap.
* `land.bank.fallback-personal`: lets Lands use the player's personal balance if the land bank cannot pay an action.

Useful commands:

* `/lands bank balance`
* `/lands bank deposit <amount>`
* `/lands bank withdraw <amount>`
* `/lands admin land <land or *> bank set <amount>`
* `/lands admin land <land or *> bank modify <amount>`

Withdraws require the role flag `BALANCE_WITHDRAW`.

# Claim Costs

Chunk claim costs are configured in `chunk`.

Important options:

* `chunk.costs_2`: base cost per claimed chunk.
* `chunk.cost-increase.mode`: `DEFAULT`, `ADD`, or `PERCENTAGE`.
* `chunk.cost-increase.value`: increase value.
* `chunk.cost-increase.max_2`: maximum claim cost. `0` disables the cap.
* `chunk.cashback.mode_2`: refund mode for unclaiming.
* `chunk.cashback.value_2`: refund amount or percentage.

Claim costs may be bypassed by free chunk permissions, initial land creation claims, admin permissions, or claim blocks.

# Land Creation and Other Costs

Common cost options in `config.yml`:

* `land.creation.costs`: cost for `/lands create`.
* `land.name.rename.costs_5`: cost to rename a land.
* `land.creation.mainblock.reposition-costs`: cost to move the main block.
* `land.spawn.creation.cost.set`: cost to set the first spawn.
* `land.spawn.creation.cost.change`: cost to change the spawn.
* `land.spawn.teleport.costs.value_3`: cost to teleport to a land spawn.
* `land.setowner.costs_6`: cost to transfer land ownership.
* `chunk.teleport.costs_3`: cost to teleport to a chunk from the claims menu.
* `random-teleport.costs_4`: cost for `/lands rtp`.

# Taxes

Taxes are configured in `features.taxes` and `taxes`.

Important options:

* `features.taxes`: enables land and area taxes.
* `taxes.min_2`: minimum tax value.
* `taxes.max_3`: maximum tax value for one area.
* `taxes.untrust-member`: untrust a member from the area if they cannot pay.
* `taxes.taxes-announcement_time`: how often players are warned about upcoming taxes.

Player command: `/lands eco taxes`

Taxes can be edited through the land menu by players with the required role permissions.

# Land Upkeep

Land upkeep is configured in `features.upkeep` and `upkeep`.

Important options:

* `features.upkeep`: enables land upkeep.
* `upkeep.per-chunk`: upkeep cost per claimed chunk.
* `upkeep.unclaim`: unclaim chunks if the land cannot pay.
* `upkeep.nopay_time`: grace period for newly created lands.
* `upkeep.upkeep-reminder_time`: reminder interval while a land has insufficient funds.

Player command: `/lands eco upkeep`

# Nation Economy

Nation economy is configured in `nations.yml`.

Important options:

* `nation.creation.costs`: cost for `/nations create`.
* `nation.name.rename.costs_2`: cost to rename a nation.
* `taxes.min`: minimum nation tax per chunk.
* `taxes.max`: maximum nation tax per chunk.
* `taxes.remove-land`: remove a land from the nation if it cannot pay nation taxes.
* `upkeep.enabled_4`: enables nation upkeep.
* `upkeep.per-chunk`: nation upkeep cost per chunk.
* `upkeep.delete-nation`: delete the nation if it cannot pay upkeep.
* `upkeep.nopay_time`: grace period for newly created nations.

When a land is part of a nation, it can pay taxes to the nation instead of paying land upkeep directly to the server. The nation can then pay nation upkeep to the server.

# Rent and Sell Payments

Rent and sell options are configured in `land.rent`.

Important options:

* `land.rent.rent`: lets players create rent offers.
* `land.rent.sell`: lets players create sell offers.
* `land.rent.bank`: sends rent and sell payments to the land bank instead of the owner's personal balance.
* `land.rent.holograms`: replaces rent signs with clickable holograms if the hologram plugin supports it.
* `land.rent.teleport.costs_7`: cost to teleport to a rentable area.
* `land.rent.teleport.rent-tp-cooldown_time`: cooldown for rentable area teleports.

See the player-facing [Rent & Sell System](../../players/advanced/Rental.md) page for gameplay behavior.

# Permission Notes

Economy command permissions are listed on the [Permissions](../permissions/Permissions.md) page.

Limit permissions and `player-limits.yml` can affect costs indirectly. For example, free land and free chunk limits can make land creation or claiming free for some players.
