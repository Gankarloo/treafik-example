# Basic docker-compose example with traefik

## steps

Create docker network  
docker network create proxy  

* start treafik
  cd traefik && docker-compose up -d  

* Now do the same for the rest of the applications  



## dns

This setup requires you to setup your hosts file accordingly.  

a good tip is to install dnsmasq.  
This setup works for fedore 34 and has dnsmasq only for wildcard lookups

### /etc/dnsmasq.conf

no-resolv  
no-poll  
address=/.docker/127.0.0.1  
user=dnsmasq  
group=dnsmasq  
interface=lo  
listen-address=127.0.0.2  
no-dhcp-interface=127.0.0.2  
bind-interfaces  
no-hosts  

### /etc/systemd/resolved.conf

[Resolve]  
DNS=127.0.0.2  

### restart services

systemctl restart dnsmasq.service  
systemctl restart systemd-resolved  
