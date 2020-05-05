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
