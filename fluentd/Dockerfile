FROM fluent/fluentd-kubernetes-daemonset:v1.9.2-debian-cloudwatch-1.0

USER root

ADD fluent-plugin-gcloud-pubsub-custom-0.4.6.gem fluent-plugin-gcloud-pubsub-custom-0.4.6.gem

RUN gem install fluent-plugin-gcloud-pubsub-custom-0.4.6.gem

ENV FLUENTD_CONF=fluent.conf

USER fluent

ENTRYPOINT ["tini" "--" "/fluentd/entrypoint.sh"]
