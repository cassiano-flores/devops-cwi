# FROM openjdk:11
# WORKDIR /app
# COPY target/hellodocker-0.0.1-SNAPSHOT.jar /app/
# EXPOSE 9320
# ENTRYPOINT ["java","-jar","/app/hellodocker-0.0.1-SNAPSHOT.jar"]

#EXPOSE 9320 -> só pra mostrar para quem está lendo, que o host (porta da máquina)
#               deve ser acessado através desse endereço

# Fase de construção
FROM maven:3.6.0-jdk-11-slim AS BUILD
WORKDIR /app
COPY src /app/src
COPY pom.xml /app
RUN mvn -f /app/pom.xml clean package

# Fase de execução
FROM openjdk:11-jre-slim
COPY --from=build app/target/hellodocker-0.0.1-SNAPSHOT.jar /usr/local/lib/hellodocker-0.0.1.jar
EXPOSE 9320
ENTRYPOINT ["java","-jar","/usr/local/lib/hellodocker-0.0.1.jar"]