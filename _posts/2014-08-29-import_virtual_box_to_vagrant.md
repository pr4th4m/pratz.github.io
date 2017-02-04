---
layout: post
title:  Import virtual box machine to vagrant
date:   2014-08-29 00:00:00
author: pratz
permalink: /import-virtual-box-machine-to-vagrant
description: Commands to import virtual box machines to vagrant
categories:
    - devops
tags:
    - lxc
    - port-forwarding
---

#### Import existing virtual box machines to vagrant

- Package a `.box` file using the following command:

        vagrant package --base <vm_name> --output <output.box>

        # vm_name - Name of the existing virtual box vm
        # output.box - Output box file name


- Add newly created box file to vagrant using following command:

        vagrant box add <box_name> <output.box>

        # box_name - Name of vagrant box
        # output.box - Newly created box file
