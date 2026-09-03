# Economy

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where land commands took an explicit `/land <land> ...`
> argument instead of acting on your edit land automatically.

Some servers use money in Lands. Your server decides which costs are enabled.

Money can be used for land creation, claiming, teleporting, rent, taxes, upkeep, renaming, and changing ownership.

# Land Bank

A land can have its own bank. The land bank can pay for land actions, taxes, and upkeep if your server enabled it.

Use `/lands bank balance` to view the bank balance.

Use `/lands bank deposit <amount>` to put money into the bank.

Use `/lands bank withdraw <amount>` to take money from the bank. You need permission from your land role to withdraw.

# Taxes

Taxes are payments from trusted players to the land or area they are trusted in.

Use `/lands eco taxes` to see taxes you may need to pay.

Land owners and players with the right role permissions can change taxes in the land menu.

If you cannot pay taxes, your server may remove you from the area.

# Upkeep

Upkeep is a regular payment that land owners may need to pay to keep their claims.

Use `/lands eco upkeep` to see upcoming upkeep for your lands.

Keep enough money in the land bank before upkeep is collected. If a land cannot pay, your server may remove claims or apply other server-defined rules.

# Nations

If your land is in a nation, your server may make your land pay the nation instead of paying upkeep directly to the server.

Nation owners can manage nation taxes in the nation menu.

Open it with `/nations`.

# Claim Costs

Claiming chunks may cost money. Unclaiming may give some money back if your server enabled refunds.

Some chunks can be free. For example, your first claims, permission-based free claims, or chunks claimed with claim blocks may not cost money.

# Rent and Sell

Rent and sell offers are explained on the [Rent & Sell System](Rental.md) page.

Rent payments may go to the land owner or to the land bank, depending on the server setup.

# Inbox

Money changes can be shown in the land inbox.

Open it from `/lands` or with `/lands menu inbox`.
