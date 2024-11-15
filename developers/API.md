[![](https://jitpack.io/v/IncrediblePlugins/DiscordBridgeAPI.svg)](https://jitpack.io/#IncrediblePlugins/DiscordBridgeAPI)

### Javadoc
See here: [Link](https://jitpack.io/com/github/incredibleplugins/DiscordBridgeAPI/latest/javadoc/)

### API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:DiscordBridgeAPI:version"
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
        <artifactId>DiscordBridgeAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the ``DiscordBridgeAPI`` interface.
DiscordBridge needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
DiscordBridgeAPI api = DiscordBridgeAPI.getInstance();
````
