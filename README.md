# Fully automatic rsyslogd for collecting remote logs
## Brief
This is just a simple rsyslogd to collect syslog from several hosts where ELK stack is way to much
## Build and start instructions
You need docker and docker-compose on your host. Just do a:

``` 
docker-compose build --no-cache
docker-compose up -d
```

It'll open rsyslog on standart ports (514/tcp/udp) and save data in 
`./containerdata/syslog/($HOSTNAME/$IP)/$YEAR/%MONTH`
on the host system. It has a logrotate for the days.

### Additional build notes
Everytime you do a `docker-compose build --no-cache` you get a fresh alpine:latest with an `apk update` and `apk upgrade` before daemons get installed. So you have latest version and latest patches in the container. ./containerdata/syslog is persistent so you don't need to take care about loosing your data. So i recommend to setup a cronjob who builds the stuff weekly and do a `docker-compose up -d` to restart with new updates.

### Additional autostart notes
On systems having problems to autostart Docker containers just do a cron for it. E.g.
`@reboot	(cd /where my composefile/is; docker-compose up -d)`
Do not care about fixing race conditions in Ubuntu systemd stuff or upstart problems or or or... It's not worth.


