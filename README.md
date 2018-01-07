# Fully automatic rsyslogd for collecting remote logs
## Brief
This is just a simple rsyslogd to collect syslog from several hosts where ELK stack is way to much
## Build and start instructions
You need docker and docker-compose on your host. Just do a:
* docker-compose build --no-cache
* docker-compose up -d
It'll open rsyslog on standart ports (514/tcp/udp) and save data in ./containerdata/syslog/($HOSTNAME/$IP)/$YEAR/%MONTH
and it has a logrotate for the days.
