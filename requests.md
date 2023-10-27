---
title: Requests
description: HTTP Library so you're not writing it every time
published: true
date: 2023-10-27T14:24:32.166Z
tags: 
editor: markdown
dateCreated: 2023-10-27T14:24:32.166Z
---

# Simple Get
`r = requests.get('URL')`

r.text - response body
r.status_code - 
r.headers -
r.request.body - (I think this is it, but request is how to see what it actually sent)

cookies = {}
cookies = {'csrftoken':1234}

r = request.get('URL', cookies = cookies)


# Simple Post

payload = "This is some content"

r = requests.pull('URL', data=payload)



# Proxies

proxies = {"https":"127.0.0.1:8080"}
r = s.post(url, data = payload, proxies = proxies, verify=False)

