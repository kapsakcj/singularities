# singularities
Singularity recipes for bioinformatics software.

This repo is __WORK IN PROGRESS__. Feel free to try the recipes/Singularity builds, but they are __not tested deeply and are in no way guaranteed to work. Proceed at your own risk__. 

It is somewhat modeled after https://github.com/StaPH-B/docker-builds , but with Singularity recipes instead.

Sysadmins for High Performance Cluster computers almost always favor Sinularity over Docker :) so I'm starting to learn the ways of Singularity.

## Available Singularity images
| Software | Version | Link |
| :--------: | :-------: | :--------: |
| SPAdes | 3.13.0 | http://cab.spbu.ru/software/spades/ |

## Useful links and resources
- Singularity v2.5 User guide https://www.sylabs.io/guides/2.5/user-guide/index.html
- SingularityHub https://singularity-hub.org/
- Excellent tutorial on Singularity (using v2.5) from Sylabs, many other links within https://github.com/Singularity-tutorial/Singularity-tutorial.github.io

TO-DO
- How to: Singularity
  - Links to docs for installing
  - How to download an image from singularity hub
  - How to take a recipe and build locally (sudo required)
- Create SingularityHub account
  - link to this repo
  - create autobuilds for each recipe
