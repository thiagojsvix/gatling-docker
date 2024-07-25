# Use uma imagem base do OpenJDK
FROM openjdk:21-slim

# Defina o diretório de trabalho dentro do container
WORKDIR /opt

ENV GATLING_VERSION=3.11.5

# Baixe e extraia o Gatling
ADD gatling.zip .

RUN apt-get update
RUN apt-get install -y unzip
RUN unzip gatling.zip
RUN cd gatling-charts-highcharts-bundle-${GATLING_VERSION}/
RUN rm -rf ../gatling.zip

# Define novo dietório de trabalho dentro do container
WORKDIR /opt/gatling-charts-highcharts-bundle-${GATLING_VERSION}/

# Atualiza arquivo de configuração
RUN rm ./src/test/resources/gatling.conf
ADD conf/gatlidng${GATLING_VERSION}.conf ./src/test/resources/gatling.conf

# Defina o comando de inicialização do Gatling
#ENTRYPOINT ["./mvnw gatling:test"]
ENTRYPOINT ["./mvnw"]
#CMD ["./mvnw"]
