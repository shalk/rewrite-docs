# Migrate `anyOf` Hamcrest Matcher to AssertJ

**org.openrewrite.java.testing.hamcrest.HamcrestOfMatchersToAssertJ**

_Migrate the `anyOf` Hamcrest Matcher to AssertJ's `satisfiesAnyOf` assertion._

## Source

[GitHub](https://github.com/openrewrite/rewrite-testing-frameworks/blob/main/src/main/java/org/openrewrite/java/testing/hamcrest/HamcrestOfMatchersToAssertJ.java), [Issue Tracker](https://github.com/openrewrite/rewrite-testing-frameworks/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-testing-frameworks/2.0.9/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-testing-frameworks
* version: 2.0.9


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-testing-frameworks:2.0.9` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.1.26")
}

rewrite {
    activeRecipe("org.openrewrite.java.testing.hamcrest.HamcrestOfMatchersToAssertJ")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-testing-frameworks:2.0.9")
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
            <recipe>org.openrewrite.java.testing.hamcrest.HamcrestOfMatchersToAssertJ</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-testing-frameworks</artifactId>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-testing-frameworks:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.testing.hamcrest.HamcrestOfMatchersToAssertJ
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Contributors
* [Aleksandar A Simpson](mailto:alek@asu.me)
* [Tim te Beek](mailto:tim@moderne.io)


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.testing.hamcrest.HamcrestOfMatchersToAssertJ)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.