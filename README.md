# Nanopub Jupyter Lab Extension

![Github Actions Status](https://github.com/fair-workflows/NanopubJL/workflows/Build/badge.svg)

A Jupyterlab extension for searching and publishing Nanopublications from a python notebook.

This extension is composed of a Python package named `NanopubJL`
for the server extension and a NPM package named `NanopubJL`
for the frontend extension.

## Docker setup
It is possible to run the project inside a docker container. Simply run the following command in the project directory:

```shell script
docker-compose up
```

## Install the extension in your Docker image

You can install the NanopubJL extension directly in your own JupyterLab Docker image. 

Add the following lines to your `Dockerfile`:

```dockerfile
RUN pip install git+git://github.com/fair-workflows/FAIRWorkbench@add_nanopub_search_things_grlc
RUN pip install git+git://github.com/fair-workflows/NanopubJL@master
RUN git clone https://github.com/fair-workflows/NanopubJL /root/NanopubJL
WORKDIR /root/NanopubJL
RUN jupyter-serverextension enable --py NanopubJL && \
    jlpm && jlpm build && jupyter-labextension link . && jlpm build && jupyter-lab build
```

## Requirements

* JupyterLab >= 2.0
