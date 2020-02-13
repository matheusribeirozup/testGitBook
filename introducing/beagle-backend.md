---
description: Getting started with Beagle in backend for frontend (BFF)
---

# Beagle Backend

## Requirements

* Kotlin 1.3+
* Maven 3+
* Spring Boot 2+ or Micronaut 1.2+
* Jackson 2+

## Setting up the dependency

Add Zup's repository.

{% tabs %}
{% tab title="pom.xml" %}
```markup
<repositories>
	<repository>
		<id>beagle-nexus</id>
		<name>Beagle Nexus Repository</name>
		<url>https://repo-iti.zup.com.br/repository/beagle-jars-all/</url>
	</repository>
</repositories>
```
{% endtab %}
{% endtabs %}

Add a dependency for Beagle framework.

{% tabs %}
{% tab title="pom.xml" %}
```markup
<dependency>
	<groupId>br.com.zup.beagle</groupId>
	<artifactId>framework</artifactId>
	<version>${beagle.framework.version}</version>
</dependency>
```
{% endtab %}
{% endtabs %}

## Add Beagle serializers

In your project configuration, add the Beagle serializers to Jackson's ObjectMapper.

```kotlin
val mapper = ObjectMapper()
val module = SimpleModule()
module.addSerializer(BeagleWidgetSerializer())
module.addSerializer(BeagleActionSerializer())
module.addSerializer(BeagleScreenSerializer())
mapper.registerModule(module)
```

