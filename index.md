---
title: ionSpring home
layout: default
---

# Introduction

> ionSpring makes it easy to create web application for IBM i platform.
>
> This is not a new framework but rather an opinionated and very light preconfiguration of existing frameworks and some small adapters for IBM i.
>
> Open source under Apache Software License 2.0

The following frameworks/libraries are used:
* [Spring Boot](https://spring.io/projects/spring-boot){:target="_blank"}: the leading Java application framework
* [Vaadin Flow](https://vaadin.com){:target="_blank"}: A Java web framework
* [Karibu-DSL](https://github.com/mvysny/karibu-dsl){:target="_blank"}: Kotlin extensions and DSL library for Vaadin Flow

# Getting started

* Create a Spring Boot Project with [Spring initializr](https://start.spring.io/#!type=gradle-project-kotlin&language=kotlin&packaging=jar&jvmVersion=17&groupId=com.example&artifactId=demo&name=demo&description=Demo%20project%20for%20Spring%20Boot&packageName=com.example.demo&dependencies=vaadin,devtools){:target="_blank"}
* Decompress the generated project and open it with your IDE ([Intellij IDEA](https://www.jetbrains.com/idea/){:target="_blank"} is recommended)
* Edit the `build.gradle.kts` file. Add the following two lines inside the `dependency` block:

```kotlin
implementation("org.ionspring:ionspring-starter:0.1.0")
```

* In `src/main/kotlin`, in the package of the application, create a new Kotlin class with the following content:

```kotlin
package com.example.demo

import com.github.mvysny.karibudsl.v10.span
import com.github.mvysny.karibudsl.v10.textField
import com.vaadin.flow.component.html.Span
import com.vaadin.flow.component.orderedlayout.VerticalLayout
import com.vaadin.flow.data.value.ValueChangeMode
import com.vaadin.flow.router.PageTitle
import com.vaadin.flow.router.Route

@Route("")
@PageTitle("Demo home")
class HomeView : VerticalLayout() {
  lateinit var span: Span

  init {
    textField("Your name") {
      valueChangeMode = ValueChangeMode.EAGER
      addValueChangeListener { e ->
        if (e.value.isBlank()) {
          span.text = "What's your name?"
        } else {
          span.text = "Hello ${e.value}"
        }
      }
    }
    span = span("What's your name?")
  }
}
```

* Start the application from your IDE
* Open [https://localhost:8080](http://localhost:8080" target="_blank">https://localhost:8080){:target="_blank"} in your browser:

![Getting started](/assets/img/getting-started.gif)

# Where to go next?

* [Project Github repository](https://github.com/ionspring/ionspring)
* [Examples Github repository](https://github.com/ionspring/ionspring-examples)