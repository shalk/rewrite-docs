# Change property value

**org.openrewrite.properties.ChangePropertyValue**

_Change a property value leaving the key intact._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-properties/src/main/java/org/openrewrite/properties/ChangePropertyValue.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-properties/8.25.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-properties
* version: 8.25.0

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | propertyKey | The name of the property key whose value is to be changed. Supports glob patterns. | `management.metrics.binders.*.enabled` |
| `String` | newValue | The new value to be used for key specified by `propertyKey`. | `newValue` |
| `String` | oldValue | *Optional*. Only change the property value if it matches the configured `oldValue`. | `oldValue` |
| `Boolean` | regex | *Optional*. Default `false`. If enabled, `oldValue` will be interpreted as a Regular Expression, to replace only all parts that match the regex. Capturing group can be used in `newValue`. |  |
| `Boolean` | relaxedBinding | *Optional*. Whether to match the `propertyKey` using [relaxed binding](https://docs.spring.io/spring-boot/docs/2.5.6/reference/html/features.html#features.external-config.typesafe-configuration-properties.relaxed-binding) rules. Default is `true`. Set to `false`  to use exact matching. |  |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangePropertyValueExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangePropertyValueExample
displayName: Change property value example
recipeList:
  - org.openrewrite.properties.ChangePropertyValue:
      propertyKey: management.metrics.binders.*.enabled
      newValue: newValue
      oldValue: oldValue
```
{% endcode %}

Now that `com.yourorg.ChangePropertyValueExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.13.0")
}

rewrite {
    activeRecipe("com.yourorg.ChangePropertyValueExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}
{% tab title="Maven" %}
1. Add the following to your `pom.xml` file:
{% code title="pom.xml" %}
```xml
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>5.30.0</version>
        <configuration>
          <activeRecipes>
            <recipe>com.yourorg.ChangePropertyValueExample</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
2. Run `mvn rewrite:run` to run the recipe.
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe ChangePropertyValueExample
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.properties.ChangePropertyValue)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Jonathan Leitschuh](mailto:jonathan.leitschuh@gmail.com), [Jenson3210](mailto:jentesondervorst@gmail.com), [Nick McKinney](mailto:mckinneynicholas@gmail.com), [Jonathan Schneider](mailto:jkschneider@gmail.com), $(git --no-pager log --format=format:'%an' -n 1), [Tim te Beek](mailto:tim@moderne.io)
