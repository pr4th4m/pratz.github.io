---
layout: post
title:  Raspberry pi setup NFS and SMB server
date:   2017-04-20 00:00:00
author: pratz
permalink: /raspi-nfs-smb
description: Setup NFS and samba server on raspberry pi
categories:
    - electronics
tags:
    - raspberry-pi
    - nfs
    - samba
---

#### NFS server
- Install server

        sudo apt install nfs-common nfs-server

- Create directory you wanna share

        mkdir /media/storage

- Edit file `/etc/exports` with below content

        /media/storage 192.168.1.0/24(rw,all_squash,insecure,no_subtree_check)
        # <directory> <who_can_access> <options>

- Restart services

        sudo service nfs restart
        /etc/init.d/nfs-kernel-server restart

- Connecting from client (MacOS)

        mkdir /Users/username/nfs_shared
        sudo mount -v -o "resvport" 192.168.1.9:/media/storage /Users/username/nfs_shared


#### Samba server
- Install server

        sudo apt-get install samba samba-common-bin

- Create samba password for system user

        sudo smbpasswd -a pi

- Create directory you wanna share

        mkdir /media/storage

- Edit file `/etc/samba/smb.conf` with below content

        [PI]
        comment = Pi workspace
        path = /media/storage
        create mask = 0775
        directory mask = 0775
        read only = no
        browseable = yes
        public = no
        force user = pi
        only guest = no

- Restart service

        sudo service samba restart

- Connecting from client (MacOS)

        mkdir /Users/username/smb_shared
		mount -t smbfs //pi@192.168.1.9/pi /Users/username/smb_shared
