# Micro Syslog
FROM alpine:latest
MAINTAINER MTH <martin@treide.org>
RUN apk update && apk upgrade && \
	apk add logrotate bash && \
	rm -rf /var/cache/apk/* && \
	mkdir -p /data
ADD ./logrotate_conf /etc/logrotate.conf
ADD ./start_sh /start.sh
ENTRYPOINT ["/start.sh"]

