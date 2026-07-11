# Unclaim and Wilderness Regeneration

Lands does not regenerate chunks by itself when players unclaim land or when wilderness is damaged.

If you want chunk regeneration, use a dedicated regeneration plugin. The recommended plugin is [WildRegeneration](https://polymart.org/resource/wildregeneration.2096).

# What Lands Handles

Lands can:

* protect claimed land and configured wilderness flags
* unclaim chunks through `/lands unclaim`, upkeep, expiration, admin actions, and other Lands systems
* refund unclaim cashback if configured in `chunk.cashback`
* refund claim blocks if `land.claimblock.refund` is enabled

Lands does not restore blocks, containers, entities, farms, or terrain after a chunk becomes wilderness.

# Related Settings

Useful Lands settings:

| Setting | Use |
| --- | --- |
| `chunk.cashback` | Refund money when players unclaim normal claimed chunks. |
| `land.claimblock.refund` | Return claim blocks when claim-block chunks are unclaimed. |
| `upkeep.unclaim` | Unclaim chunks if a land cannot pay upkeep. |
| `land.leave-unclaim` | Unclaim chunks supplied by a member who leaves when the owner no longer has enough claim limit. |
| `land.expiration` | Remove inactive members, replace inactive owners, or delete inactive lands. |

# Admin Notes

Before enabling regeneration on a live server:

1. Test the regeneration plugin on a copy of the world.
2. Confirm how it handles containers, protected blocks, custom blocks, and entities.
3. Confirm whether regeneration runs immediately or queues work over time.
4. Back up affected worlds and the Lands database.

For inactive land cleanup, read [Land Expiration and Cleanup](Expiration.md).
