# Leaderboards

Lands supports top lists through `/lands top`, `/nations top`, signs, and holograms.

Available contexts:

* `land`
* `nation`

Available sortings:

* `balance`
* `chunks`
* `members`
* `level`
* `ratio-kd`: war kill and death ratio.
* `ratio-wl`: won and lost war ratio.

The `top-lands.divide` option in `config.yml` controls whether large balances are shortened. It also affects matching PlaceholderAPI balance placeholders.

# Signs

## Sign Lines

* Line 1: `[lands]`
* Line 2: `top`
* Line 3: `<context> <sorting>`
* Line 4: `<place>`

Example:

````text
[lands]
top
land balance
1
````

Permission to create leaderboard signs:

`lands.admin.sign.top`

# Holograms

To create holograms, install a supported hologram plugin and configure `general.hologram-provider` if you want to force one provider.

Supported plugins:

* CMI
* DecentHolograms
* FancyHolograms
* HolographicDisplays

Commands:

* `/lands admin hologram create <context> <sorting>`
* `/lands admin hologram list`
* `/lands admin hologram delete`

Permissions:

* `lands.admin.command.hologram.create`
* `lands.admin.command.hologram.list`
* `lands.admin.command.hologram.delete`
