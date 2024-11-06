FROM openjdk:17-jdk
ADD target/observability-auto-java.jar /observability-auto.jar
ADD target/opentelemetry-javaagent-2.1.0.jar /opentelemetry-javaagent.jar

ENV OTEL_EXPORTER_OTLP_ENDPOINT=http://host.docker.internal:4318

ENTRYPOINT java -javaagent:/opentelemetry-javaagent.jar \
                -Dotel.traces.exporter=otlp \
                -Dotel.metrics.exporter=otlp \
                -Dotel.logs.exporter=otlp \
                -Dotel.exporter.otlp.endpoint=${OTEL_EXPORTER_OTLP_ENDPOINT} \
                -Dotel.service.name=sample-java \
                -jar /observability-auto.jar
