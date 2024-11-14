# Levels
Levels can be configured in the levels.yml file of Lands.
The level of a land or nation can be retrieved using this method: [MemberHolder#getLevel](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/memberholder/MemberHolder.html#getLevel())

# Level Requirements
You can also add new level requirements programmatically. These must be added before Lands is fully enabled. The best way to achieve this, is registering the requirements at your onLoad method in your main class.\
* You can use this method in your `onLoad` method of your main class: [LandsIntegration#onLoad](https://javadoc.jitpack.io/com/github/angeschossen/LandsAPI/7.10.6/javadoc/me/angeschossen/lands/api/LandsIntegration.html#onLoad(java.lang.Runnable))
* Example: https://gist.github.com/Angeschossen/37f0e2b2641e2980d4a0ee489de81715