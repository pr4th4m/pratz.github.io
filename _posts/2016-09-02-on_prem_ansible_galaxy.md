---
layout: post
title:  On-prem ansible galaxy
date:   2016-09-02 00:00:00
author: pratz
permalink: /on-prem-ansible-galaxy
description: Use git as ansible galaxy inside company premises
categories:
    - infrastructure-management
tags:
    - ansible
    - ansible-galaxy
---

#### On-prem ansible galaxy
Generic ansible roles can be shared through [ansible galaxy](https://galaxy.ansible.com) though in many cases we can not use ansible galaxy as its hosted publicly. Solution is to host something similar to ansible galaxy on-prem.


##### On-prem galaxy repository
- For this blog I am considering stash (https://stash.company.com) but gitlab, gogs or similar should work as well
- Create a new project on stash `Ansible Galaxy` with key `AG`
- Create repo for each generic ansbile role.
- We can browse through all the generic ansbile roles at https://stash.company.com/projects/AG
- Now these roles can be used with multiple ansible playbooks.


##### Usage
- Create a new file `requirements.yml` alongside ansible `playbook.yml`.
- For this blog purposes I am considering `awscli` as an generic ansible role with its own repo, which resides in our newly created stash project `Ansible Galaxy (AG)`
- Copy/paste below content to `requirements.yml`

        ---
        name: awscli
        src: git+https://stash.company.com/scm/ag/awscli
        version: master
        path: ~/.ansible/roles

        # name - name of role
        # src - location of role
        # version - which branch the role should be installed from
        # path - where we want to install roles

- The `requirements.yml` files acts as a role dependency list for our `playbook.yml`


##### Installation
- Once we define our ansible playbook dependencies, its time to install them.

        sudo ansible-galaxy install -r requirements.yml

        # NOTE: no need to install ansible-galaxy seperately, it ships with default ansible installation

- Done! all the roles are now installed and ready to be used by our `playbook.yml`
