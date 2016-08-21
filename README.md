# shinken-pack-collectd-mongodb

## Description

This Shinken monitoring pack is used to manage mongodb services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-mongodb: Manage all default thresholds and values for services

### Services

| Service name              | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|---------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| MongoDB - $KEY$ processes | Check MongoDB processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _mongodb_processes         |
| MongoDB - $KEY$           | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _mongodb_listen            |

## Default values

    _mongodb_processes                          mongod $(mongod)$$(1:1)$$(1:1)$
    _mongodb_listen                             mongod listen 27017 $(27017)$$(1:1)$$(1:1)$
