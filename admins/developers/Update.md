Since 6.26.0 the API has changed in some minor, but important ways.
Mostly methods and classes that have been deprecated for years have been removed.

# Changes
* You now create a LandsIntegration instance via the static method of the **LandsIntegration interface** not directly through an constructor. This improves maintainability and backward support in the future.
* ``getLand`` methods have been removed from the LandsIntegration. The reason is that it has been misused in the past to check flag states. The problem is that Lands offers sub areas inside lands. Therefore one should retrieve an `Area` to check flag states. Not just the land. As this check would only be done against the default area. Therefore, use ``getArea`` or ``getUnloadedArea`` if the location is not loaded.
* The old ``LandSetting`` enums have been removed. Please use ``Flags.<Flag>`` instead.

# Removed in 9.3.0

Everything that was deprecated in the API has been removed in 9.3.0. If your plugin still uses one of these, switch to
the replacement and compile against the new API.

## Classes

| Removed | Use instead |
|---|---|
| `legacy.LandsIntegrator`, `integration.LandsIntegration` | `LandsIntegration.of(plugin)` (`me.angeschossen.lands.api.LandsIntegration`) |
| `flags.Flags`, `flags.Flag`, `flags.DefaultStateFlag` | `flags.type.Flags` and the types in `flags.type` |
| `flags.types.RoleFlag`, `LandFlag`, `PlayerFlag`, `NationRoleFlag` | `flags.type.RoleFlag`, `NaturalFlag`, `PlayerFlag` (`NationRoleFlag`: no replacement, use `flags.type.RoleFlag`) |
| `land.enums.LandSetting` | `flags.type.Flags` |
| `land.enums.SettingMode`, `land.enums.SortMode` | No replacement (no longer used) |
| `player.chat.ChatMode` | `LandPlayer#getChatTarget()` / `setChatTarget(MemberHolder)` |
| `events.LandCreateEvent` | `events.land.create.LandPreCreateEvent` |
| `events.land.claiming.LandUnclaimSelectionEvent` | `events.land.claiming.selection.LandUnclaimSelectionEvent` |
| `events.player.teleportation.PlayerSpawnLandEvent` (wasn't called) | `events.land.spawn.LandSpawnTeleportEvent` |
| `events.war.captureflag.CaptureFlagBreakEvent` (wasn't called) | `LandBlockRemoveEvent`: for capture flags its reason is a `CaptureFlagRemovalReason` |
| `CaptureFlagBreakEvent.BreakReason` | `land.block.removalreason.CaptureFlagRemovalReason` (same values) |

In `events.yml`, the sections `LandCreateEvent` and `PlayerSpawnLandEvent` are renamed to `LandPreCreateEvent` and
`LandSpawnTeleportEvent` on the first start of 9.3.0, so commands configured there keep running. `PlayerSpawnLandEvent`
wasn't called anymore: its commands run again, on every teleport to a land spawn. The section `LevelChangedEvent`,
which never matched its event, becomes `MemberHolderLevelChangedEvent` and runs from now on.

## Methods

| Removed | Use instead |
|---|---|
| `Land#of(name, landType, location, owner, claim, msg)` | `Land#of(name, tag, landType, location, owner, claim, msg)` (tag may be `null`) |
| `Land#delete(LandPlayer, DeleteReason)`, `Land#delete(Player)` | `Land#delete(LandPlayer)` |
| `Land#getChunks(World)`, `Land#getSubAreas(World)` | `Land#getContainer(World)` |
| `Land#hasArea(String)` | `Land#getArea(String) != null` |
| `Land#setSpawn(Location)` | `Land#setSpawnPosition(UnloadedPosition)` |
| `Land#getSize()` | `Land#getChunksAmount()` |
| `Land#getMaxMembers()`, `Land#getMaxChunks()` | `Land#getLimit(Limit.LAND_MEMBERS)`, `Land#getLimit(Limit.LAND_SIZE)` |
| `LandWorld#getArea(Location)` | `LandWorld#getArea(int, int, int)` |
| `LandWorld#hasRoleFlag(Player, ...)`, `LandWorld#hasFlag(...)` | `LandWorld#hasRoleFlag(LandPlayer, Location, RoleFlag, Material, boolean)` |
| `Area#getId()` | `Area#getULID()` |
| `Area#hasRoleFlag(Player, ...)`, `Area#hasFlag(...)` | `Area#hasRoleFlag(LandPlayer, RoleFlag, Material, boolean)`, `Area#hasRoleFlag(UUID, RoleFlag)` |
| `LandArea#contains(int, int, int)` | `LandArea#getBoundingBox()` |
| `CaptureFlag#breakCaptureFlag(..., CaptureFlagBreakEvent.BreakReason)` | Same method with a `CaptureFlagRemovalReason` (same values) |
| `TaxHolder#getColorName()` (on areas) | `getColorName(CommandSender)` |
| `MemberHolder#getWarName()` | `MemberHolder#getWarName(PlayerDataBase)` (`null` for the default language) |
| `MemberHolder#isTrusted(LandPlayer)` | `MemberHolder#isTrusted(UUID)` |
| `LandPlayer#getChatMode()`, `LandPlayer#setChatMode(ChatMode)` | `LandPlayer#getChatTarget()`, `LandPlayer#setChatTarget(MemberHolder)` |
| `LandPlayer#getInvite(String)`, `LandPlayer#hasInvite(String)` | `LandPlayer#getInvite(Land)` |
| `LandPlayer#getLand(String)` | `LandPlayer#getLands()` |
| `LandPlayer#getSupportClaimsPerLand()`, `TrustedPlayer#getSupportClaims()` | No replacement: support claims depend on a config option |
| `CombatTag#getAttacker()`, `CombatTag#getTarget()` | `CombatTag#getOwner()`, `CombatTag#getOpponents()` |
| `InboxMessage#getText()`, `InboxMessage#getTextWithDate()` | `getText(PlayerData)`, `getTextWithDate(PlayerData)` |
| `InboxCategory#getName()` | `InboxCategory#getName(LandPlayer)` |
| `Role#isVisitorRole()` | `Role#getType()` |
| `Sorting#getDisplayName()` | `Sorting#getDisplayName(LandPlayer)` |
| `Limit#getOldName()` | No replacement (`Limit.getByOldName(String)` stays) |
| `BroadcastEvent#getMessage()` | `BroadcastEvent#parseMessage(MessageParseRequest)`, `getMessageKey()` |
| `ChunkPreClaimEvent#getWorldName()` | `ChunkPreClaimEvent#getWorld()` |
| `LandEditMemberEvent#getTargetUID()`, `TargetableEvent#getTargetUID()` | `getTargetUUID()` |

`PlayerEvent#getPlayerUID()` and `PlayerNullableEvent#getPlayerUID()` stay (PluginFramework's events need them), but
are deprecated: use `getPlayerUUID()`.
