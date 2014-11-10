FROM debian

MAINTAINER Fai Fung <ffung@xebia.com>

RUN apt-get update 
RUN apt-get install -y openjdk-7-jre-headless --no-install-recommends

ADD xl-deploy-4.5.1-server.tar.gz /opt
ADD xldeploy.answers /opt/xl-deploy-4.5.1-server/bin/xldeploy.answers 

WORKDIR /opt/xl-deploy-4.5.1-server/bin 
RUN ["./server.sh", "-setup", "-reinitialize", "-force", "-setup-defaults", "./bin/xldeploy.answers"]

VOLUME /opt/xl-deploy-4.5.1-server/conf
VOLUME /opt/xl-deploy-4.5.1-server/ext
VOLUME /opt/xl-deploy-4.5.1-server/hotfix
VOLUME /opt/xl-deploy-4.5.1-server/importablePackages
VOLUME /opt/xl-deploy-4.5.1-server/log
VOLUME /opt/xl-deploy-4.5.1-server/plugins
VOLUME /opt/xl-deploy-4.5.1-server/repository

EXPOSE 4516

CMD ["./server.sh"]
