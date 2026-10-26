# Land and Nation Levels

Lands and nations can level up, if your server has levels enabled. Higher levels give rewards, for example more claims,
more members, a lower upkeep, faster crop growth or features like a public spawn. The rewards of all levels you reached
add up.

# Leveling Up

Open the level menu with `/lands menu land level` (for your nation: `/nations menu nation level`). It shows:

* your current level and its rewards,
* the next level, its cost and its rewards,
* the requirements of the next level and how far you are, for example the number of trusted players or the age of the
  land.

Once all requirements are met, click **Level up**. The cost is paid from the land's bank (`/lands deposit`). A nation pays
from the bank of its capital. You need the `level_up` role flag, which only the owner has by default (for nations: you need
to be allowed to edit the nation).

When your land can level up, its online members are told, for example after a deposit or when a menu of the land is
opened.

Your level is never lost, also if you no longer meet the requirements later.

Who counts as a member for the requirements: players trusted in the whole land, you included. Players trusted only in a
sub area, tenants and players trusted for a limited time don't count. The playtime requirement only counts members who
are trusted for some days (7 by default): trusting a player who played a lot doesn't help right away.

# Locked Features

Your server can lock features until a level, for example:

* visitors teleporting to your land's spawn,
* the land storage,
* renting out and selling areas,
* declaring wars.

If you try to use a locked feature, Lands tells you which level unlocks it.
