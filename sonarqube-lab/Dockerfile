FROM alpine:latest

# Instalar pacotes necessários
RUN apk update && \
    apk add --no-cache wget unzip curl

# Instalar o Go
ENV GOLANG_VERSION=1.17
RUN wget -O go.tar.gz https://golang.org/dl/go${GOLANG_VERSION}.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go.tar.gz && \
    rm go.tar.gz
ENV PATH="/usr/local/go/bin:${PATH}"

# Instalar o OpenJDK 11
RUN apk add --no-cache openjdk11

# Instalar o SonarQube
ENV SONARQUBE_VERSION=9.1.0.47736
RUN wget -O sonarqube.zip https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-${SONARQUBE_VERSION}.zip && \
    unzip sonarqube.zip -d /opt && \
    rm sonarqube.zip
ENV PATH="/opt/sonarqube-${SONARQUBE_VERSION}/bin/linux-x86-64:${PATH}"

# Instalar o Sonar Scanner
ENV SONAR_SCANNER_VERSION=4.6.2.2472
RUN wget -O sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}-linux.zip && \
    unzip sonar-scanner.zip -d /opt/sonar-scanner && \
    rm sonar-scanner.zip
ENV PATH="/opt/sonar-scanner-${SONAR_SCANNER_VERSION}-linux/bin/linux-x86-64:${PATH}"

# Definir o diretório de trabalho
WORKDIR /app

# Expor a porta do SonarQube
EXPOSE 9000

# Iniciar o SonarQube
CMD ["sonar.sh", "start"]
