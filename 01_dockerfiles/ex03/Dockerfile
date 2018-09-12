FROM ubuntu
RUN apt-get update && apt-get -y install curl \
	ca-certificates \
	openssh-server \
	postfix

WORKDIR /

RUN curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
RUN bash script.deb.sh
RUN apt-get update && EXTERNAL_URL="http://gitlab.example.com" && \
	apt-get install -yq gitlab-ce && \
	apt update && apt install -y tzdata && \
	apt-get clean && rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

EXPOSE 3000 90

RUN echo "/opt/gitlab/embedded/bin/runsvdir-start&\nEXTERNAL_URL="localhost" && gitlab-ctl reconfigure\ngitlab-cntl start\ntail -f /dev/null" > /entrypoint.sh

RUN chmod 755 entrypoint.sh
CMD ["bash", "entrypoint.sh"]

# docker run -it --rm -p 90:90 -p 3000:3000 hjo/ex03