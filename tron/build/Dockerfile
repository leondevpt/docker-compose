FROM mcr.microsoft.com/java/jdk:8-zulu-ubuntu
ARG TRON_VERSION
ENV TRON_VERSION=$TRON_VERSION
ARG USERNAME=ubuntu
ARG USER_UID=1000
ARG USER_GID=$USER_UID
# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && mkdir -p /app   && chown -R $USER_UID:$USER_GID /app
RUN  apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y apt-transport-https ca-certificates git wget pkg-config && \
    apt-get clean
# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME
WORKDIR /app/
RUN cd /app && wget https://github.com/tronprotocol/java-tron/releases/download/GreatVoyage-$TRON_VERSION/FullNode.jar
# copy as none root
COPY --chown=$USER_UID:$USER_GID ./main_net_config.conf /app/
