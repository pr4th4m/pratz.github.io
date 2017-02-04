---
layout: post
title:  Netrc python client
date:   2016-03-07 00:00:00
author: pratz
permalink: /netrc-python-client
description: python api client for netrc
categories:
    - configuration
tags:
    - python
    - netrc
    - api
---

#### What is Netrc file ?
Netrc file contains user credentials and is used to auto-login. It is usually located in users home directory `.netrc` but location can be overridden with `NETRC` environment variable. Netrc also supports macros `macdef` to automate tasks. Netrc can be used with ftp, curl, git etc.


#### Netrc file sample:

    ~ $ cat .netrc
    machine product.company.com
    login first.last
    password secret-password

    macdef macro-name1
    command1
    command2


#### Get client:

    curl -o netrc_client.py  "https://gist.githubusercontent.com/pratz/789dc165c6d9f79be86608547b128c69/raw/41fb7796f6b6d0a09ac5ddeaf8c79de30a2387ed/NetRc%2520-%2520read,%2520write,%2520update"


#### Client compatibility:
    - Linux/Mac
    - Python 2.7.x


#### Usage:

    # create client
    netrc_instance = NetRc(
            "product.company.com",
            login="first.last",
            password="secret-password",
            account="", # account is optional
            )

    # create or update file content
    netrc_instance.create_or_update()

    # Custom file path (not recommended, as other programs might look for .netrc in users home directory)
    NETRC_FILE_PATH = /custom/file/path
    netrc_instance.create_or_update(path=NETRC_FILE_PATH)


#### Warning:
- Netrc stores credentials in plan text. This is how netrc is meant to be ;)


#### Use case:
- Its a good idea to use netrc when you have token based authentication.
- Automation for service accounts with token based authentication.
