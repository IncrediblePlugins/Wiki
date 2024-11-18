Adding support for your own item stacking plugin is easy. Make sure you [setup the API](API.md)
then just impletemt the ``ItemStackerProvider`` interface and set it as seen below.
````java
ItemStackerProvider provider = new ItemStackerProvider() {
    ...
}

UpgradeableHoppersAPI.getInstance().setItemStackerProvider(provider);
````