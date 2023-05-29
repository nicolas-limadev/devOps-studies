FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y wget unzip openjdk-11-jdk nodejs

COPY provision.sh /provision.sh
RUN chmod +x /provision.sh

EXPOSE 9000

CMD ["/provision.sh"]
