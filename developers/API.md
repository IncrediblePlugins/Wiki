[![](https://jitpack.io/v/IncrediblePlugins/BetterFarmingAPI.svg)](https://jitpack.io/#IncrediblePlugins/BetterFarmingAPI)

### Javadoc
See here: [Link](https://jitpack.io/com/github/incredibleplugins/BetterFarmingAPI/latest/javadoc/)

### API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:BetterFarmingAPI:version"
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
        <artifactId>BetterFarmingAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the ``BetterFarmingAPI`` interface.
BetterFarming needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
BetterFarmingAPI api = BetterFarmingAPI.getInstance();
````
