[![](https://jitpack.io/v/IncrediblePlugins/UpgradeableSpawnersAPI.svg)](https://jitpack.io/#IncrediblePlugins/UpgradeableSpawnersAPI)

### Javadoc
https://jitpack.io/com/github/incredibleplugins/UpgradeableSpawnersAPI/latest/javadoc/

### API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}
dependencies {
    compileOnly "com.github.angeschossen:UpgradeableSpawnersAPI:version"
}
```

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
        <artifactId>UpgradeableSpawnersAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

The API is accessible through an implementation of the ``UpgradeableSpawnersAPI`` interface.
UpgradeableSpawners needs to be loaded before this API can be used. It doesn't need to be enabled though.
````
UpgradeableSpawnersAPI api = UpgradeableSpawnersAPI.getInstance();
````
