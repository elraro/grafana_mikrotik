ARG ARCH="amd64"
ARG OS="linux"
FROM quay.io/prometheus/busybox-${OS}-${ARCH}:latest
LABEL maintainer="The Prometheus Authors <prometheus-developers@googlegroups.com>"
LABEL Software="snmp_exporter prometheus for Mikrotik"
LABEL Author="IgorKha, elraro"

RUN wget https://github.com/prometheus/snmp_exporter/releases/download/v0.20.0/snmp_exporter-0.20.0.linux-amd64.tar.gz \
&& tar xfz snmp_exporter-0.20.0.linux-amd64.tar.gz --strip-components=1 -C . \
&& mv snmp_exporter /bin/snmp_exporter \
&& mkdir /etc/snmp_exporter \
&& rm snmp.yml \
&& rm LICENSE \
&& rm NOTICE \
&& rm snmp_exporter-0.20.0.linux-amd64.tar.gz

COPY /snmp/snmp.yml /etc/snmp_exporter/snmp.yml

EXPOSE      9116
ENTRYPOINT  [ "/bin/snmp_exporter" ]
CMD         [ "--config.file=/etc/snmp_exporter/snmp.yml" ]
