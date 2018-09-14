FROM ubuntu:14.04

RUN mkdir /VPN

WORKDIR /VPN

RUN apt-get -y update && apt-get -y install \
        curl

RUN curl -L https://get.docker.com/gpg . | sudo apt-key add - && \
    echo deb http://get.docker.io/ubuntu docker main | sudo tee /etc/apt/sources.list.d/docker.list

RUN curl -sSL 'https://get.docker.com/ubuntu/pool/main/l/lxc-docker-1.7.0/lxc-docker-1.7.0_1.7.0_amd64.deb' .

RUN echo $USER

RUN usermod -l docker $USER

# https://www.digitalocean.com/community/tutorials/how-to-run-openvpn-in-a-docker-container-on-ubuntu-14-04