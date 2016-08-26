# containers-for-dev-environment
Setting up a container to use as a development environment

## Why

During my GTK3/Vala GUI development experiments, I soon encountered a big hurdle: it was absolutely necessary for me to get a recent version of GTK3, as some of the features I needed had been added in recent builds. As I was not ready to migrate my current Linux setup, I looked for a solution to build and use GTK3 (and many of its related libraries like ATK, GDK-pixbuf, etc.) from the sources.

My first environment was a dedicated VirtualBox setup. Which made sense since I use VirtualBox quite a lot for testing Linux & BSD dists. I did not even need to compile the latest sources, but the VM issues started to grow annoying: especially when a graphics driver update borked my install. Plus I could not use the created tools on my own setup. A major issue of course.

After that, I tried a local dev environment, using the "--prefix" option. It worked, but created a whole set of problems with the environment (icons & such). The whole GTK3 environment is dependent on many things, and themes as well as icons became a big annoyance as they were not properly detected (or did not exist in my setup) and this was really visually ugly.

Then I searched for a jail environment, with cgroups or the like, but soon realized it was annoying to setup.

Recently I looked into containers. After a bit of experimenting -I tested Docker then lxc then lxd- I determined that this was the easiest solution by far.

Currently, I think that Docker is the easiest & fastest to setup. For such a dev env (GUI dev), I'm not sure if lxc/lxd are any better (after all Docker is supposed to contain an App, which is my final purpose).

## Objectives

This document will explain how to setup a container (with X11 communications so that GUI dev is possible) & the steps for installing GTK3 & some of its related libraries from scratch.

## Prerequisites

- A minimal understanding of containers (beginner level), the needed reading material will be linked
- Some experience with Unix-like systems & their sources build system (configure, make, etc.)

## Important note

I'm basically a beginner in the use of Docker, so maybe I've missed some features that could be used. But this setup works.
