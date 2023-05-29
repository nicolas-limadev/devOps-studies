FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y wget unzip openjdk-11-jdk curl && \
    wget -O go.tar.gz https://go.dev/dl/go1.20.4.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go.tar.gz && \
    rm go.tar.gz && \
    apt-get install -y golang

ENV PATH="/usr/local/go/bin:${PATH}"

RUN wget -O sonarqube.zip https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.1.0.47736.zip \
    && unzip sonarqube.zip -d /opt \
    && rm sonarqube.zip \
    && echo 'export PATH=$PATH:/opt/sonarqube-9.1.0.47736/bin' >> /root/.bashrc

RUN wget -O sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.6.2.2472-linux.zip \
    && unzip sonar-scanner.zip -d /opt/sonar-scanner \
    && echo 'export PATH=$PATH:/opt/sonar-scanner/bin' >> root/.bashrc
    
COPY . .

EXPOSE 9000

CMD cd /opt/sonarqube-9.1.0.47736/bin && ./sonar.sh start
