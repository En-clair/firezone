---
layout: default
title: Resource Requirements
nav_order: 2
parent: Deploy
---
---

Firezone uses in-kernel WireGuard, so its performance should be very good. We
recommend starting with 1 vCPU and 1 GB of RAM and scaling up as the number of
users and bandwidth requirements grow. In general, more CPU cores translate to
higher bandwidth capacity per tunnel while more RAM will help with higher counts
of users and tunnels.

In the vast majority of cases, with WireGuard, your network link speed is going
to be the bottleneck before your CPU will.
