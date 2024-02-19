# Migration von 2022 zu 2023

Unter src/test/integration/$appname/resources/META-INF/persistence.xml

```xml
<persistence>
    ...
    <!-- neue mappings hinzufügen -->
    <mapping-file>META-INF/mycore-jobqueue-mappings.xml</mapping-file>
    <mapping-file>META-INF/mycore-viewer-mappings.xml</mapping-file>
    ...
    
    <properties>
        ...
        <!-- neue properties hinzufügen -->
        <property name="hibernate.auto_quote_keyword" value="true" />
        ...
    </properties>
</persistence>
```

Remove the following files from pom.xml:

```xml

<dependency>
    <groupId>com.sun.activation</groupId>
    <artifactId>jakarta.activation</artifactId>
</dependency>
```

Change the version in the pom.xml:

```xml
<project>
    <parent>
        <groupId>de.gbv.reposis</groupId>
        <artifactId>reposis_mir_parent</artifactId>
        <version>2023.06-SNAPSHOT</version> <!-- this -->
    </parent>

    <artifactId>reposis_$id</artifactId>
    <version>2023.06-SNAPSHOT</version> <!-- this -->
</project>
```