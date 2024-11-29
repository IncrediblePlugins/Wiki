Camps are temporary lands that are created by placing a camp item. A camp will be deleted automatically after a server defined period.
A camp does not pay any upkeep. You can give camp items to players by executing `/lands admin player <player> give camp <amount> <radius>`.

The configuration can be found in config.yml:
````yaml
# Camps are temporary lands that will get deleted after a defined period.
# Camp items can be given at first join or by executing /lands admin player <player> give camp <amount> <radius>
camp:
  # Set how much it should cost. This also includes the chunks that are being claimed.
  costs_8: 0
  # After how much time should camps be deleted?
  # 0 = never
  expire_time: 1d
  # Configure the default radius of chunks to claim.
  # You can override this executing /lands admin player give camp <radius> [silent]
  # 0 = only the chunk in which the camp item is placed.
  radius: 1
````