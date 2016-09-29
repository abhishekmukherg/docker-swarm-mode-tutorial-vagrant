# Docker swarm mode Tutorial Vagrant setup

This is just a simple repository to help get someone setup on following the
[docker swarm-mode
tutorial](https://docs.docker.com/engine/swarm/swarm-tutorial/). These boxes
are _not_ yet set up for actually running swarm-mode command. The purpose of
these boxes is so you can create your own swarm-mode cluster by hand (practice
for actually doing it IRL).

## Requirements

* Vagrant (obviously)
* VirtualBox
* Ansible installed on your host

## What this comes with

You'll be set up with a manager and two workers that are set up already per the
first page of [the
tutorial](https://docs.docker.com/engine/swarm/swarm-tutorial/), since this is
the non-interesting part of the tutorial. The IP address of the master should
be 192.168.99.100, as suggested in the tutorial. You should be able to skip
right ahead to [create a
swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/)
