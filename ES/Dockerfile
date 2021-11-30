FROM adoptopenjdk/openjdk11:x86_64-ubuntu-jdk-11.0.13_8

USER root

RUN groupadd -g 1000 elasticsearch && useradd elasticsearch -u 1000 -g 1000

WORKDIR /etc/elasticsearch

COPY elasticsearch-oss-7.10.2-amd64.deb /opt/

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh

RUN chmod 0775 /usr/local/bin/docker-entrypoint.sh

RUN apt-get install /opt/elasticsearch-oss-7.10.2-amd64.deb

RUN set -ex && for path in data logs config config/scripts; do \
        mkdir -p "$path"; \
        chown -R elasticsearch:elasticsearch "$path"; \
    done
RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch

RUN chown -R elasticsearch:elasticsearch /etc/default/elasticsearch

RUN chown -R elasticsearch:elasticsearch /etc/elasticsearch

COPY logging.yml /etc/elasticsearch/

COPY elasticsearch.yml /etc/elasticsearch/

ENV PATH=$PATH:/usr/share/elasticsearch/bin

ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]

CMD ["eswrapper"] 

EXPOSE 9200 9300
