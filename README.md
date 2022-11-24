### Note
DNS to block ads

#### Installation
https://github.com/pi-hole/pi-hole/#one-step-automated-install

#### Blacklist and whitelist
More general whitelist: https://github.com/anudeepND/whitelist

##### Manual Whitelist
```
pihole -w click.linksynergy.com
```

##### Manual Blacklist
```
pihole -b click.linksynergy.com
```


#### Other public DNS
##### Adguard
###### Default
```
176.103.130.130
176.103.130.131
```

###### Family protection
```
176.103.130.132
176.103.130.134
```

##### Google
```
8.8.8.8
8.8.4.4
```

##### Cloudflare
###### Public DNS from Cloudflare
```
1.1.1.1
1.0.0.1
```

###### Malware Blocking Only from Cloudflare
```
1.1.1.2
1.0.0.2
```

###### Malware and Adult Contentfrom Cloudflare
```
1.1.1.3
1.0.0.3
```


##### DNS over HTTPS / TLS
```
dns.adguard.com
dns-family.adguard.com 
dns.google
one.one.one.one
```


##### DNS Test with nslookup
```
# bad host with ad
nslookup yieldmanager.com 1.1.1.1

# good host
nslookup google.com 1.1.1.1
```


##### Run with docker

```
touch etc-pihole etc-dnsmasq.d docker-compose.yml
```

```yml
version: "3"

# More info at https://github.com/pi-hole/docker-pi-hole/ and https://docs.pi-hole.net/
services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    # For DHCP it is recommended to remove these ports and instead add: network_mode: "host"
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp" # Only required if you are using Pi-hole as your DHCP server
      - "80:80/tcp"
    environment:
      TZ: 'America/Chicago'
      # WEBPASSWORD: 'set a secure password here or it will be random'
    # Volumes store your data between container upgrades
    volumes:
      - './etc-pihole:/etc/pihole'
      - './etc-dnsmasq.d:/etc/dnsmasq.d'
    #   https://github.com/pi-hole/docker-pi-hole#note-on-capabilities
    cap_add:
      - NET_ADMIN # Required if you are using Pi-hole as your DHCP server, else not needed
    restart: unless-stopped
```

```bash
docker-compose up
```

###### Change Password
```
docker exec -it 02638aea9b7a /bin/bash
# when connected, update the password with this command
pihole -a -p
```
