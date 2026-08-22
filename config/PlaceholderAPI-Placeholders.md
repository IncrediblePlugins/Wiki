# PlaceholderAPI Placeholders

Here is a list of all available placeholders.

## Players
`%chestprotect_player_limit_<limit>%`\
The player's value for a ChestProtect limit.

Replace `<limit>` with a limit ID from [Limits](Limits.md).

Important: In the current plugin implementation, the placeholder parser only reads the first
segment after `player_limit`. Because ChestProtect limit IDs contain underscores, standard IDs such
as `player_blocks` may return an invalid-limit message until the parser is updated.

Use `/papi parse <player> %chestprotect_player_limit_player_blocks%` to test the placeholder on
your server after updates.
