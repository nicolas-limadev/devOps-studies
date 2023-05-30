# Use a imagem do Sonar Scanner
FROM sonarsource/sonar-scanner-cli

# Defina as variáveis de ambiente do SonarQube
ENV SONAR_HOST_URL=http://localhost:9000
ENV SONAR_LOGIN=sqp_ed97d15f47df371831f9e4b6ddada74e93047df7

# Defina o diretório de trabalho
WORKDIR /usr/src/app

# Copie o código fonte para o contêiner
COPY . .

# Execute o comando do Sonar Scanner
CMD sonar-scanner

