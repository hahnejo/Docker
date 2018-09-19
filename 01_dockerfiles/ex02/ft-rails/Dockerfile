FROM ruby:2.5
RUN apt-get update -q && \
	apt-get install -y build-essential libpq-dev nodejs && \
	mkdir /opt/app && \
	gem install rails bundler
ONBUILD WORKDIR /opt
ONBUILD RUN rails new app
ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install
ONBUILD RUN rails generate migration CreateProducts name:string
ONBUILD RUN rake db:migrate
