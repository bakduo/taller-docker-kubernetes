FROM adoptopenjdk/openjdk11:alpine-jre

MAINTAINER rag.lkw.net@oncosmos.com

LABEL "App"="Ejer4"

LABEL "Description"="Sample use Dockerfile with Java Jar"
RUN mkdir /app

COPY *.jar app/

WORKDIR /app

RUN addgroup app

RUN adduser -D -h /app appjava app

RUN chown -R appjava:app /app

USER appjava

ENV PATH $PATH:$JAVA_HOME/bin:.

EXPOSE 8080

ENTRYPOINT ["java", "-server", "-Xmx64M", "-jar", "passwordapi.jar"]
