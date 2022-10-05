# Running Unifi Controller Baremetal vs Docker

## Docker
Running The unifi controller in a small deployment would be just best to use docker if your not looking at using large quantities of the unifi devices maybe 10-20 max

### Using Linuxserver.io image 
```yml
version: "2.1"
services:
  unifi-controller:
    image: lscr.io/linuxserver/unifi-controller:latest
    container_name: unifi-controller
    environment:
      - PUID=1000
      - PGID=1000
      - MEM_LIMIT=1024 #optional
      - MEM_STARTUP=1024 #optional
    volumes:
      - /unifi:/config
    ports:
      - 8443:8443
      - 3478:3478/udp
      - 10001:10001/udp
      - 8080:8080
      - 1900:1900/udp #optional
      - 8843:8843 #optional
      - 8880:8880 #optional
      - 6789:6789 #optional
      - 5514:5514/udp #optional
    restart: unless-stopped
```

## Baremetal

Running the unifi controller bare-metal is alot more simple and has more access to the hardware compared to the docker deployement

Runnion on your own hardware means though that you would need to dedicate a VM or a machine to this

**THIS IS SUBJECT TO CHANGE DEPENDING ON VERSIONS**
```bash
curl https://fw-download.ubnt.com/data/unifi-controller/7fe4-debian-7.2.94-60da5d445e0f47779a6d635724185886.deb
# SUBJECT TO CHANGE
sudo dpkg -i 7fe4-debian-7.2.94-60da5d445e0f47779a6d635724185886.deb
```
