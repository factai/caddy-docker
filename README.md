# caddy

A [Docker](http://docker.com) image for [Caddy](http://caddyserver.com). This image includes the [cors](http://caddyserver.com/docs/http.cors) and [expires](http://caddyserver.com/docs/http.expires) plugin.

Fork from [abiosoft/caddy-docker](https://github.com/abiosoft/caddy-docker). Thanks for the great work :)

[abiosoft/caddy:builder](https://github.com/abiosoft/caddy-docker/blob/master/BUILDER.md) is used to build Caddy from binaries.

## Docker Documentation
For more details please refer to the repository forked from. Note that there is no PHP-version and git-plugin implemented in this fork.

### Docker-Compose example
Example config for a `docker-compose.yml`:
```yml
version: '2'

volumes:
  caddy_cert: {}

services:
  web:
    image: factai/alpine-caddy
    environment:
      - ACME_AGREE=true
    ports:
      # Caddy needs both ports (http, https) for automatic certificate retrieval
      - "443:443"
      - "80:80"
    volumes:
      - ./Caddyfile:/etc/Caddyfile
      # persist obtained certificates between restarts
      - caddy_cert:/root/.caddy
```