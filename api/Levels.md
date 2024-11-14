# Levels
Levels can be configured in the levels.yml file of Lands.
The level of a land or nation can be retrieved using this method:
https://github.com/IncrediblePlugins/LandsAPI/blob/e16aaddb3bcb6104bbfcc2b4c4634f2bdc808ff4/src/main/java/me/angeschossen/lands/api/MemberHolder.java#L65

# Level Requirements
You can also add new level requirements programmatically. These must be added before Lands is fully enabled. The best way to achieve this, is registering the requirements at your onLoad method in your main class.\
Register example: https://gist.github.com/Angeschossen/37f0e2b2641e2980d4a0ee489de81715