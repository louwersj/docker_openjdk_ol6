FROM oraclelinux:6.8

MAINTAINER Johan Louwers <louwersj@gmail.com>

RUN yum -y install java-1.7.0-openjdk-devel && yum clean all

ENV JAVA_HOME /usr/lib/jvm/java-openjdk

CMD ["java", "-version"]
