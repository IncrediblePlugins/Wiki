# Levels

Levels are configured in the `levels.yml` file of Lands ([Levels](../configuration/Levels.md)). Get the level of a land or
nation with `MemberHolder#getLevel()`, all levels with `LevelsHandler#getLandLevels()` and `#getNationLevels()`
(`LandsIntegration#getLevelsHandler()`).

* Levels are bought: `MemberHolder#levelUp(LandPlayer)` checks the next level's requirements and pays its cost. It
  completes with a `LevelUpResult`.
* Levels aren't lost on their own. `MemberHolderLevelUpEvent` (cancellable) is called before a level-up,
  `MemberHolderLevelChangedEvent` after every level change, with its `LevelChangeCause`.
* `Level#getId()` is the level's section name in `levels.yml`.
* `MemberHolder#hasUnlock(String)` checks a feature unlocked by the `unlock` reward.

# Requirement Types

A plugin adds a requirement by registering a requirement type. Lands creates a requirement from every section of that type
in `levels.yml`. Register it in your plugin's `onLoad`: Lands reads `levels.yml` at the start of its `onEnable`, and
registering later throws an `IllegalStateException` (e.g. after a plugin reload). `LandsIntegration#onLoad(Runnable)` waits
until Lands loaded, if your plugin loads first, but it must still be called from your `onLoad`. Catch the exception, so a
missing requirement doesn't break the rest of your Lands integration.

Requirements of a plugin are configured under the plugin's name: the type `myplugin.hoppers` is
`requirements.myplugin.hoppers` in `levels.yml`.

```java
public final class MyPlugin extends JavaPlugin {

    @Override
    public void onLoad() {
        LandsIntegration lands = LandsIntegration.of(this);
        lands.onLoad(() -> {
            LevelsHandler levels = lands.getLevelsHandler();
            levels.registerRequirementType(HolderType.LAND, "myplugin.hoppers", definition -> new AbstractRequirement(definition) {
                @Override
                public @NotNull CompletableFuture<Double> retrieveValue(@NotNull MemberHolder holder) {
                    return CompletableFuture.supplyAsync(() -> (double) countHoppers((Land) holder));
                }
            });

            // nations: the sum of their lands
            levels.registerRequirementType(HolderType.NATION, "myplugin.hoppers", definition -> new AbstractRequirement(definition) {
                @Override
                public @NotNull CompletableFuture<Double> retrieveValue(@NotNull MemberHolder holder) {
                    return levels.sumOverLands((Nation) holder, land -> CompletableFuture.supplyAsync(() -> (double) countHoppers(land)));
                }
            });
        });
    }
}
```

* `retrieveValue` may be costly: Lands never calls it on the main thread and never waits for it there. Do the work off the
  main thread and complete the future exceptionally on errors. A value that takes longer than 10 seconds counts as not met.
* Lands caches values for 30 seconds for menus and placeholders, and retrieves them again before a level-up. When you know
  a value changed (e.g. a hopper was placed), call `LevelsHandler#invalidate(holder, "myplugin.hoppers")`.
* `RequirementDefinition#getSection()` has the requirement's section, for your own options.
* Return `null` from the type to skip an invalid requirement (log why).

# Reward Types

Rewards work the same way: `LevelsHandler#registerRewardType(HolderType, String, RewardType)`. A reward's `onReach`
runs when a land or nation reaches its level, `onLose` when an admin lowers the level below it. Rewards of all levels up
to the current one apply, so a plugin can also check `holder.getLevel()` and the levels below it whenever it needs to.
