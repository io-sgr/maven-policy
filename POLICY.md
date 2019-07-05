# Maven Root POM - Policy overview

The following policies are enforced by the Maven Root POM:

* SpotBugs - [https://spotbugs.github.io/]
* PMD - [https://pmd.github.io/]
* Checkstyle - [https://checkstyle.sourceforge.io/]
* Code Coverage (JaCoCo) - [http://www.eclemma.org/jacoco/]

## PMD Plugin

Ignore code in

* `target/generated-sources/stubs`
* `target/generated-sources/annotations`

Activate our own PMD rules.

## Checkstyle Plugin

Activate our own Checkstyle to match code style.


## Rules

### PMD

The full list of active rules is in the [PMD Standard Ruleset](./maven-rules/src/main/resources/pmd/sgr/sgr-standard.xml).

The ruleset should only be referenced as `pmd/sgr.xml` which allows refactoring and modification of the rule sets without rewriting pom files all the time.

### Checkstyle

The list of rules is in the [checkstyle set](./maven-rules/src/main/resources/checkstyle/sgr.xml). There is an additional [javadoc checkstyle set](./maven-rules/src/main/resources/checkstyle/sgr-javadoc.xml) which also enforces basic Javadoc formatting.

Files in `generated-sources` folders are ignored.

The javadoc checkstyle is activated by default.

To use the non-javadoc enabled checkstyle rules, use

```xml
<plugins>
    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <configuration>
            <configLocation>checkstyle/sgr.xml</configLocation>
        </configuration>
    </plugin>
</plugins>
```

in the root POM of a project.

### SpotBugs

Findbugs is run at `Max` effort.
