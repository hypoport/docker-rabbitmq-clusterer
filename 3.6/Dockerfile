FROM rabbitmq:3.6.3-management

ENV RABBITMQ_CLUSTERER_VERSION 3.6.x-667f92b0

ENV RABBITMQ_BOOT_MODULE rabbit_clusterer

ENV RABBITMQ_SERVER_ADDITIONAL_ERL_ARGS "-pa /plugins/rabbitmq_clusterer.ez/rabbitmq_clusterer-${RABBITMQ_CLUSTERER_VERSION}/ebin"

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates wget && rm -rf /var/lib/apt/lists/* \
    && wget -O /plugins/rabbitmq_clusterer.ez "https://www.rabbitmq.com/community-plugins/v3.6.x/rabbitmq_clusterer-${RABBITMQ_CLUSTERER_VERSION}.ez" \
    && rabbitmq-plugins enable rabbitmq_clusterer --offline \
    && rabbitmq-plugins enable rabbitmq_shovel rabbitmq_shovel_management \
    && apt-get purge -y --auto-remove ca-certificates wget
