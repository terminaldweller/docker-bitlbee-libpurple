# docker-bitlbee-libpurple

This repo is a [fork](https://github.com/ezkrg/docker-bitlbee-libpurple)

**NOTE**: the alpine image is currently unmaintained.

The images are built and pushed to [dockerhub](https://hub.docker.com/r/terminaldweller/bitlbee_purple) automatically via github actions.

This docker image includes bitlbee-libpurple with a bunch of useful plugins:

- telegram via [tdlib-purple](https://github.com/BenWiederhake/tdlib-purple/)
- hangouts via [purple-hangouts](https://bitbucket.org/EionRobb/purple-hangouts)
- slack via dylex's fork of [slack-libpurple](https://github.com/dylex/slack-libpurple)
- discord via [purple-discord](https://github.com/EionRobb/purple-discord)
- rocket.chat via [purple-rocketchat](https://bitbucket.org/EionRobb/purple-rocketchat)
- mastodon via [bitlbee-mastodon](https://github.com/kensanata/bitlbee-mastodon)
- signal via [purple-presage](https://github.com/hoehermann/purple-presage)
- whatsapp via [purple-gowhatsmeow](https://github.com/hoehermann/purple-gowhatsapp.git)
- microsoft teams via [purple-teams](https://github.com/EionRobb/purple-teams)
- icyque via [icyque](https://github.com/EionRobb/icyque)
- [facebook](https://github.com/jgeboski/bitlbee-facebook)
- [steam](https://github.com/jgeboski/bitlbee-steam)
- [sipe](https://github.com/tieto/sipe)

for mattermost, use [matterircd](https://github.com/42wim/matterircd)

for matrix, use [matrix2051](https://github.com/progval/matrix2051)

## Building and Running

```bash
docker build -t bitlbee-purple .
```

```bash
docker run -p 6667:6667 --name bitlbee -v /local/path/to/configurations:/var/lib/bitlbee --restart=always --detach bitlbee-purple
```

An example compose file:

```yaml
services:
  bitlbee:
    image: bitlbee-purple
    deploy:
      resources:
        limits:
          memory: 384M
    logging:
      driver: "json-file"
      options:
        max-size: "100m"
    networks:
      - bitlbeenet
    ports:
      - "127.0.0.1:8667:6667"
      - "172.17.0.1:8667:6667"
    restart: unless-stopped
    user: "bitlbee:bitlbee"
    command:
      [
        "/usr/sbin/bitlbee",
        "-F",
        "-n",
        "-u",
        "bitlbee",
        "-c",
        "/var/lib/bitlbee/bitlbee.conf",
        "-d",
        "/var/lib/bitlbee",
      ]
    volumes:
      - ./conf/bitlbee.conf:/var/lib/bitlbee/bitlbee.conf:ro
      - userdata:/var/lib/bitlbee
networks:
  bitlbeenet:
volumes:
  userdata:
```
