FROM adoptopenjdk/openjdk11:x86_64-ubuntu-jdk-11.0.13_8

ENV VERSION="0.23.0"

RUN curl -L -o alertmanager-${VERSION}.linux-amd64.tar.gz https://github.com/prometheus/alertmanager/releases/download/v${VERSION}/alertmanager-${VERSION}.linux-amd64.tar.gz \
 && tar -xzvf alertmanager-${VERSION}.linux-amd64.tar.gz \
 && rm alertmanager-${VERSION}.linux-amd64.tar.gz

WORKDIR /alertmanager-${VERSION}.linux-amd64

RUN mkdir /etc/alertmanager 

RUN cp alertmanager /bin/alertmanager
RUN cp amtool /bin/amtool
RUN cp alertmanager.yml /etc/alertmanager/alertmanager.yml



WORKDIR /alertmanager
RUN chown -R nobody /etc/alertmanager /alertmanager

USER       nobody
EXPOSE     9093
VOLUME     [ "/alertmanager" ]
ENTRYPOINT [ "/bin/alertmanager" ]
CMD        [ "--config.file=/etc/alertmanager/alertmanager.yml" "--storage.path=/alertmanager" ]
