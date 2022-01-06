FROM harisekhon/ubuntu-java:jdk8

USER root

RUN groupadd -g 1000 logstash && useradd logstash -u 1000 -g 1000

COPY logstash-oss-7.10.2-amd64.deb /opt/logstash-oss-7.10.2-amd64.deb

RUN apt-get install -y /opt/logstash-oss-7.10.2-amd64.deb

COPY logstash-input-google_pubsub-1.2.1.gem /opt/logstash-input-google_pubsub-1.2.1.gem

COPY docker-entrypoint /usr/local/bin/docker-entrypoint

WORKDIR /usr/share/logstash

ENV PATH=$PATH:/usr/share/logstash/bin

RUN /usr/share/logstash/bin/logstash-plugin install /opt/logstash-input-google_pubsub-1.2.1.gem

RUN chmod 0775 /usr/local/bin/docker-entrypoint

USER logstash

EXPOSE 5044 9600

ENTRYPOINT ["/usr/local/bin/docker-entrypoint"]


