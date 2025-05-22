---
title: Installing a CA Certificate on an IOS Mobile Device
description: 
published: true
date: 2025-05-22T19:59:16.590Z
tags: 
editor: markdown
dateCreated: 2025-05-22T19:59:16.590Z
---

# Enabling Burp Certificate in iPOD

Actually got something useful from an IBM site:
https://www.ibm.com/docs/en/mpf/7.1.0?topic=certificates-installing-root-ca-ios

Highlights
1. Get Cert in .crt form (Not PEM)
2. Email .crt file as attachment.
3. Open file, IOS will create a profile.
4. Go to settings -> General -> VPN & Device Management
5. Enable the profile.
6. General -> About -> Certificate Trust Settings
7. Slide switch to green.


