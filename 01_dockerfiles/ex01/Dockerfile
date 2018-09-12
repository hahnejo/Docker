# start debian
FROM debian

# hook up the port number
EXPOSE 9987/udp 30033 10011

# install bzip2 so that we can untar the teamspeak server client
RUN apt-get update -y && \
	apt-get install --assume-yes apt-utils && \
	apt-get install bzip2 wget -y && \
	wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2 && \
	tar jxf teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2 && \
	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# cd into where the teamspeak is installed
WORKDIR teamspeak3-server_linux_amd64

# execute the script
CMD ["sh", "ts3server_minimal_runscript.sh"]