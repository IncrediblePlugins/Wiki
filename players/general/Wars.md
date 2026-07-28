This page explains wars from a player's point of view.

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where wars used a standalone `/wars` command and you
> selected a land first with `/lands edit <land>` before running commands against it.

War commands are reached through `/land <land> war ...` (also available as `/lands land <land> war ...`),
or `/nation <nation> war ...` if the fight involves your nation instead of just your land. Replace
`<land>`/`<nation>` with the land or nation on your side of the war throughout this page.

# 1. Starting a War

To start a war, use `/land <land> war declare <land or nation>`.

You can only declare war if your role is allowed to manage wars. Your server may also require both sides to have enough members, claims, money, or age. Some servers only allow wars at certain times, or only between nations.

The target must be marked as an enemy first. If they have a war shield, they cannot be attacked until the shield ends.

After using the command, a menu opens where you can set a tribute. The tribute is the money the defender must pay if they surrender later. If the tribute is set to `0`, surrender may be disabled, depending on the server.

Some servers use mutual war declarations. In that case, the defender must accept the request with `/land <land> war declare <attacker>` before the normal preparation time starts. They can deny it with `/land <land> war decline`.

# 2. Preparation Time

After a declaration is sent or accepted, the war enters preparation time. During this time, both sides can prepare, but the fight has not started yet.

Use `/land <land> war info` or `/land <land> war menu` to see:

- who is fighting
- when the war starts
- how many points are needed to win
- the tribute
- the capture flag recipe, if capture flags are enabled

The length of preparation time depends on the server.

# 3. When the War Starts

When preparation time ends, both teams can fight each other.

Use `/land <land> war menu` to see the current war status. It shows both teams, kills, captures, points, the remaining time, and the actions that may be allowed in enemy land.

Use `/land <land> war spawn` to teleport near the enemy side, if your server can find a safe war spawn.

Your server decides what players can do in enemy claims during war. For example, you may be able to enter enemy land, fight players, place ladders, break certain blocks, open containers, or do none of these. Usually this only applies to the main lands that started the war, but servers can also include allied lands as war zones. Always check the war menu for what is allowed on your server.

Some servers require defenders to be online before enemies can invade or capture land.

# 4. Teams and Allies

If you are part of multiple lands that are in the same war, your team is chosen once and stays the same for the whole war. Defending lands are prioritized.

Allies may be able to help in war. For example, lands in the same nation can fight together. Allies that join the war can also be attacked by the enemy.

# 5. Capture Flags

Capture flags are special war blocks. You can craft them or receive them from the server. If crafting is enabled, the recipe is shown in the war menu (`/land <land> war info captureflag`).

Place a capture flag on a border chunk of enemy war land during the war. If the flag is too far inside the claim, too close to another capture flag, outside the allowed height, or on cooldown, it cannot be placed.

To capture the area, your team must hold the flag until the progress bar fills. Progress only moves forward when the invaders have more players in the area than the defenders. If defenders enter the area, they can stop or push back the capture progress.

Defenders are notified when a capture flag is placed. They can try to defend the area or destroy the flag. Destroying an enemy capture flag may give points. Depending on the server, a captured area may become unclaimed or may be claimed by the invaders.

# 6. Points and Winning

Wars are won with points. Points can come from kills, captured flags, destroyed capture flags, and sometimes other server settings.

The war ends when a team reaches the required points or when the war time runs out. If time runs out, the team with the most points wins. If both teams have the same score, the war ends in a draw.

The winner may receive money from the loser and other rewards set by the server. After the war, one or both sides may receive a war shield, depending on the server.

# 7. Surrender

The player surrendering for a land or nation needs permission to manage wars.

If defenders surrender, they pay the tribute that was set by the attackers. If attackers surrender, they may also need to pay a server-defined tribute to the defenders.

Surrender is done from the war menu (`/land <land> war menu`). If the required tribute is `0`, surrender may be blocked. If your land or nation cannot afford the tribute, you cannot surrender until enough money is available.

# 8. Useful Commands

- `/land <land> war menu` - open the war menu
- `/land <land> war info` - show information about your current or upcoming war
- `/land <land> war declare <land or nation>` - declare or accept a war
- `/land <land> war decline` - deny a mutual war declaration
- `/land <land> war spawn` - teleport near the enemy during war

If your nation is fighting instead of just your land, use the same subcommands under
`/nation <nation> war ...`.
