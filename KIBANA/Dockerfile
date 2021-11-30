FROM harisekhon/ubuntu-java:jdk8

USER root

RUN groupadd -g 1000 kibana && useradd kibana -u 1000 -g 1000

COPY kibana-oss-7.10.2-amd64.deb /opt/

RUN apt-get install -y /opt/kibana-oss-7.10.2-amd64.deb

COPY kibana.yml /etc/kibana/

WORKDIR /usr/share/kibana

COPY kibana-docker /usr/local/bin/kibana-docker

RUN chmod 0775 /usr/local/bin/kibana-docker

RUN chown -R kibana:kibana /etc/default/kibana

RUN chown -R kibana:kibana /usr/share/kibana

RUN chown -R kibana:kibana /etc/kibana

RUN ln -s /etc/kibana /usr/share/kibana/config

EXPOSE 5601

ENV PATH=$PATH:/usr/share/kibna/bin

USER 1000

CMD ["/usr/local/bin/kibana-docker"]
