# Laboratório usando Open Telemetry para coletar métricas e spanmetrics de uma app Java

Ref.: https://medium.com/@ahmadalammar/simplifying-spring-observability-with-opentelemetry-auto-instrumentation-and-java-agent-part-1-ef163f4125e3


## Instalação de Dependências:
```sh
sudo yum install -y maven
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Build:
Build da app de testes via maven:

```sh
cd build/java
mvn clean package
```

## Configurando a stack do Opentelemetry:


A partir da raiz do projeto inicialize a stack de observability para os testes:

```sh
docker-compose build
docker-compose up
```

> A partir da execução verifique se a aplicação está escutando na porta 8080 nas paths "/", e "/actuator/health"
> Mnatenha a execução em foreground (omitindo o parâmetro "-d") para acompanhar o processo de ingestão dos spans enviados pela app

---
