# API

The current FasterFurnaces API module is intentionally very small.

It exposes:

```java
me.angeschossen.fasterfurnaces.api.Furnace
```

`Furnace` is a marker interface for upgradeable furnace objects. This source tree does not expose a public `FasterFurnacesAPI` singleton or a higher-level service API.

## Dependency

The API module is built as `fasterfurnaces-api`.

Gradle example:

```groovy
repositories {
    maven { url 'https://repo.incredibleplugins.com/releases' }
}

dependencies {
    compileOnly 'com.github.angeschossen:fasterfurnaces-api:version'
}
```

Replace `version` with the version you want to compile against.

## Notes

Do not build against relocated plugin internals from the shaded plugin jar. If you need functionality that is not exposed by the API module, request a dedicated API addition instead of relying on implementation classes.
