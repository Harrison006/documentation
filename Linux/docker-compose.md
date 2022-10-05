# Normal Use
Generall common knowledge of compose is to 
```
# This force recreates any existing containers
Docker Compose up -d --force-recreate
```
Store all configs on network storage

Never store anything local besides the compose file

e.g nfs share

# Example Docker compose file

```yml
version: "2.1"
services:
  quassel-core:
    image: lscr.io/linuxserver/quassel-core:latest
    container_name: quassel-core
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Australia/Brisbane
      - RUN_OPTS=--config-from-environment #optional
    volumes:
      - /mnt/nas/irc:/config
      - /path/to/config:/config
    ports:
      - 4242:4242
      - 11304:10113 #optional
    restart: unless-stopped
```
The Name of these files are
```
docker-compose.yml
```