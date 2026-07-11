Since 6.26.0 the API has changed in some minor, but important ways.
Mostly methods and classes that have been deprecated for years have been removed.

# Changes
* You now create a LandsIntegration instance via the static method of the **LandsIntegration interface** not directly through an constructor. This improves maintainability and backward support in the future.
* ``getLand`` methods have been removed from the LandsIntegration. The reason is that it has been misused in the past to check flag states. The problem is that Lands offers sub areas inside lands. Therefore one should retrieve an `Area` to check flag states. Not just the land. As this check would only be done against the default area. Therefore, use ``getArea`` or ``getAreaUnloaded`` if the location is not loaded.
* The old ``LandSetting`` enums have been removed. Please use ``Flags.<Flag>`` instead.

