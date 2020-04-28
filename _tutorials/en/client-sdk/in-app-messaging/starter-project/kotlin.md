---
title: Kotlin
language: kotlin
menu_weight: 1
---

Open `Config.kt` file and add fill:

1. `Jane`'s user Id and JWTs
1. `Joe`'s user Id and JWTs
1. `CONVERSATION_ID` you've created on the previous steps:

```kotlin
package com.vonage.tutorial.messaging

data class User(
    val name: String,
    val jwt: String
)

object Config {

    const val CONVERSATION_ID: String = "" // TODO: set conversation Id

    val jane = User(
        "Jane",
        "" // TODO: "set Jane's JWT token"
    )
    val joe = User(
        "Joe",
        "" // TODO: set Joe's JWT token"
    )
}

```

Notice that we hardcoded these cons and values to store the properties of users. This might feel a bit out of place but makes it easier to use later on in this tutorial.