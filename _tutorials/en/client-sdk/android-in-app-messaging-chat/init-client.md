---
title: Initialize the client
description: In this step you will initialize `NexmoClient`, so it can be used within the application.
---

# Initialize the client

[NexmoClient](https://developer.nexmo.com/sdk/stitch/android/com/nexmo/client/NexmoClient.html) is the main class used to interact with `Android-Client-SDK`. Prior to usage we have to initialize the client by providing instance of the Android [Context](https://developer.android.com/reference/android/content/Context) class. The best place to initialize the client is the custom Android [Application](https://developer.android.com/reference/android/app/Application) class.

```tabbed_content
source: '_tutorials_tabbed_content/client-sdk/tutorials/android-in-app-messaging-chat/init-client'
```

We have working client so let's authenticate the users.