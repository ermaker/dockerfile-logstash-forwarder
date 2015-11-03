# Logstash-forwarder

# Getting Started

# Usage

```shell
DOMAIN=YOUR.DOMAIN.COM
CWD=$(pwd $(dirname $0))
CONF=${CWD}/lf.conf.d

openssl req \
  -x509 \
  -batch \
  -nodes \
  -newkey rsa:2048 \
  -days 3650 \
  -keyout ${CONF}/lf.key \
  -out ${CONF}/lf.crt \
  -subj /CN=${DOMAIN}
```

```shell
CWD=$(pwd $(dirname $0))
CONF=${CWD}/lf.conf.d
LOG=${CWD}/log

docker create \
  --name lf \
  -v ${CONF}:/opt/conf.d:ro \
  -v ${LOG}:/opt/log:ro \
  --restart=on-failure:5 \
  lf
```
