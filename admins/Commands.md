
      uspawners.admin.*:
        description: Permission for all admin commands. This does not include bypass.
        default: op
        children:
          uspawners.admin.command.give:
            description: /Spawners give
            default: op