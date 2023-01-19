---
title: Mobsf
description: A quick summary of Mobsf
published: true
date: 2023-01-19T16:56:38.005Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:22:57.593Z
---

# Static apk analysis
Highlights findings that you'd go have to investigate.

Note that setup.sh needs a handful of packages installed libxml-dev I think was one.  Once those are installed rerun setup.sh.  Building by hand was hard and I never worked it out.

# Run in a docker

```
docker pull opensecurity/mobile-security-framework-mobsf
docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

# If you want persistence
Not sure if uid:gid is correct here (9901 stuff)
```
mkdir <dirname>
chown 9901:9901 <dirname>
docker run -it --rm --name mobsf -p 8000:8000 -v <dirname>:/home/mobsf/.MobSF opensecurity/mobile-security-framework-mobsf:latest
```

# Or you can build from docker file (why?)
```
git clone https://github.com/MobSF/Mobile-Security-Framework-MobSF.git
cd Mobile-Security-Framework-MobSF
docker build -t mobsf .
docker run -it --rm -p 8000:8000 mobsf
```
