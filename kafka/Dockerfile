FROM openjdk:8-jdk-slim as download
ARG SCALA_VERSION=2.13
ARG KAFKA_VERSION=3.1.0
ADD https://dlcdn.apache.org/kafka/${KAFKA_VERSION}/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz .
RUN tar -xvf kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz
RUN mv kafka_${SCALA_VERSION}-${KAFKA_VERSION} kafka
FROM openjdk:8-jdk-slim as run
COPY --from=download /kafka /opt/kafka
EXPOSE 9093/tcp
EXPOSE 9092/tcp
LABEL org.opencontainers.image.source https://github.com/drydock-app/library
CMD ["/opt/kafka/bin/kafka-server-start.sh","/etc/kafka/server.properties"]
