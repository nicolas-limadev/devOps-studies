FROM adoptopenjdk/openjdk11:jdk-11.0.19_7-alpine
RUN addgroup -g 1000 notes && adduser -D -u 1000 -G notes notes
ENV MAVEN_VERSION 3.9.1
ENV MAVEN_HOME /usr/lib/mvn
ENV PATH $MAVEN_HOME/bin:$PATH
RUN wget https://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
    tar -zxvf apache-maven-$MAVEN_VERSION-bin.tar.gz && \
    rm apache-maven-$MAVEN_VERSION-bin.tar.gz && \
    mv apache-maven-$MAVEN_VERSION /usr/lib/mvn
RUN apk --update add git
RUN mkdir /opt/notes
RUN chown -R notes:notes /opt/notes
USER notes:notes
WORKDIR /opt/notes
RUN git clone https://github.com/callicoder/spring-boot-mysql-rest-api-tutorial.git /opt/notes
RUN mvn package -Dmaven.test.skip=true
ARG JAR_FILE=*.jar
RUN cp ./target/easy-notes-1.0.0.jar /opt/notes/easy-notes.jar
COPY application.properties application.properties
ENTRYPOINT ["java", "-jar", "/opt/notes/easy-notes.jar"]