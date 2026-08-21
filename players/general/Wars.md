This page explains wars from a player's point of view: how to start one, what happens during it, and
how a war is won or lost.

> This page describes the latest plugin version. If these commands don't work on your server, it may
> still be running an older version where wars used a standalone `/wars` command and you selected a
> land first with `/lands edit <land>` before running commands against it.

War commands are reached through `/land <land> war ...` (also available as `/lands land <land> war ...`),
or `/nation <nation> war ...` if the fight involves your nation instead of just your land. Replace
`<land>` / `<nation>` with the land or nation on your side of the war throughout this page.

# 1. How a War Works, in Short

1. You mark the other side as an **enemy**, then **declare war**.
2. When declaring, you choose a **war mode** (how the war is scored and won) and a **war goal** (what
   the winner gets when it ends). See [War Modes and Goals](War-Modes-and-Goals.md).
3. There is a **preparation time**, then the war **starts** and both teams can fight.
4. The war ends when one side reaches the points needed to win, or when time runs out. The goal you
   picked then decides the reward - robbed money, unclaimed land, vassalage, a raid window, and so on.
5. At any point a side can **surrender** to end it early on gentler terms.

# 2. Before You Can Declare

The other side must be marked as an **enemy** first (see [Relations](Relations.md)). You also need a
role that is allowed to manage wars.

Your server may add extra requirements before a war can be declared, such as:

- both sides having enough members, claimed chunks, money, or age,
- only allowing wars between nations,
- only allowing declarations on certain days or hours,
- limiting how far apart in level the two sides may be.

If the enemy has an active **war shield**, they can't be attacked until it runs out. Shields are given
after events like creating a land, surrendering, or finishing a war.

# 3. Declaring a War

Start with:

```
/land <land> war declare <enemy land or nation>
```

A short menu then walks you through the declaration:

1. **Pick a war mode** - how the war is fought and scored (a straight skirmish, or a King of the Hill
   contest). Some modes are only offered when the server has set them up.
2. **Pick a war goal** - what actually happens to the loser (money robbed, land unclaimed, vassalized,
   raided...). Some goals are only available in certain situations - for example, vassalizing requires
   your side to be a nation.
3. **Confirm** the declaration.

Read [War Modes and Goals](War-Modes-and-Goals.md) for what each mode and goal does.

**Mutual declarations.** Some servers require the defender to accept first. The defender accepts by
running `/land <land> war declare <attacker>`, or refuses with `/land <land> war decline`. Preparation
time only begins once they accept.

# 4. Preparation Time

After a declaration is sent (or accepted), the war enters **preparation time**. Both sides can get
ready, but no fighting counts yet.

Use `/land <land> war info` or `/land <land> war menu` to see:

- who is fighting,
- the war mode and goal,
- when the war starts,
- how many points are needed to win,
- the capture flag recipe, if capture flags are used.

If you chose the **King of the Hill (Player Lands)** mode, this is when each team sets its point - see
[War Modes and Goals](War-Modes-and-Goals.md#king-of-the-hill-player-lands).

# 5. When the War Starts

When preparation ends, both teams can fight. Use `/land <land> war menu` to follow the current status:
both teams, their points, the remaining time, and what you're allowed to do in enemy land.

Use `/land <land> war spawn` to teleport near the enemy, if your server can find a safe war spawn.
(In a King of the Hill arena war, this sends you to your team's arena spawn instead.)

**What you can do in enemy claims** depends entirely on the server. You might be able to enter enemy
land, fight players, place ladders, break certain blocks, open containers - or none of these. Usually
this only applies to the main lands that started the war, but some servers also turn allied lands into
war zones. Always check the war menu for what's allowed.

Some servers require defenders to be **online** before enemies can invade or capture.

# 6. Teams and Allies

If you belong to several lands that end up in the same war, your team is chosen once and stays the same
for the whole war (defending lands are prioritized).

Allies can help fight - for example, lands in the same nation fight together. Allies that join a war can
also be attacked by the enemy.

# 7. Capture Flags

Capture flags are special war blocks used by the standard **Skirmish** mode. You craft them (the recipe
is shown in `/land <land> war info captureflag`) or receive them from the server.

Place a capture flag on a **border chunk** of enemy war land during the war. It can't be placed if it's
too far inside the claim, too close to another flag, outside the allowed height, or on cooldown.

To capture the area, your team holds the flag until its progress bar fills. Progress only moves forward
while the invaders have **more players in the area than the defenders** - defenders standing in the area
stop, and can push back, the progress. Defenders are warned when a flag is placed and may fight for the
area or destroy the flag. Depending on the server, a captured area becomes unclaimed or is claimed by
the invaders, and destroying an enemy flag can award points.

> King of the Hill wars use their own fixed points instead of craftable flags - see
> [War Modes and Goals](War-Modes-and-Goals.md).

# 8. Points and Winning

Every war mode is scored in **points**; the mode decides where points come from (kills and captures in
Skirmish, or holding a point over time in King of the Hill).

A war ends when a team reaches the required points, or when the war time runs out. If time runs out, the
team with the most points wins - but if the scores are tied (or too close, in King of the Hill), it's a
**draw**. A draw has no winner, so the goal's reward does not apply.

When there is a winner, the **war goal** decides what happens to the loser, and both sides may receive a
war shield afterwards.

# 9. Surrender

A side can surrender to end the war early - during preparation or once it's active. Surrendering still
applies the war goal, but usually on **gentler terms** than losing the fight outright (for example, less
money is robbed). You need permission to manage wars to surrender for your land or nation.

Surrender from the war menu (`/land <land> war menu`). There is no tribute to negotiate - the cost is
whatever the server configured for that goal's surrender.

# 10. Independence (Vassals)

If your land has been **vassalized** by a nation (see the Vassal goal), you can fight to break free:

```
/land <land> war independence
```

This starts an independence war against your overlord. Win it and your land becomes free again. Lose it
(or draw) and you stay a vassal and can't try again until a cooldown passes.

# 11. Useful Commands

- `/land <land> war menu` - open the war menu
- `/land <land> war info` - show information about your current or upcoming war
- `/land <land> war info captureflag` - show the capture flag recipe
- `/land <land> war declare <land or nation>` - declare or accept a war
- `/land <land> war decline` - deny a mutual war declaration
- `/land <land> war spawn` - teleport near the enemy (or to your arena spawn) during war
- `/land <land> war koth set` - place your team's King of the Hill point in your own land
- `/land <land> war independence` - a vassal declares an independence war

If your nation is fighting instead of just your land, use the same subcommands under
`/nation <nation> war ...`.
