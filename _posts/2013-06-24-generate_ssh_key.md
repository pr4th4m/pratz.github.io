---
layout: post
title:  Generate ssh key
date:   2013-06-24 00:00:00
author: pratz
permalink: /generate-ssh-key
categories:
    - protocol
tags:
    - ssh
---

#### Generate SSH key:

- To generate a new SSH key, copy and paste the command below, making sure to substitute in your email. The default settings are preferred, so when you're asked to "enter a file in which to save the key,"" just press enter to continue.

        $ ssh-keygen -t rsa -C "your_email@example.com"

- Creates a new ssh key, using the provided email as a label.

- Generating public/private rsa key pair.

        $ ssh-add id_rsa

- Next, you'll be asked to enter a passphrase

        Enter passphrase (empty for no passphrase):
        Enter same passphrase again:

- Which should give you something like this:

        Your identification has been saved in /home/you/.ssh/id_rsa.
        Your public key has been saved in /home/you/.ssh/id_rsa.pub.
        The key fingerprint is:
        01:0f:f4:xb:xa:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com

- Run the following command to copy the key to your clipboard.

        $ sudo apt-get install xclip
        $ xclip -sel clip < ~/.ssh/id_rsa.pub
