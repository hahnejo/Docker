FROM ubuntu:14.04

RUN mkdir /crypto

WORKDIR /crypto

RUN apt-get -y update && \
	apt-get -y install \
        python \
        python3 \
        vim \
        git

RUN echo "import hashlib as hasher\nimport datetime as date" > crypto.py

RUN apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/*