---
title: Cygwin Python Installation to avoid site vs distro package issues
description: 
published: true
date: 2023-01-19T15:37:18.776Z
tags: 
editor: markdown
dateCreated: 2023-01-19T15:37:18.776Z
---

# Source
https://sick.codes/python-cygwin-venv-the-only-way-to-install-python2-and-python3-on-cygwin-and-use-it-properly/

Install these packages first:
```
python3 python27 python27-devel python3-devel python27-virtualenv python3-virtualenv
```

# From cygwin command line
```
wget https://raw.githubusercontent.com/transcode-open/apt-cyg/master/apt-cyg -O /bin/apt-cyg
chmod a+x /bin/apt-cyg
/bin/apt-cyg --version
apt-cyg update
apt-cyg install diffutils git bash bash-completion openssh sshpass zstd rsync zip
apt-cyg install cygwin64-gcc-core cygwin64-gcc-g++ gcc-fortran make automake alternatives ca-certificates zlib0
apt-cyg install python python3 python-devel python3-devel python-virtualenv python3-virtualenv
apt-cyg install make automake gcc-core gcc-g++ zlib zlib-devel libffi-devel openssl-devel
```
Notes:  
cygwin64-gcc-core and cygwin64-gcc-g++ didn't exist.
Wherever it said python-* I needed to change it to python27 (deprecated 27)

Then activate as normal with v2 or v3