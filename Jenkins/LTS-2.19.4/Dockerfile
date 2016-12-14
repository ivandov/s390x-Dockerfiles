# Jenkins 2.19.4 LTS for s390x

FROM s390x/ubuntu
MAINTAINER Ivan Dovgan (ivandov@us.ibm.com)

ENV JENKINS_HOME /jenkins
ENV JENKINS_SLAVE_AGENT_PORT 50000
ENV LOGFILE /var/log/jenkins/jenkins.log

VOLUME /jenkins

RUN apt-get update && \
    apt-get install -y \
    wget \
    openjdk-8-jre-headless

RUN mkdir /var/log/jenkins/

RUN wget http://mirrors.jenkins.io/war-stable/2.19.4/jenkins.war

#Default Web-UI port
EXPOSE 8080

#Default port for Jenkins Slaves
EXPOSE 50000

CMD nohup java -jar jenkins.war > $LOGFILE 2>&1
