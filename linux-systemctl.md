<!-- TITLE: Linux Systemctl -->
<!-- SUBTITLE: How to make a Service under Systemctl -->

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

