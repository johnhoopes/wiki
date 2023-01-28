---
title: Linux Systemctl
description: How to make a Service under Systemctl
published: true
date: 2023-01-28T16:07:33.829Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:21:21.191Z
---

# Make a .service file

```text
[Unit]
Description=My Service
After=network.target

[Service]
ExecStart=/usr/bin/my-service
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

# Installation

```text
cp my-service.service /lib/systemd/system

systemctl daemon-reload
systemctl enable my-service
```

# User Services
apparently normal users can make services.
Need linger permission (see below)
```text
~/.config/systemd/user/weechat.service

[Unit]
Description=Weechat IRC Client (in tmux)
After=network-online.target

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/bin/tmux -2 -u new-session -d -s irc /usr/bin/weechat
ExecStop=/usr/bin/tmux kill-session -t irc

[Install]
WantedBy=default.target
```

# Linger
run following as root to allow service after login
```
# loginctl enable-linger <user>
```
run this to show users permission
```
> loginctl show-user $(whoami) --property Linger
```

# Checking the log

```text
journalctl --unit my-service --follow
```

