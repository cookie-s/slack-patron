FROM ruby:2.4-alpine
MAINTAINER tyage <namatyage@gmail.com>

ARG SRCDIR="/usr/local/slack-patron"

RUN set -x && \
	apk upgrade --update && \
	apk add --update \
		git \
		build-base \
		openssl \
		openssl-dev && \
	echo 'gem: --no-document' >> /etc/gemrc

ADD . ${SRCDIR}

RUN cd ${SRCDIR} && \
	bundle install

COPY ./config.yml ${SRCDIR}/config.yml
WORKDIR ${SRCDIR}

CMD bundle exec ruby logger/logger.rb
