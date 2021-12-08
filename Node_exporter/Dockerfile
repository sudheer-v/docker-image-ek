FROM adoptopenjdk/openjdk11:x86_64-ubuntu-jdk-11.0.13_8
ENV VERSION="1.3.1"

RUN curl -L -o node_exporter-${VERSION}.linux-amd64.tar.gz \
 https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz \
 && tar -xzvf node_exporter-${VERSION}.linux-amd64.tar.gz \
 && rm node_exporter-${VERSION}.linux-amd64.tar.gz


RUN cp node_exporter-${VERSION}.linux-amd64/node_exporter /bin/node_exporter

EXPOSE      9100
USER        nobody
ENTRYPOINT  [ "/bin/node_exporter" ]
