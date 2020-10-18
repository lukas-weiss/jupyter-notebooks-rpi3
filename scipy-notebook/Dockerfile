ARG BASE_CONTAINER=lweiss89/jupyter-base-notebook:latest
FROM $BASE_CONTAINER

LABEL maintainer="Lukas Weiß <info@l-weiss.de>"

# upgrade the system and install relevant dependencies
RUN apt-get update && apt-get upgrade -yq

 # upgrade pip
RUN pip install --upgrade pip setuptools wheel

RUN pip install -U numpy matplotlib pandas scipy scikit-learn