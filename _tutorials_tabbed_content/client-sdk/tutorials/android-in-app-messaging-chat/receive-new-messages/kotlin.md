---
title: Kotlin
    language: kotlin
menu_weight: 1
---


All events we got so far are already in this conversation. So how do we display any new incoming messages? We can achieve this by implementing the conversation listener.

Firstly, inside `ChatViewModel` class, `getConversation()` method, add `conversation.addMessageEventListener`:

```kotlin
private fun getConversation() {
    client.getConversation(Config.CONVERSATION_ID, object : NexmoRequestListener<NexmoConversation> {

        override fun onSuccess(conversation: NexmoConversation?) {
            this@ChatViewModel.conversation = conversation

            conversation?.let {
                getConversationEvents(it)
                conversation.addMessageEventListener(messageListener)
            }
        }

        override fun onError(apiError: NexmoApiError) {
            this@ChatViewModel.conversation = null
            _errorMessage.postValue("Error: Unable to load conversation ${apiError.message}")
        }
    })
}
```

Now, locate the `private val messageListener = object : NexmoMessageEventListener` property in the `ChatFragment` class and implement conversation listener `onTextEvent(textEvent: NexmoTextEvent)` method:

```kotlin
    private val messageListener = object : NexmoMessageEventListener {
        override fun onTypingEvent(typingEvent: NexmoTypingEvent) {}

        override fun onAttachmentEvent(attachmentEvent: NexmoAttachmentEvent) {}

        override fun onTextEvent(textEvent: NexmoTextEvent) {
            updateConversation(textEvent)
        }

        override fun onSeenReceipt(seenEvent: NexmoSeenEvent) {}

        override fun onEventDeleted(deletedEvent: NexmoDeletedEvent) {}

        override fun onDeliveredReceipt(deliveredEvent: NexmoDeliveredEvent) {}
    }
```

Now each time new message is revieved `onTextEvent(textEvent: NexmoTextEvent)` listener will be called, new message will be passed to `updateConversation(textEvent: NexmoTextEvent)` method and dispatched to the view via  `conversationMessages` `LiveData` (same `LiveData` used to dispatch all the messages after loading conversation events).

The last thing to do is to make sure that all listeners will be removed when `ChatViewModel` is destroyed eg. when user navigates back. Fill the body of the `onCleared()` method in the `ChatViewModel` class.

```kotlin
override fun onCleared() {
    conversation?.removeMessageEventListener(messageListener)
}

```
