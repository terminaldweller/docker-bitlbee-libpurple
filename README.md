# docker-bitlbee-libpurple

This repo is a [fork](https://github.com/ezkrg/docker-bitlbee-libpurple)

**__NOTE__**: the alpine image unmaintained.

This docker image includes bitlbee-libpurple with a bunch of useful plugins:

- [facebook](https://github.com/jgeboski/bitlbee-facebook)
- [steam](https://github.com/jgeboski/bitlbee-steam)
- telegram via [tdlib-purple](https://github.com/BenWiederhake/tdlib-purple/)
- hangouts via [purple-hangouts](https://bitbucket.org/EionRobb/purple-hangouts)
- slack via dylex's fork of [slack-libpurple](https://github.com/dylex/slack-libpurple)
- [sipe](https://github.com/tieto/sipe)
- discord via [purple-discord](https://github.com/EionRobb/purple-discord)
- rocket.chat via [purple-rocketchat](https://bitbucket.org/EionRobb/purple-rocketchat)
- [mastodon](https://github.com/kensanata/bitlbee-mastodon)
- signal via [purple-presage](https://github.com/hoehermann/purple-presage)
- icyque via [icyque](https://github.com/EionRobb/icyque)
- whatsapp via [purple-gowhatsmeow](https://github.com/hoehermann/purple-gowhatsapp.git)
- microsoft teams via [purple-teams](https://github.com/EionRobb/purple-teams)

## Building and Running

```bash
docker build -t bitlbee-purple .
```

```bash
docker run -p 6667:6667 --name bitlbee -v /local/path/to/configurations:/var/lib/bitlbee --restart=always --detach bitlbee-purple
```
