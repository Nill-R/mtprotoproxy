# Async MTProto Proxy #

Fast and simple to setup MTProto proxy written in Python.

## Starting Up ##
    
1. `git clone https://github.com/Nill-R/mtprotoproxy.git; cd mtprotoproxy`
2. Edit *config.py*, set **PORT**, **USERS** and **AD_TAG**
3. Copy config for rsyslog, systemd-unit, fail2ban filter to directories for it. Create fail2ban jail and restart fail2ban.
4. `mkdir /etc/mtprotoproxypy/; cp config.py /etc/mtprotoproxypy/mtprotoproxypy.conf`
5. `cp mtprotoproxy.py /usr/local/bin/`
6. `mkdir /var/log/mtprotoproxypy/;chown syslog /var/log/mtprotoproxypy`
7. `systemctl daemon-reload; systemctl enable mtprotoproxypy; systemctl start mtprotoproxypy`
8. `tail /var/log/mtprotoproxy/mtprotoproxypy.log`

## Channel Advertising ##

To advertise a channel get a tag from **@MTProxybot** and put it to *config.py*.

## Performance ##

The proxy performance should be enough to comfortably serve about 4 000 simultaneous users on
the VDS instance with 1 CPU core and 1024MB RAM.

## Advanced Usage ##

The proxy can be launched:
- with a custom config: `python3 mtprotoproxy.py [configfile]`
- several times, clients will be automaticaly balanced between instances
- with uvloop module to get an extra speed boost
- with runtime statistics exported to [Prometheus](https://prometheus.io/)
