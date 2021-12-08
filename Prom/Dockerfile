FROM adoptopenjdk/openjdk11:x86_64-ubuntu-jdk-11.0.13_8

ENV VERSION="2.32.0-rc.0"

#RUN groupadd -g 1000 nobody && useradd nobody -u 1000 -g 1000

RUN curl -L -o prometheus-2.32.0-rc.0.linux-amd64.tar.gz https://github.com/prometheus/prometheus/releases/download/v${VERSION}/prometheus-${VERSION}.linux-amd64.tar.gz \
 && tar -xzvf prometheus-${VERSION}.linux-amd64.tar.gz \
 && rm prometheus-${VERSION}.linux-amd64.tar.gz

WORKDIR /prometheus-${VERSION}.linux-amd64

RUN mkdir /etc/prometheus && mkdir /usr/share/prometheus

RUN cp prometheus /bin/prometheus
RUN cp promtool /bin/promtool
RUN cp prometheus.yml /etc/prometheus/prometheus.yml
RUN cp -r console_libraries /usr/share/prometheus/
RUN cp -r consoles /usr/share/prometheus/


WORKDIR /prometheus
RUN ln -s /usr/share/prometheus/console_libraries /usr/share/prometheus/consoles/ /etc/prometheus/ && \
    chown -R nobody /etc/prometheus /prometheus

USER       nobody
EXPOSE     9090
VOLUME     [ "/prometheus" ]
ENTRYPOINT [ "/bin/prometheus" ]
CMD        [ "--config.file=/etc/prometheus/prometheus.yml", \
             "--storage.tsdb.path=/prometheus", \
             "--web.console.libraries=/usr/share/prometheus/console_libraries", \
             "--web.console.templates=/usr/share/prometheus/consoles" ]
