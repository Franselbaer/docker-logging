# Micro Syslog
FROM alpine:latest
MAINTAINER MTH <martin@treide.org>
RUN apk update && apk upgrade && \
	apk add rsyslog && \
	rm -rf /var/cache/apk/* && \
	mkdir -p /etc/rsyslog.d && \
	mkdir -p /data
ADD ./rsyslog_conf /etc/rsyslog.d/syslogserver.conf
EXPOSE 514/tcp 514/udp
ENTRYPOINT ["rsyslogd", "-n"]

