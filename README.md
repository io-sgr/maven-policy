# Maven Root POM

Using this root pom as the parent of a project at io.sgr will do the following things:

- Inherit from the [BasePOM Project](https://github.com/basepom/basepom/)
- Enable the release plugin to build a javadoc jar when releasing a project
- Apply some basic policy to the project


## How to set it up

* IntelliJ IDEA code formatter: load [the configuration file](./IDE/intellij/SgrCodeStyle.xml) into the IDE.


## How to use it

The Maven Root POM provides a common set of configurations for maven plugins to build Java projects. Most of the time, it should no longer be necessary to have any `<plugin>` or `<pluginManagement>` sections in the project POMs.

The pom is activated by adding it as parent to the project POM. Add the following snippet to the POM in the root of a project:

```xml
<parent>
    <groupId>io.sgr.maven</groupId>
    <artifactId>maven-base</artifactId>
    <version>1.0.9-SNAPSHOT</version>
</parent>
```

This should be enough for most projects that use JDK 1.8.

The [policy overview](POLICY.md) contains more information about the policies set in the Maven root POM.
