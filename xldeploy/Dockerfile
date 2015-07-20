FROM debian

MAINTAINER Fai Fung <ffung@xebia.com>

ENV version 5.0.1
RUN apt-get update 
RUN apt-get install -y openjdk-7-jre-headless unzip wget --no-install-recommends

RUN wget https://dist.xebialabs.com/public/distributions/xl-deploy/${version}/xl-deploy-${version}-server-free-edition.zip -O /tmp/xld.zip && unzip /tmp/xld.zip -d /opt && rm /tmp/xld.zip
ADD xldeploy.answers /opt/xl-deploy-${version}-server-free-edition/bin/xldeploy.answers 

WORKDIR /opt/xl-deploy-${version}-server-free-edition/bin 
RUN ["./run.sh", "-setup", "-reinitialize", "-force", "-setup-defaults", "./bin/xldeploy.answers"]

VOLUME /opt/xl-deploy-${version}-server-free-edition/conf
VOLUME /opt/xl-deploy-${version}-server-free-edition/ext
VOLUME /opt/xl-deploy-${version}-server-free-edition/hotfix
VOLUME /opt/xl-deploy-${version}-server-free-edition/importablePackages
VOLUME /opt/xl-deploy-${version}-server-free-edition/log
VOLUME /opt/xl-deploy-${version}-server-free-edition/plugins
VOLUME /opt/xl-deploy-${version}-server-free-edition/repository

EXPOSE 4516

CMD ["./run.sh"]
