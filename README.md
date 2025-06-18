# Migration from 2023 to 2024

**Note**: *Persistence.xml* under *src/test/integration/$appname/resources/META-INF/*
is no longer used. The database is now configured via mycore properties.

**Note**: Java 21 and above is required.


Change the version in the pom.xml:

```xml
<project>
    <parent>
        <groupId>de.gbv.reposis</groupId>
        <artifactId>reposis_mir_parent</artifactId>
        <version>2024.06-SNAPSHOT</version> <!-- this -->
    </parent>

    <artifactId>reposis_$id</artifactId>
    <version>2024.06-SNAPSHOT</version> <!-- this -->
</project>
```