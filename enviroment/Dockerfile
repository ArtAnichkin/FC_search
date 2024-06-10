ARG UBUNTU_VER=22.04
ARG CONDA_VER=latest
ARG OS_TYPE=x86_64
ARG PY_VER=3.10
ARG PANDAS_VER=1.5.3

FROM nvcr.io/nvidia/cuda:12.2.0-devel-ubuntu22.04
# FROM ubuntu:${UBUNTU_VER}
# System packages 
RUN apt-get update && apt-get install -yq curl wget jq vim

ENV DEBIAN_FRONTEND noninteractive
RUN useradd -ms /bin/bash --uid 1000 jupyter\
&& apt update\
&& apt install -y python3.10-dev python3.10-distutils curl\
&& ln -s /usr/bin/python3.10 /usr/local/bin/python3\
&& curl https://bootstrap.pypa.io/get-pip.py | python3

# Use the above args 
#ARG CONDA_VER
#ARG OS_TYPE
# Install miniconda to /miniconda
#RUN curl -LO "http://repo.continuum.io/miniconda/Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh"
#RUN bash Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh -p /miniconda -b
#RUN rm Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh
#ENV PATH=/miniconda/bin:${PATH}
#RUN conda update -y conda
#RUN conda init

#RUN conda create --name env python=3.10

# Make RUN commands use the new environment:
#SHELL ["conda", "run", "--no-capture-output", "-n", "env", "/bin/bash", "-c"]


#ARG PY_VER
#ARG PANDAS_VER
# Install packages from conda 
#RUN conda config --add channels conda-forge
#RUN conda install xtb-python


RUN apt-get -y install git
RUN apt-get update && apt-get install -y gcc g++

RUN pip install numpy==1.25.2 scipy==1.11.4 pandas===1.5.3 matplotlib==3.7.1 seaborn==0.13.1 rdkit==2022.3.5 mordred==1.2.0 torch==2.2.1 

RUN pip install phik umap-learn shap boruta torch_geometric  pytorch-lightning torchmetrics
RUN pip install  torch_geometric  pytorch-lightning torchmetrics
RUN pip install xtb
RUN pip install phik umap-learn shap boruta
RUN apt-get install -y libxrender1