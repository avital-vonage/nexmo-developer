---
title: Fetch the conversation
description: In this step you join your Users to your Conversation
---

# Fetch the Conversation

Chat screen (`ChatFragment` and `ChatViewModel` classes) is responsible for fetching the conversation and all the conversation evets.

![ChatFragment UI](/assets/images/client-sdk/android-in-app-messaging-chat/chat-fragment-ui.png)

View (`ChattFragment`) creation results in calling `viewModel.getConversation()` method tha loads the conversation.

```tabbed_content
source: '_tutorials_tabbed_content/client-sdk/tutorials/android-in-app-messaging-chat/fetch-conversation'
```
