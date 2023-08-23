# Migrate Lombok to a Java 11 compatible version

**org.openrewrite.java.migrate.lombok.UpdateLombokToJava11**

_Update Lombok dependency to a version that is compatible with Java 11 and migrate experimental Lombok types that have been promoted._

### Tags

* java17
* lombok

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/lombok.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/2.0.9/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 2.0.9


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:2.0.9` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.1.26")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.lombok.UpdateLombokToJava11")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:2.0.9")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven POM" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>5.4.2</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.migrate.lombok.UpdateLombokToJava11</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>2.0.9</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.lombok.UpdateLombokToJava11
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Upgrade Gradle or Maven dependency versions](../../../java/dependencies/upgradedependencyversion.md)
  * groupId: `org.projectlombok`
  * artifactId: `lombok`
  * newVersion: `1.18.*`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `lombok.experimental.Builder`
  * newFullyQualifiedTypeName: `lombok.Builder`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `lombok.experimental.Value`
  * newFullyQualifiedTypeName: `lombok.Value`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `lombok.experimental.Wither`
  * newFullyQualifiedTypeName: `lombok.With`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `lombok.experimental.var`
  * newFullyQualifiedTypeName: `lombok.var`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `lombok.experimental.val`
  * newFullyQualifiedTypeName: `lombok.val`
* [Prefer `final var`](../../../java/migrate/lombok/lombokvaltofinalvar.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.lombok.UpdateLombokToJava11
displayName: Migrate Lombok to a Java 11 compatible version
description: Update Lombok dependency to a version that is compatible with Java 11 and migrate experimental Lombok types that have been promoted.
tags:
  - java17
  - lombok
recipeList:
  - org.openrewrite.java.dependencies.UpgradeDependencyVersion:
      groupId: org.projectlombok
      artifactId: lombok
      newVersion: 1.18.*
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: lombok.experimental.Builder
      newFullyQualifiedTypeName: lombok.Builder
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: lombok.experimental.Value
      newFullyQualifiedTypeName: lombok.Value
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: lombok.experimental.Wither
      newFullyQualifiedTypeName: lombok.With
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: lombok.experimental.var
      newFullyQualifiedTypeName: lombok.var
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: lombok.experimental.val
      newFullyQualifiedTypeName: lombok.val
  - org.openrewrite.java.migrate.lombok.LombokValToFinalVar

```
{% endtab %}
{% endtabs %}

## Contributors
* [Tim te Beek](mailto:tim.te.beek@jdriven.com)
* [Patrick](mailto:patway99@gmail.com)
* [Knut Wannheden](mailto:knut@moderne.io)
* Tyler Van Gorder
* [Sam Snyder](mailto:sam@moderne.io)
* [Jonathan Schnéider](mailto:jkschneider@gmail.com)


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.migrate.lombok.UpdateLombokToJava11)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.