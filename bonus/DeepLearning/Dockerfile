FROM ubuntu

EXPOSE 8888 8888

RUN rm -rf /var/lib/apt/lists/*

ARG THEANO_VERSION=rel-0.8.2
ARG TENSORFLOW_VERSION=0.12.1
ARG TENSORFLOW_ARCH=cpu
ARG KERAS_VERSION=1.2.0
ARG LASAGNE_VERSION=v0.1
ARG TORCH_VERSION=latest
ARG CAFFE_VERSION=master

RUN apt-get -y update && \
	apt-get -y install \
		cmake \
		git \
		vim \
		wget \
		python-virtualenv \
		python-pip \
		python-dev \
		python3-pip \
		python3-dev

RUN apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/* 

RUN pip install --upgrade pip

RUN apt-get update && \
	apt-get -qq -y install curl && \
	curl https://bootstrap.pypa.io/3.3/get-pip.py && \
	python get-pip.py && \
	rm get-pip.py

RUN apt-get update && apt-get install -y \
		python-numpy \
		python-scipy \
		python-nose \
		python-h5py \
		python-pandas \
		python-sklearn \
		python-sympy \
	apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/*

RUN pip --no-cache-dir install --upgrade ipython && \
	pip --no-cache-dir install \
		Cython \
		ipykernel \
		jupyther \
		path.py \
		Pillow \
		pygments \
		six \
		sphinx \
		wheel \
		zmq \
		&& \
	python -m ipykernel.kernelspec

# RUN pip --no-cache-dir install \

RUN mkdir /tensorflow

WORKDIR /tensorflow

RUN virtualenv --system-site-packages venv && \
	virtualenv --system-site-packages -p python3 venv && \
	source /tensorflow/venv/bin/activate \
		/tensorflow/venev/bin/activate.csh && \
	. /tensorflow/venv/bin/activate.fish && \
	(venv)$ pip install --upgrade pip && \
	pip install --upgrade tensorflow && \
	(venv)$ python -c "import tensorflow as tf; print(tf.__version__)"