---
layout: post
title:  Git login with Netrc
date:   2016-04-01 09:43:59
author: pratz
permalink: /git-auto-login-with-netrc
description: Login to git automatically with netrc
cover:  /assets/posts/git.jpg
categories:
    - version-control-system
tags:
    - git
    - netrc
---

#### What is Netrc file ?
Netrc file contains user credentials and is used to auto-login. It is usually located in users home directory `.netrc` but location can be overridden with `NETRC` environment variable. Netrc also supports macros `macdef` to automate tasks. Netrc can be used with ftp, curl, git etc.


#### Netrc file:
- Create file named `.netrc` in home directory.
- Lets consider your git server is hosted on domain `git.company.com`

        ~ $ cat .netrc
        machine git.company.com
        login first.last
        password secret-password

#### Secure netrc file:
- As `.netrc` is used to store credentials, lets secure the file.

        ~ $ chmod 0600 ~/.netrc


That's it, next time when you use git for domain `git.company.com`, git should pick up the credentials on behalf of you ;)


#### Warning:
- Netrc stores credentials in plan text. This is how netrc is meant to be ;)


#### Use case:
- Its a good idea to use netrc when you have token based authentication.
- Automation for service accounts with token based authentication.
