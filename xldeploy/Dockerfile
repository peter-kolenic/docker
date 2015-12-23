FROM debian:8.2

MAINTAINER Fai Fung <ffung@xebia.com>

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y openjdk-7-jre-headless unzip wget --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

ENV version 5.1.3
RUN wget -q https://dist.xebialabs.com/public/trial/xl-deploy/xl-deploy-${version}-server-trial-edition.zip -O /tmp/xld.zip && \
    unzip -q /tmp/xld.zip -d /opt && \
    rm /tmp/xld.zip
ADD xldeploy.answers /opt/xl-deploy-${version}-server-trial-edition/bin/xldeploy.answers

WORKDIR /opt/xl-deploy-${version}-server-trial-edition/bin
RUN ["./run.sh", "-setup", "-reinitialize", "-force", "-setup-defaults", "./bin/xldeploy.answers"]

VOLUME /opt/xl-deploy-${version}-server-trial-edition/conf
VOLUME /opt/xl-deploy-${version}-server-trial-edition/ext
VOLUME /opt/xl-deploy-${version}-server-trial-edition/hotfix
VOLUME /opt/xl-deploy-${version}-server-trial-edition/importablePackages
VOLUME /opt/xl-deploy-${version}-server-trial-edition/log
VOLUME /opt/xl-deploy-${version}-server-trial-edition/plugins
VOLUME /opt/xl-deploy-${version}-server-trial-edition/repository

EXPOSE 4516

CMD ["./run.sh"]
