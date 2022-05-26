# katello-pull-transport-migrate

_katello-pull-transport-migrate_ is a script which can be run on a client to migrate from katello-agent to REX pull transport (formerly known as "pull provider.")

## What it does
* Gets configuration from `subscription-manager config --list`
* Writes correct configuration in `config.toml` based on subscription-manager config
* Enables pull transport daemon service (`yggdrasild`) on the client and displays status

After a successful run, it is safe to remove katello-agent from the client.

## Prerequisites

### Server
* Foreman version 3.3 or later
* foreman_remote_execution version 7.0 or later
* smart_proxy_remote_execution_ssh version 0.7.0 or later

Run `foreman-installer` with the following options:

```
foreman-installer \
  --enable-foreman-proxy-plugin-remote-execution-script \
  --foreman-proxy-plugin-remote-execution-script-mode pull-mqtt
```

### Client
* `katello-pull-transport-migrate` RPM installed (this will install the two dependencies, `yggdrasil` and `foreman_ygg_worker`)
* Registered to Katello (script will exit if client is registered directly to RHSM)

## Run

```sh
./katello-pull-transport-migrate
```

## Contribute

Please, open your PR and join our [community](https://theforeman.org/contribute.html)!

Issues tracked via [Redmine](https://projects.theforeman.org/projects/foreman_remote_execution).