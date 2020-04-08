---
title: Authenticate Your Users
description: In this step you authenticate your users via the JWTs you created earlier
---

# Authenticate Your Users

Your users must be authenticated to be able to participate in the `Conversation`. Login screen (`LoginFragment` and `LoginViewModel` classes) is responsible for authenticating the users.

![LoginFragment UI](/assets/images/client-sdk/android-in-app-messaging-chat/login-fragment-ui.png)

> **NOTE:** You perform this authentication using the `JWTs` generated and provided in a previous steps. 

```tabbed_content
source: '_tutorials_tabbed_content/client-sdk/tutorials/android-in-app-messaging-chat/authenticate-users'
```

We're now ready to fetch the conversation within the app.