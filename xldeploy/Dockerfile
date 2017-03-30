FROM java:8u77-jre-alpine

MAINTAINER Fai Fung <ffung@xebia.com>

ENV version 6.1.0
ENV root /lib
ENV home ${root}/xl-deploy-${version}-server 

ADD xl-deploy-${version}-server-trial-edition.tar.gz ${root}


RUN rm -R \
      ${home}/serviceWrapper \
      ${home}/samples \
      ${home}/importablePackages/*

ADD xldeploy.answers ${home}/bin/xldeploy.answers
ADD keystore.jks ${home}/conf/keystore.jks

WORKDIR ${home}
RUN ["bin/run.sh", "-setup", "-reinitialize", "-force", "-setup-defaults", "bin/xldeploy.answers"]

VOLUME ["${home}/conf", \
	"${home}/ext", \
	"${home}/hotfix", \
	"${home}/importablePackages", \
	"${home}/log", \
	"${home}/plugins", \
	"${home}/repository"]

EXPOSE 4516

CMD ["bin/run.sh"]
