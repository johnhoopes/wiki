---
title: Telegram Notifications
description:  How to set up and use
published: true
date: 2023-08-01T16:40:25.941Z
tags: 
editor: markdown
dateCreated: 2023-08-01T16:40:03.118Z
---

# Setup

- Using your Telegram client, send a message to @BotFather with the command /newbot and follow the instructions.
- Note the bot token you receive after successfully registering the bot.
- Message your bot with a simple message like /start or /test

Then use 
```
curl -i -X GET https://api.telegram.org/bot<BOT_TOKEN>/getUpdates
```

to get a chat ID of the chat you made by messaging.

Now you have an API token and a Chat ID

```
curl -i -X GET "https://api.telegram.org/bot<BOT_TOKEN>/sendMessage?chat_id=<CHAT_ID>&text=hello"
```


All of this from:
https://bananamafia.dev/post/telegram-notifications/