FROM harisekhon/ubuntu-java:jdk8

USER root

RUN groupadd -g 1000 filebeat && useradd filebeat -u 1000 -g 1000

COPY filebeat-oss-7.10.2-amd64.deb /opt/filebeat-oss-7.10.2-amd64.deb 

RUN apt-get install -y /opt/filebeat-oss-7.10.2-amd64.deb

COPY docker-entrypoint /usr/local/bin/docker-entrypoint

WORKDIR /usr/share/filebeat

ENV PATH=$PATH:/usr/share/filebeat/bin

RUN chmod 0775 /usr/local/bin/docker-entrypoint

USER filebeat

ENTRYPOINT ["/usr/local/bin/docker-entrypoint"]

CMD ["-environment" "container"]

