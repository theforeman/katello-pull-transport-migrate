# katello-pull-transport-migrate

_katello-pull-transport-migrate_ is a script which can be run on a client to migrate from katello-agent to REX pull transport (formerly known as "pull provider.")

## What it does
* Gets configuration from `subscription-manager config --list`
* Writes correct configuration in config.toml based on subscription-manager config
* Enables pull transport daemon service (yggdrasild) on the client and displays status

After a successful run, it is safe to remove katello-agent from the client.

## Prerequisites

### Server
(the following soon to be done for you by foreman-installer)

* Message broker such as `mosquitto` running
* smart_proxy_remote_execution_ssh configured as follows
```
# /etc/foreman-proxy/settings.d/remote_execution_ssh.yml
:mqtt_broker: localhost
:mqtt_port: 1883
:mode: pull-mqtt
```

### Client
* `yggdrasil` and `foreman_ygg_worker` RPMs installed
* Registered to Katello (script will exit if client is registered directly to RHSM)

## Run

```
# set $SBINDIR if it's other than /usr/sbin
./katello-pull-transport-migrate
```

## Contribute

Please, open your PR and join our [community](https://theforeman.org/contribute.html)!

Issues tracked via [Redmine](https://projects.theforeman.org/projects/foreman_remote_execution).