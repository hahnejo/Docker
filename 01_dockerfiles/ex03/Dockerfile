FROM ubuntu

EXPOSE 3000 90

# some necessary packages

RUN apt-get update -yq && apt-get install -yq --no-install-recommends \
	postfix

# RUN dpkg-reconfigure postfix

RUN apt-get install -yq \
		build-essential \
		curl \
		ca-certificates \
		openssh-server

WORKDIR /

RUN curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
CMD ["bash", "script.deb.sh"]
RUN apt-get install -yq gitlab-ce

# RUN mkdir /etc/init
# RUN initctl start gitlab-runsvdir
# RUN initctl start gitlab-runsvdir.service

RUN apt-get update -yq && \
	# echo "Europe/Dublin" > /etc/timezone && \
	# dpkg-reconfigure -f noninteractive tzdata && \
	export DEBIAN_FRONTEND=noninteractive DEBCONF_NONINTERACTIVE_SEEN=true && \
	apt-get install -yq tzdata && \
	apt-get clean && rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

RUN touch /entrypoint.sh && \
	chmod 755 entrypoint.sh && \
	echo "/opt/gitlab/embedded/bin/runsvdir-start&\nexport EXTERNAL_URL ="localhost"\ngitlab-ctl reconfigure\ngitlab-ctl start\ntail -f /dev/null" > entrypoint.sh

RUN bash entrypoint.sh

# https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/common_installation_problems/README.md#reconfigure-freezes-at-ruby_blocksupervise_redis_sleep-action-run

# RUN gitlab-ctl reconfigure

# docker run -it --rm -p 90:90 -p 3000:3000 -p 90:90 ex03