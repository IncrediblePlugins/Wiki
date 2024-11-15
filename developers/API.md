[![](https://jitpack.io/v/IncrediblePlugins/FasterFurnacesAPI.svg)](https://jitpack.io/#IncrediblePlugins/FasterFurnacesAPI)

# Javadoc
Can be found [here](https://jitpack.io/com/github/incredibleplugins/FasterFurnacesAPI/latest/javadoc/).

# API Usage Explained
Include the API using Gradle:
```groovy
repositories {
	maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly "com.github.angeschossen:FasterFurnacesAPI:version"
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
        <artifactId>FasterFurnacesAPI</artifactId>
        <version>version</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
Replace `version` with the version that you want to use.

The API is accessible through an implementation of the [FasterFurnacesAPI](https://javadoc.jitpack.io/com/github/angeschossen/FasterFurnacesAPI/4.13.10/javadoc/me/angeschossen/fasterfurnaces/api/FasterFurnacesAPI.html) interface.
FasterFurnaces needs to be loaded before this API can be used. It doesn't need to be enabled though.
````java
FasterFurnacesAPI api = FasterFurnacesAPI.getInstance();
````
