FROM gradle:jdk11 AS build-stage

ENV APP_HOME=/root/dev/app/
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

COPY *.gradle gradle.* $APP_HOME
RUN gradle --version

COPY src $APP_HOME/src
COPY resources $APP_HOME/resources
RUN gradle --no-daemon build

FROM openjdk:11-jre-slim

COPY --from=build-stage /root/dev/app/build/libs/* ./

EXPOSE 8080
CMD ["java","-jar","citest-0.0.1-all.jar"]
