# Spawner Stacking

This page is about **stacking spawner blocks** into one combined stack. It is not about stacked
mobs — read [the FAQ](FAQ.md#why-are-entities-stacked) if you were looking for that instead.

# What Stacking Does

If your server has spawner stacking enabled, placing an upgradeable spawner next to a matching one
merges it into a single stack instead of taking up another block. One spawner block can then
represent many spawners at once, each contributing to how often and how much it spawns.

# How to Merge Spawners

Place a spawner within the configured distance of another spawner of the same entity type and
upgrade level. It merges automatically — you do not need to do anything else. Chat tells you when a
merge happens and how many spawners are now in the stack.

A spawner only merges into a stack if the entity type and upgrade level match exactly. Placing a
higher- or lower-level spawner next to an existing stack starts a separate stack instead of merging.

There is a maximum stack size. If a stack is already full, a newly placed spawner starts its own
stack nearby instead.

# Breaking a Stacked Spawner

Breaking a stacked spawner normally takes just **one** spawner out of the stack — the block stays
in place with the reduced amount, and you receive one spawner item.

Sneaking while breaking it may instead take the **entire stack** at once, depending on your
server's settings. Ask your server's staff, or check chat when you break one — it tells you how
many spawners you received.

Depending on server settings, a broken stack either drops one spawner item per spawner (which stack
normally in your inventory) or a single bundled item that remembers the whole stack and rebuilds it
immediately when placed again.

# Upgrading a Stack

Upgrading a stacked spawner upgrades every spawner inside it at once. Because of that, the upgrade
cost for a stack may be higher than upgrading a single spawner — your server decides whether the
cost scales with the stack size.

# Limits

Your personal placed-spawner limit and your server's per-chunk spawner limit may or may not count
every spawner inside a stack individually — this depends on server configuration. If you are
unsure why a stack didn't grow further, ask your server's staff whether a limit was reached.
