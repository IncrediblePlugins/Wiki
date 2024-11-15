[![](https://jitpack.io/v/Angeschossen/UpgradeableHoppersAPI.svg)](https://jitpack.io/#Angeschossen/UpgradeableHoppersAPI)

# Javadoc
https://jitpack.io/com/github/angeschossen/UpgradeableHoppersAPI/latest/javadoc/

# API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:UpgradeableHoppersAPI:version"
}
```
Replace `version` with the version that you want to use.

Include the API using Maven:
```xml
<repositories>
	<repository>
		<id>jitpack.io</id>
		<url>https://jitpack.io</url>
	</repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.github.angeschossen</groupId>
        <artifactId>UpgradeableHoppersAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the [UpgradeableHoppersAPI](https://javadoc.jitpack.io/com/github/angeschossen/UpgradeableHoppersAPI/4.13.10/javadoc/me/angeschossen/upgradeablehoppers/api/UpgradeableHoppersAPI.html) interface.
UpgradeableHoppers needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
UpgradeableHoppersAPI api = UpgradeableHoppersAPI.getInstance();
````
