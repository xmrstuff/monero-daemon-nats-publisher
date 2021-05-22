## monero-daemon-nats-publisher

Builds a Docker image with Monero Daemon set up to publish Monero Blocks to a NATS Streaming server, using the `--block-notify` param to invoke a CLI util (https://github.com/xmrstuff/monero-nats-publisher)

The image is built and published to https://hub.docker.com/repository/docker/xmrstuff/monero-daemon-nats-publisher

### Configuration

The `CMD` included in the Dockerfile is an example that uses the default configuration of the CLI util. You'd need to overwrite the `CMD` to pass custom configuration. Something like:

```bash
/usr/bin/publisher ping && \
/usr/bin/monerod \
    --non-interactive \
    --block-notiy="/usr/bin/publisher --nats-url=my-nats-server:4222 block %s"
```

See the README in the CLI's repo (https://github.com/xmrstuff/monero-nats-publisher) for more info 
