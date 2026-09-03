When you declare a war you pick two things: a **war mode** and a **war goal**. This page explains what
each one means in-game. For the overall flow of a war, see [Wars](Wars.md).

- A **war mode** decides *how the war is fought and scored* - where points come from and how you win.
- A **war goal** decides *what happens to the loser* when the war ends.

Which modes and goals you can choose depends on the server; some are turned off or only make sense in
certain situations.

# War Modes

## Skirmish

The classic war. You earn points by **killing enemy players** and by **capturing their land with
capture flags** (and by breaking the enemy's flags). First team to the required points wins; if time
runs out, the team ahead on points wins.

This is the mode that uses craftable capture flags - see [Wars, section 7](Wars.md#7-capture-flags).

## King of the Hill (Server Arena)

Fought over a **neutral arena** the server admins have built somewhere. Kills score nothing here -
instead, whichever team is **holding the arena's control point** earns points every few seconds. Hold
it longer than the enemy and you win.

- Both teams are teleported to their arena spawn when the war starts.
- Capturing (filling) the control point resets it and sends everyone back to their spawns, so the fight
  restarts for the point.
- This mode can only be chosen when the server has a free, fully built arena.

## King of the Hill (Player Lands)

A two-front King of the Hill that needs no admin arena. During preparation, **each team places one
control point in its own land**, and you score by **holding the enemy's point** - so both lands become
battlegrounds at once.

To place your point, stand where you want it in your own main land during preparation and run:

```
/lands war koth set
```

(Use `/nations war koth set` if a nation is fighting - the point goes in its capital land.)

- Your own point **can't be broken by hand**. To move it, just run the command again where you want it.
- You **only score by capturing the enemy's point**, never by sitting on your own - standing on your own
  point only defends it. So to win, you have to go on the offensive.
- Attackers are allowed to break and place some blocks in the contested lands to reach the enemy point.
- If a team doesn't place its point in time, the war falls back to a server arena (if one is free), or
  the team that did place wins - a draw if neither placed.

# War Goals

The goal is what the winner actually gets. A **surrender** applies the same goal but usually on gentler
terms than a fought loss, and a **draw** applies nothing (there's no winner).

## Skirmish (robbery)

A low-stakes war. The winner **robs money** from the loser's bank and no one loses any claims. The
mildest goal - good for rivalries and friendly server events.

## Annexation

The winner **unclaims all of the loser's war lands**. The loser is paid the normal unclaim cash-back for
those chunks, but the land itself is gone. Ownership is not transferred - the chunks simply become
wilderness again.

## Vassalage

The winning **nation** absorbs the loser as a restricted **vassal** member of the nation. Only available
when your side is a nation. On some servers the loser's bank balance is seized too. A vassalized land can
later fight for freedom with an [independence war](Wars.md#10-independence-vassals).

## Raid

After the war, the winner's members get a **raid window** on the loser's lands - a period during which
they can loot containers, open doors, and break through walls to breach the base (limited to a set list
of blocks, so they can't level everything). A time-limited "spoils of war" instead of a permanent loss.

## Independence

A special goal used only when a **vassal declares independence** from its overlord
(`/lands war independence`). Win and the vassal becomes free; lose or draw and it stays a vassal
and can't try again for a while.
