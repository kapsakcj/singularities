# singularities
Singularity recipes for bioinformatics software.

This repo is __WORK IN PROGRESS__. Feel free to try the recipes/Singularity builds, but they are __not tested deeply and are in no way guaranteed to work. Proceed at your own risk__. 

It is somewhat modeled after https://github.com/StaPH-B/docker-builds , but with Singularity recipes instead.

Sysadmins for High Performance Cluster computers almost always favor Sinularity over Docker :) so I'm starting to learn the ways of Singularity.

## Available Singularity images
| Software | Version | Link |
| :--------: | :-------: | :--------: |
| SPAdes | 3.13.0 | http://cab.spbu.ru/software/spades/ |
| QUAST | 5.0.0 | https://github.com/ablab/quast |
| Lyve-SET | 1.1.4f | https://github.com/lskatz/lyve-SET |

These Singularity images can be built if you have Singularity installed and **have sudo/admin priveleges**
```
# build an image using a recipe (called Singularity in this example)
sudo singularity build my-new-singularity-image.simg /path/to/Singularity

# download the repo
git clone https://github.com/kapsakcj/singularities.git
# another example using the SPAdes recipe
sudo singularity build my-new-spades-3.13.0-image.simg /path/to/Singularity.spades.3.13.0
```

These Singularity images are also available to download from singularity-hub.org if you **don't have sudo priveleges** (no build necessary!). The badge below is a link to the singularity-hub.org collection.

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/2778)

The name of the Singularity hub collection is `kapsakcj/singularities` and the tag is specified by the extenion of the Singularity recipe file. For example the recipe, `/spades/3.13.0/Singularity.spades.3.13.0`, can be downloaded like so:
```
# download an image like so, and name it whatever you want with the --name flag
singularity pull --name my-new-spades-3.13.0-image shub://kapsakcj/singularities:spades.3.13.0
```

## Useful links and resources
- Singularity v2.6 User guide https://www.sylabs.io/guides/2.6/user-guide/index.html
- SingularityHub https://singularity-hub.org/
- Excellent tutorial on Singularity (using v2.5) from Sylabs, many other links within https://github.com/Singularity-tutorial/Singularity-tutorial.github.io
- How to build a container using Singularity Hub, linked to a github repo with Singularity recipes https://github.com/singularityhub/singularityhub.github.io/wiki/Build-A-Container

### Tips/Tricks/Things-to-remember about Singularity [ many from Jake Garfin :) ]
- Singularity automatically brings your user & group into the container with you (ie. no `-u $(id -u):$(id -g)` needed like in Docker)
- Singularity (by default) wants to mount your entire home directory inside the container as well. Use `--cleanenv` and `--containall` to keep things separate and bring in specific directories you want with `-B /local-dir:/dir-in-container`
- Docker images converted to Singularity that want to write to system directories owned by root aren't going to work out of the box.
- If you are making a container with something that uses perl, add this to the recipe in the `%environment` section to prevent locale settings errors (see lyveset recipe)
```
%environment
    export LC_ALL=C
```


TO-DO
- How to: Singularity
  - Links to docs for installing
  - How to download an image from singularity hub
  - How to download an image fromm dockerhub
    - `singularity pull docker://staphb/skesa`
  - How to take a recipe and build locally (sudo required)
  - How to run a Singularity container
    - Different ways to run - `singularity exec [...]` or ./name-of-singularity.simg [...]
    - Mounting DIRs - default way (mount entire `$HOME` DIR), or way to mount a specific DIR and not entire `$HOME` DIR
  
- Create SingularityHub account
  - link to this repo
  - create autobuilds for each recipe
