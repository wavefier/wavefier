---
layout: page
title: User manual
subtitle: How to set up Wavefier from scratch
---

Due to its modular architecture based on containers, to set up the Wavefier framework all the containers have to be up and running. When changes are pushed to one of the project's repositories, continuous integration automatically triggers the build and release of the updated docker container, which is stored via GitHub Packages' [Container Registry](https://ghcr.io). 

# Running Wavefier on your local machine
To set up Wavefier on your local machine, you should clone the [docker-images](https://github.com/wavefier/docker-images) repository and run the command:

`docker-compose up`

This command will build, (re)create, start and link the containers for the project following the configuration in the *docker-compose.yml* file. 

# Running Wavefier at CNAF Tier 1
This section is being updated. Stay Tuned.
