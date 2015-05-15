FROM phusion/baseimage


RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
  && add-apt-repository -y ppa:webupd8team/java \
  && apt-get update \
  && apt-get install -y oracle-java8-installer tomcat7 \
  && rm -rf /var/lib/apt/lists/* \
  && rm -rf /var/cache/oracle-jdk8-installer

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

ENV CATALINA_HOME /usr/share/tomcat7
ENV PATH $CATALINA_HOME/bin:$PATH

EXPOSE 8080
EXPOSE 8000
CMD ["/usr/share/tomcat7/bin/catalina.sh", "jpda", "run"]