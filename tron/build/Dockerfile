FROM mcr.microsoft.com/java/jdk:8-zulu-ubuntu
ARG TRON_VERSION
ENV TRON_VERSION=$TRON_VERSION
RUN mkdir -p /app
RUN  apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y apt-transport-https ca-certificates git wget pkg-config && \
    apt-get clean
WORKDIR /app/
RUN cd /app && wget https://github.com/tronprotocol/java-tron/releases/download/GreatVoyage-$TRON_VERSION/FullNode.jar
COPY  ./main_net_config.conf /app/
