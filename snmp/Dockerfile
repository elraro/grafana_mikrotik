ARG ARCH="amd64"
ARG OS="linux"
FROM quay.io/prometheus/busybox-${OS}-${ARCH}:latest
LABEL maintainer="The Prometheus Authors <prometheus-developers@googlegroups.com>"
LABEL Software="snmp_exporter prometheus for Mikrotik"
LABEL Author="IgorKha, elraro"

RUN wget https://github.com/prometheus/snmp_exporter/releases/download/v0.20.0/snmp_exporter-0.20.0.linux-amd64.tar.gz \
&& tar xfz snmp_exporter-0.20.0.linux-amd64.tar.gz --strip-components=2 -C . \
&& mv snmp_exporter /bin/snmp_exporter \
&& mv snmp.yml /etc/snmp_exporter/snmp.yml \
&& rm -y LICENSE \
&& rm -y NOTICE

EXPOSE      9116
ENTRYPOINT  [ "/bin/snmp_exporter" ]
CMD         [ "--config.file=/etc/snmp_exporter/snmp.yml" ]
