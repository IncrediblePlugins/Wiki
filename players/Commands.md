# Player Commands

`/farm` is the short alias used in this page. `/betterfarming` is the full command. Your server may also enable other aliases, such as `/farms`.

Some commands may be hidden from you if you do not have permission. Use `/farm help` in game to see the commands available to you on your server.

| Command | What it does | Permission |
| --- | --- | --- |
| `/farm get [type] [amount]` | Gets farm item(s). If type is not provided, the server's default farm type is used. The command may cost money, experience, levels, or configured currency items. | `betterfarming.command.get` |
| `/farm get [type] [amount] confirm` | Confirms a farm purchase when your server requires purchase confirmation. | `betterfarming.command.get` |
| `/farm list` | Opens the list of farms you placed. From this menu you can open a farm menu or teleport to a farm if teleporting is enabled. | `betterfarming.command.list` |
| `/farm help [page]` | Shows BetterFarming command help. Only commands you can use are shown. | `betterfarming.command.help` |
| `/farm confirmtp` | Confirms an unsafe farm teleport destination after BetterFarming asks for confirmation. | Server dependent |

# Command Tips

Farm type names come from the server's `farms.yml`. If `/farm get crop` does not work, use `/farm help` or ask staff which farm types are enabled.

Teleporting from `/farm list` can have a cost or a short wait time. If BetterFarming warns that the destination is unsafe, only confirm when you are sure you want to teleport there.
