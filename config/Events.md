**If there's an error at when a condition is checked, you most likely have a mistake in your condition (syntax).**

# Concept
All available events in the plugin's API are able to get some commands attached. These commands can be bound to conditions.

## Event
Each event has its own section in the `events.yml` file. An event can have a parent condition attached. This condition must be passed in order for the other conditions even to be checked.

### Available Events
[Click here for a list of all events of Lands.](https://github.com/Angeschossen/LandsAPI/tree/master/src/main/java/me/angeschossen/lands/api/events)
Whenever a new event gets added, you need to manually add it in events.yml, if you want to execute commands for it.

# Condition Operators
A condition supports the following operators:

## Logical Operators
* `&&` And
* `||` Or
* `==` Equals
* `!=` Not equals
* `!` Negation
* `>=` Greater or equals (only applicable with numbers)
* `>` Greater (only applicable with numbers)
* `<=` Smaller or equals (only applicable with numbers)
* `<` Smaller (only applicable with numbers)

### Checking if Variable is Set
Some events are called for different entities, where some variables might be null. Example: The `LandOwnerChangeEvent` can be called for an area, but also for a land. When called for a land, then all `area_...` variables will be null. This allows you to differentiate if the owner was changed for a land or just an area (rental). Example:
```yaml
condition: 'area_name != null' # called for an area
```

## Numerical Operators
* `+` Addition
* `-` Subtraction
* `*` Multiplication
* `/` Division

## Text Operators
* `==` Equals
* `!=` Not equals
* `tolowercase("Text ABC")` will change `Text ABC` to `text abc`
* `variable_or_text contains("text")` Contains text, whereas `variable_or_text` can be a variable or "text".

## Player related
* `haspermission("permission")` Check if a player has a permission. Replace `permission` with a permission of your choice. You can specify a player by using `haspermission([player_uuid, "permission"])` where `player_uuid` is a provided variable from the event that must end in "_uuid".

### Comparing Text
Text must be enclosed by quotation marks. Example:
```yaml
condition: 'player_name=="Steve"'
```

## Variables
The variables of each event can be viewed by enabling the `logging.debug` option in config.yml.
You must invoke the event to print all variables and affected player groups to the console. PlaceholderAPI placeholders are supported for both player related conditions and commands, but not for cancellation conditions and general conditions that are not bound to a player group.

## Lists
You can define a list of objects (including logical expressions) by surrounding them by `[]` and separating list items by `,`.

### Operators
* `["aBc"] contains("aBc")` Contains
* `tolowercase(["aBc"])` Turns `["aBc"]` into `["abc"] `

Example:
```yaml
condition: '["abc", "def"] contains(["abc"])' # = true
condition: '["abc", "def"] equals ["abc", "fed"]' = false
```

## Commands
### Affected Player Groups
You can execute commands for different groups of players. These players may not be online at command execution.
Each player group can have multiple conditions with multiple commands attached. The condition is checked for every individual player that is part of this group. You can get the player's name or UUID by using `this_name` and `this_uuid` as a variable. Example:

```yaml
      land_online:
        1:
          condition: 'player_lands_own >= 0'
          commands:
            - 'say First condition with one command attached.'
        2:
          condition: '(player_lands_trusted <= player_lands_own + 2 && player_name=="Steve") || land_name=="Test"'
          commands: 
            - 'say Second condition with one command attached.'
```

### Execute as Console
[Click here.](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#optional-item-parameters)

# Event Cancellation
You can cancel an event by setting the condition at the `cancel` option. Later, you can check if the event has been cancelled.
You might not want to run certain commands, when the event has been cancelled. Therefore, it's highly recommended to check the event cancellation. You can find an example below.

## Cancellation Variables
* `cancelled` - will equal true if the event has been cancelled by you or any 3rd party plugin
* `cancelled_self` - will equal true, if the event has been cancelled by your condition.

# Example:
```yaml
LandOwnerChangeEvent:
  cancel: 'reason=="UPKEEP"'
  commands:
    condition: 'cancelled == false && reason=="BOUGHT"'
    groups:
      player_self:
        1:
          condition: 'area_name != null' # purchased area
          commands:
            - 'msg Hello {owner_new_name}, you''ve purchased the area {area_name}.'
        2:
          condition: 'area_name == null' # purchased the whole land
          commands:
            - 'msg Hello {owner_new_name}, you''ve purchased the whole land {land_name}.'
      land_online:
        1:
          condition: 'area_name == null' # purchased the whole land
          commands:
            - 'msg {player_name} The player {owner_new_name} is now the new owner of your land {land_name}.'
      area_online:
        1:
          condition: 'area_name != null' # purchased area
          commands: # {player_name} will be the player that is part of the "land_trusted" collection.
            - 'msg {player_name} The player {owner_new_name} bought the area {area_name}.'
```
