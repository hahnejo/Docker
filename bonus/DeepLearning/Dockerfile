FROM ubuntu:14.04

RUN rm -rf /var/lib/apt/lists/*

RUN apt-get -y update && \
	apt-get -y install \
		cmake \
		git \
		vim \
		wget \
		python \
		python3 \
		python-virtualenv \
		python-pip \
		python-dev \
		python3-pip \
		python3-dev

RUN apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/* 

RUN pip install --upgrade pip && \
	pip3 install -vU setuptools && \
	pip3 install jupyter

RUN apt-get update && \
	apt-get -qq -y install curl

# this is to prevent asking for timezone. Otherwise, we get stuck.

ENV DEBIAN_FRONTEND noninteractive

RUN export DEBIAN_FRONTEND=noninteractive && \
	apt-get install -y tzdata && \
	ln -fs /usr/share/zoneinfo/America/Fremont /etc/localtime && \
	dpkg-reconfigure --frontend noninteractive tzdata \
		debconf

RUN apt-get update && apt-get install -y \
		python-numpy \
		python-pandas

RUN apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/*

# miniconda installation
RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh