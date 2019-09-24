FROM gradle:jdk11 AS build-stage

ENV APP_HOME=/root/dev/app/
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

COPY . $APP_HOME
RUN gradle build

FROM openjdk:11-jre-slim
ENV HOTBOX=/root
WORKDIR $HOTBOX

COPY --from=build-stage /root/dev/app/build/libs/* ./

EXPOSE 8080
CMD ["java","-jar","citest-0.0.1-all.jar"]
