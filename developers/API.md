[![](https://jitpack.io/v/Angeschossen/ChestProtectAPI.svg)](https://jitpack.io/#Angeschossen/ChestProtectAPI)

# Javadoc
https://jitpack.io/com/github/angeschossen/ChestProtectAPI/latest/javadoc/

# API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:ChestProtectAPI:version"
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
        <artifactId>ChestProtectAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the [ChestProtectAPI](https://javadoc.jitpack.io/com/github/angeschossen/ChestProtectAPI/4.13.10/javadoc/me/angeschossen/chestprotect/api/ChestProtectAPI.html) interface.
UpgradeableHoppers needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
ChestProtectAPI api = ChestProtectAPI.getInstance();
````
