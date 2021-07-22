FROM adoptopenjdk/openjdk11:jdk-11.0.11_9-alpine

ARG VERSION=0.20.2
ENV DATAVERSE_SUPERSET_GIT=https://github.com/SSHOC/dataverse-superset.git

WORKDIR /opt/dataverse-superset
RUN apk add --no-cache bash git vim less
RUN git clone ${DATAVERSE_SUPERSET_GIT} . && cp application.yaml.sample application.yaml && \
    sed -i "s|172.18.0.3:5432|postgres:5433|g" application.yaml && sed -i "s|192.168.56.7|superset|g" application.yaml && \
    ./gradlew build

ENTRYPOINT [ "bash", "-c","./gradlew bootRun" ]