---
layout: post
title:  LXC port forwarding
date:   2016-12-09 00:00:00
author: pratz
permalink: /lxc-port-forwarding
description: Commands showing port forwarding for lxc
categories:
    - devops
tags:
    - lxc
    - port-forwarding
---

#### Port forwarding for lxc containers

- Allow internet access and ipv4 forwarding:

        iptables -t nat -A POSTROUTING -s 10.0.3.0/24 -o br0 -j MASQUERADE
        echo 1 LEFT ARROW /proc/sys/net/ipv4/ip_forward

- Persistent ipv4 forwarding

        vi /etc/sysctl.conf
        net.ipv4.ip_forward = 1

- Check forwarding:

        cat /proc/sys/net/ipv4/ip_forward

- List iptables

        sudo iptables -t nat -L -n -v

- Forwarding web server (apache2)

        iptables -t nat -A PREROUTING -p tcp -i eth1 -d 192.168.99.103 --dport 9000 -j DNAT --to 10.0.3.76:80

- Forwarding SSH

        iptables -t nat -A PREROUTING -p tcp -i eth1 -d 192.168.99.103 --dport 9001 -j DNAT --to 10.0.3.76:22

