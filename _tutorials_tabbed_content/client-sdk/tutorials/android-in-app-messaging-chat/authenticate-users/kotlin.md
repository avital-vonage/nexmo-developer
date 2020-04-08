---
title: Kotlin
language: kotlin
menu_weight: 1
---
Now You have to retrieve client instance inside `LoginViewModel` class. Usually it would be provided it via injection, but for tutorial purposes you will retrieve instance directly using static method. Locate the `private val client` property in the `LoginViewModel` class and update it's implementation:

```kotlin
private var client = NexmoClient.get()
```

Locate the `onLoginUser` method within the `LoginViewModel` class and fill it's body to enable user login:

```kotlin
fun onLoginUser(user: User) {
    if (!user.jwt.isBlank()) {
        client.login(user.jwt)
    }
}
```

> **NOTE:** Inside `LoginFragment` class, explore the `loginUser` method that was written for you. This method is called when one of the two `Login as ...` buttons are clicked. This method calls above `onLoginUser` method. 

> **NOTE:** The `User` type is the `data class` that we've defined in the `Config.kt` file.


Now add connection listener to listen to the `client` instance to listen for connection state changes and use `_connectionStatus` `LiveData` to propagate new connection state to the view (`LoginFragment`). Locate the `init` block inside `LoginViewModel` class and repleace it with this code:


```kotlin
init {
    client.setConnectionListener { newConnectionStatus, _ ->
        _connectionStatus.postValue(newConnectionStatus)
    }
}
```

Now view needs to react to the newly dispatched connection state. Locate the `private val stateObserver` property within `LoginFragment` and fill it's body:

```kotlin
private val stateObserver = Observer<ConnectionStatus> {
    connectionStatusTextView.text = it.toString()

    if (it == ConnectionStatus.CONNECTED) {
        val navDirections = LoginFragmentDirections.actionLoginFragmentToChatFragment()
        findNavController().navigate(navDirections)
    } else if (it == ConnectionStatus.DISCONNECTED) {
        dataLoading = false
    }
}
```

The above code will display current connection state and if the user is authenticated (`ConnectionStatus.CONNECTED`) it will navigate user to the `ChatFragment` where user can view and interact with the conversation.
