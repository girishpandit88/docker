FROM ubuntu

RUN \
	apt-get update \
	&& apt-get install -y software-properties-common
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
  && add-apt-repository -y ppa:webupd8team/java \
  && apt-get update \
  && apt-get install -y oracle-java8-installer tomcat7 \
  && rm -rf /var/lib/apt/lists/* \
  && rm -rf /var/cache/oracle-jdk8-installer

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Create working space
RUN mkdir /var/dynamodb_wd
WORKDIR /var/dynamodb_wd

# Default port for DynamoDB Local
EXPOSE 7777

# Get the package from Amazon
RUN wget -O /var/dynamodb_wd/dynamodb_local_latest http://dynamodb-local.s3-website-us-west-2.amazonaws.com/dynamodb_local_latest \
&& tar xfz /var/dynamodb_wd/dynamodb_local_latest

# Default command for image
ENTRYPOINT ["/usr/bin/java", "-Djava.library.path=.", "-jar", "DynamoDBLocal.jar", "-dbPath", "/var/dynamodb_local"]
CMD ["-port", "7777"]

# Add VOLUMEs to allow backup of config, logs and databases
VOLUME ["/var/dynamodb_local", "/var/dynamodb_wd"]