---
layout: post
title:  Artifactory python client
date:   2017-02-04 00:00:00
author: pratz
permalink: /artifactory-python-client
description: Python api client for artifactory
categories:
    - api-client
tags:
    - python
    - artifactory
    - api
---

#### Py-Artifactory
[**Artifactory**](https://www.jfrog.com/artifactory) is a artifact repository manager which supports software packages created by different technologies.
It can also be integrated with major CI/CD and DevOps tools.
This article shows how we can communicate with artifactory using a python api client.


#### Pre-requisites:
- Python 2.7 or higher
- libxml2/libxslt (will be deprecated in future releases)

        # Debian based
        sudo apt-get install libxml2-dev libxslt1-dev

        # RedHat based
        sudo yum install libxml2-devel libxslt-devel


#### Installation:
- Fire-up below command in terminal, `tag` specifies a version number.

        pip install git+https://github.com/veritasos/py-artifactory.git@<tag>


#### Usage:
- Create client instance

        from artifactory import Artifactory
        artifactory = Artifactory(
                url="http://127.0.0.1:8081",
                username="username",
                password="password",
                )

- List users

        user_list = artifactory.security.users.list()

- Get user

        user = artifactory.security.users.fetch("user.name")


- Create user

        user = artifactory.security.users.new()
        user.name = "first.last"
        user.password = "test"
        user.email = "first.last@testartifactory.com"
        user.groups = ["readers"]
        response = user.create()


- And much more ......

        Artifactory Users
        Artifactory Groups
        Artifactory Permissions
        Artifactory Repositories
        Artifactory Repository Replication
        Artifactory LDAP
        Artifactory User Api Keys


#### Detailed documentation:
A much more detailed documentation is provided here [**py-artifactory**](https://github.com/VeritasOS/py-artifactory)


[**Feel free to Contribute back**](https://github.com/pratz/py-openemm)
