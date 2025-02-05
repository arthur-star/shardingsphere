+++
title = "Proxy Startup"
weight = 1
+++

## Startup Steps

1. Download the latest version of ShardingSphere-Proxy.
1. If users use docker, they can execute `docker pull shardingsphere/shardingsphere-proxy` to get the image. Please refer to [Docker Image](/en/user-manual/shardingsphere-proxy/docker/) for more details.
1. After the decompression, revise `conf/server.yaml` and documents begin with `config-` prefix, `conf/config-xxx.yaml` for example, to configure sharding rules and replica query rules. Please refer to [Configuration Manual](/en/user-manual/shardingsphere-proxy/configuration/) for the configuration method.
1. Please run `bin/start.sh` for Linux operating system; run `bin/start.bat` for Windows operating system to start ShardingSphere-Proxy. To configure start port and document location, please refer to [Quick Start](/en/quick-start/shardingsphere-proxy-quick-start/).

## Using PostgreSQL

1. Use any PostgreSQL client end to connect, such as `psql -U root -h 127.0.0.1 -p 3307`.

## Using MySQL/openGauss

1. Copy MySQL/openGauss's JDBC driver to folder `ext-lib/`.
1. Use any MySQL/openGauss client end to connect, such as `mysql -u root -h 127.0.0.1 -P 3307` or `gsql`.

## Using user-defined sharding algorithm

When developer need to use user-defined sharding algorithm, it can not configure via inline expression in YAML file simply, should use the way below to configure sharding algorithm. 

1. Implement `ShardingAlgorithm` interface.
1. Package Java file to jar.
1. Copy jar to ShardingSphere-Proxy's `ext-lib/` folder.
1. Configure user-defined Java class into YAML file. Please refer to [Configuration Manual](/en/user-manual/shardingsphere-proxy/configuration/) for more details.

## Notices

1. ShardingSphere-Proxy uses 3307 port in default. Users can start the script parameter as the start port number, like `bin/start.sh 3308`.
1. ShardingSphere-Proxy uses `conf/server.yaml` to configure the registry center, authentication information and public properties.
1. ShardingSphere-Proxy supports multi-logic data source, with each yaml configuration document named by `config-` prefix as a logic data source.
