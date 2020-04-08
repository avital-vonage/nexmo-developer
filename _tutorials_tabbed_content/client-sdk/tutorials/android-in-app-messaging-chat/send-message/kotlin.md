---
title: Kotlin
language: kotlin
menu_weight: 1
---


Inside `ChatViewModel` class, locate the `onSendMessage` method and fill its the body:

```kotlin
fun onSendMessage(message: String) {
        if (conversation == null) {
            _errorMessage.postValue("Error: Conversation does not exist")
            return
        }

        conversation?.sendText(message, object : NexmoRequestListener<Void> {
            override fun onSuccess(p0: Void?) {
            }

            override fun onError(apiError: NexmoApiError) {
            }
        })
    }
```

> **NOTE:** Inside `ChatFragment` class, contains `sendMessageButton listener` that was written for you. This method is called when user click `send` button. If message text exists above `viewModel.onSendMessage()` method is called.

You'll notice that, although the message was sent, the conversation doesn't include it. We could be calling `getConversationEvents()` method each time after we send the message, but the SDK provides a beter way to handle this scenario.
