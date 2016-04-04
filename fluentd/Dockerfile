FROM fluent/fluentd:latest

MAINTAINER Jose Sanchez <jose@varcelona.com>

USER root

ENV PATH /home/ubuntu/ruby/bin:$PATH
RUN gem install fluent-plugin-elasticsearch

RUN apk --update-cache add rsyslog \
    && mkdir -p /etc/rsyslog.d/

COPY rsyslog.conf /etc/rsyslog.d/udp.conf

CMD rsyslogd && exec fluentd -c /fluentd/etc/$FLUENTD_CONF -p /fluentd/plugins $FLUENTD_OPT
