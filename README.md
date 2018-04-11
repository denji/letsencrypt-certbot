# Let's Encrypt Certbot container

[![](https://images.microbadger.com/badges/version/denji/letsencrypt-certbot.svg)](https://microbadger.com/images/denji/letsencrypt-certbot)

### Docker image

[![](https://images.microbadger.com/badges/image/denji/letsencrypt-certbot.svg)](https://microbadger.com/images/denji/letsencrypt-certbot) [![](https://img.shields.io/docker/automated/denji/letsencrypt-certbot.svg)](https://hub.docker.com/r/denji/letsencrypt-certbot/builds/) [![](https://img.shields.io/docker/pulls/denji/letsencrypt-certbot.svg)](https://hub.docker.com/r/denji/letsencrypt-certbot/) [![](https://img.shields.io/docker/stars/denji/letsencrypt-certbot.svg)](https://hub.docker.com/r/denji/letsencrypt-certbot/)

## Usage

### Set up a Certbot container

See example compose file at [`/alpine/docker-compose.yml`](/alpine/docker-compose.yml).

    docker-compose up -d; docker-compose logs

### Register new domain

```sh
docker exec -it example_certbot_1 \
    certbot \
    certonly \
    --standalone \
    --text \
    --email email@example.com \
    --agree-tos \
    --standalone-supported-challenges http-01 \
    --domains example.com
```

Explanation:

```sh
docker exec -it example_certbot_1             # enter composed container
    certbot                                   # run `certbot`
    certonly                                  # we write our own configs
    --standalone                              # auth method
    --text                                    # disable ncurses interface
    --email email@example.com                 # this is usually req'd
    --agree-tos                               # this is always req'd
    --standalone-supported-challenges http-01 # disable :443 check
    --domains example.com                     # the domain we are reg'ing
```
