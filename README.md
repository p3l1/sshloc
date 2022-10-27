# EndleSSH to ELK Stack

This project is based on the [docker-elk](https://github.com/deviantony/docker-elk) template from deviantony.

## Features

The given [`docker-compose.yml`](docker-compose.yml) was extended to expose the [endlessh](https://github.com/skeeto/endlessh) service to provide an SSH honeypot on port 2222.
Endlessh's log output is sent to logstash by using a shared Docker volume. The log is then transformed using [GROK](logstash/pipeline/logstash.conf) patterns and sent to elasticsearch.

## Motivation

I run multiple servers for a variety of services, directly connected to the internet. In this kind of scenario the `/var/log/auth.log` file is pretty much flooded with failed SSH authentication attempts. To slow down attackers and to gather some information about them I wanted to monitor all incoming authentication attempts. So I moved the real SSH service to another port and deployed endlessh on port 22.
To store and evaluate the collected data I chose the ELK stack, to learn how to work with it.

## License

[MIT](LICENSE)
