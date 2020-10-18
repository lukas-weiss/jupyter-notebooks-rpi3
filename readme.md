# Jupyter Notebooks RPi3

Providing the Dockerfiles so it is possible to run Jupyter Notebooks in a container environment on your RPi3/ARM32. The style of the Dockerfile is the same as Jupyter provide the original ones. They do not support ARM32 architecture with their images, so I decided to create my own.

## base notebook
Contains just basic depedencies for running jupyter notebooks without the data science stack. Based on  `python:slim-buster@sha256:f2615c63a0aa41d635f69fedec0152ae76ba7b254b005c159245293eb707ad0c` and prepared environment to install the data science stack manually.

### default configuration
* default notbooksdir `/root/notebooks`
* default port `8888`
* listen to ip addresses `*`
* running as user `root`

### Docker Hub
`lweiss89/jupyter-base-notebook`

**Status:** released

https://hub.docker.com/repository/docker/lweiss89/jupyter-base-notebook

## scipy-notebook
Contains the most relevant dependencies of the data science stack for running Jupyter Notebooks and is based on `base notebook`

### Installed dependencies
* scipy
* numpy
* pandas
* matplotlib
* scikit-learn

### Docker Hub
`lweiss89/jupyter-scipy-notebook`

**Status:** not released

## TODO's
* Build images on RPi3 and release them to `Docker Hub`
* Support Jupyter Lab (argument based)
* Edit user handling so that Jupyter is not running as root
* Specify dependency versions so it will be stable
