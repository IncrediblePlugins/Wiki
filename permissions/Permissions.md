## Numbered Permissions
**Replace `<number>` with a number and `<farmtype>` with the configuration key of a farm type (farms.yml file).**\
Example:
````
  crop:
    enabled: true
````
Results in betterfarming.crop.10. Whereas 10 represents the maximum farms of this farm type.

`betterfarming.total.<number>`
Description: How many crop farms should the player be able\
to create in total? Below, you can control individual farm type limits.\
Both permissions need to be set in order to create any farm. 

`betterfarming.<farmtype>.<number>`\
Description: How many crop farms should the player be\
able to create?\
Example: `betterfarming.crop.5`, `betterfarming.tree.5`, `betterfarming.ore.5`

`betterfarming.roles.<number>`\
Description: How many player roles should the player be\
able to create per farm?

`betterfarming.members.<number>`\
Description: How many players should the farm owner be\
able to trust at the farm?

## General Permissions
`betterfarming.upgrade`\
Description: Only allow players with this permission to upgrade any farm, if config option upgrade-perm enabled.

## Command Permissions
See here: [Link](../players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by BetterFarming. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.
You don't need to explicitly set them.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set betterfarming.teleport.farm false``
The value ``false`` is important here.

### Teleportation Permissions
`betterfarming.teleport.farm`\
Description: Allow teleportation to placed farms.\
Note: This permission is set by default.

## Admin Permissions
```
      betterfarming.admin.*:
        description: Access to all admin actions.
        children:
          betterfarming.admin.flag.*:
            description: Access to all admin flags.
            children:
              betterfarming.admin.flag.auto_replant:
                description: Being able to toggle the auto replant flag.
          betterfarming.admin.command.*:
            description: Access to all admin commands.
            children:
              betterfarming.admin.command.reload:
                description: Access to /betterfarming reload command.
```

## Bypass Permissions

```
      betterfarming.bypass.*:
        description: Bypass all protections.
        children:
          betterfarming.bypass.block_break:
            description: Bypass block break protection.
          betterfarming.bypass.block_place:
            description: Bypass block place protection.
          betterfarming.bypass.harvest:
            description: Bypass harvest protection.
          betterfarming.bypass.plant:
            description: Bypass crop plant protection.
          betterfarming.bypass.interact:
            description: Bypass interact block protection.
          betterfarming.bypass.manage_players:
            description: Manage players of a farm, even if you're not trusted.
          betterfarming.bypass.delete:
            description: Delete other players farms.
          betterfarming.bypass.edit:
            description: Open other players farm menu and bypass role priorities.
          betterfarming.bypass.claims:
            description: Allow players to create farms on claims they're not trusted in and in wilderness, even if only-land is enabled in config.
```


