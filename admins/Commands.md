
      chestprotect.command.*:
        description: Get access to all commands
        default: op
        children:
          chestprotect.command.exit:
            description: Exit /Lock, /Unlock, /Untrust, /Trust, /SetRole mode
            default: op
          chestprotect.command.help:
            description: Get command information, help
            default: op
          chestprotect.command.lock:
            description: Enter /Lock mode
            default: op
          chestprotect.command.unlock:
            description: Enter /Unlock mode
            default: op
          chestprotect.command.trust:
            description: Enter /Trust mode
            default: op
          chestprotect.command.untrust:
            description: Enter /Untrust mode
            default: op
          chestprotect.command.setrole:
            description: Enter /SetRole mode
            default: op