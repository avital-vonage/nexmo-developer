---
title: Kotlin
language: kotlin
menu_weight: 1
---
Locate the `BaseApplication` class and initialize `NexmoClient` using the builder:

```kotlin
class BaseApplication : Application() {

    override fun onCreate() {
        super.onCreate()
        
        NexmoClient.Builder().build(this)
    }
}
```

The above code will allow to retrieve `NexmoClient` instance later by using `NexmoClient.get()`.

> **NOTE:** You can enable additional `Logcat` logging by utilising `logLevel()` method of the builder eg.
`NexmoClient.Builder().logLevel(ILogger.eLogLevel.SENSITIVE).build(this)`
