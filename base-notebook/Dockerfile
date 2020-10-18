ARG ROOT_CONTAINER=python:slim-buster@sha256:f2615c63a0aa41d635f69fedec0152ae76ba7b254b005c159245293eb707ad0c
ARG BASE_CONTAINER=$ROOT_CONTAINER
FROM $BASE_CONTAINER

LABEL maintainer="Lukas Weiß <info@l-weiss.de>"

WORKDIR /root

# upgrade the system and install relevant dependencies
RUN apt-get update \
 && apt-get upgrade -yq \
 && apt-get install -yq \
    gfortran \
    libopenblas-dev \
    ca-certificates \
    liblapack-dev \
    nano \
    build-essential \
    libssl-dev \
    libffi-dev \
    python-dev \
    git \
    inkscape \
    jed \
    libsm6 \
    libxext-dev \
    libxrender1 \
    lmodern \
     # ---- nbconvert dependencies ----
    texlive-xetex \
    texlive-fonts-recommended \
    texlive-plain-generic \
    # ----
    tzdata \
    ffmpeg \
    dvipng \
    cm-super \
    bzip2 \
    libjpeg62-turbo-dev \
    zlib1g-dev \
    fonts-liberation \
 && apt-get clean && rm -rf /var/lib/apt/lists/*

# upgrade pip
RUN pip install --upgrade pip setuptools wheel

# install jupyter
RUN pip install ipywidgets jupyter jupyterlab

# Configure jupyter
RUN jupyter nbextension enable --py widgetsnbextension
RUN jupyter serverextension enable --py jupyterlab
RUN jupyter notebook --generate-config
RUN mkdir notebooks
RUN sed -i "/c.NotebookApp.open_browser/c c.NotebookApp.open_browser = False" /root/.jupyter/jupyter_notebook_config.py \
        && sed -i "/c.NotebookApp.ip/c c.NotebookApp.ip = '*'" /root/.jupyter/jupyter_notebook_config.py \
        && sed -i "/c.NotebookApp.port/c c.NotebookApp.port = 8888" /root/.jupyter/jupyter_notebook_config.py \
        && sed -i "/c.NotebookApp.allow_password_change/c c.NotebookApp.allow_password_change = True" /root/.jupyter/jupyter_notebook_config.py \
        && sed -i "/c.NotebookApp.notebook_dir/c c.NotebookApp.notebook_dir = '/root/notebooks'" /root/.jupyter/jupyter_notebook_config.py

VOLUME /root/notebooks

EXPOSE 8888

CMD ["jupyter", "notebook", "--allow-root"]