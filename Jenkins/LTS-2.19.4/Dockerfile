# Jenkins 2.19.4 LTS for s390x

FROM s390x/ubuntu
MAINTAINER Ivan Dovgan (ivandov@us.ibm.com)

ENV JENKINS_HOME=/jenkins
ENV LOGFILE=/var/log/jenkins/jenkins.log

RUN apt-get update && \
    apt-get install -y \
    wget \
    openjdk-8-jre-headless

RUN mkdir /jenkins && mkdir /var/log/jenkins/ && cd /jenkins

RUN wget http://mirrors.jenkins.io/war-stable/2.19.4/jenkins.war

EXPOSE 8080

CMD nohup java -jar jenkins.war > $LOGFILE 2>&1
