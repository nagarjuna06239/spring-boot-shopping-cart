#FROM openjdk:8u151-jdk-alpine3.7

#EXPOSE 8070

#ENV APP_HOME /usr/src/app

#COPY target/shopping-cart-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar

#WORKDIR $APP_HOME

#ENTRYPOINT exec java -jar app.jar
# Maven build container 

FROM maven:3.5.2-jdk-8-alpine AS maven_build

COPY pom.xml /tmp/

COPY src /tmp/src/

WORKDIR /tmp/

RUN mvn package

#pull base image

FROM openjdk:8u151-jdk-alpine3.7

EXPOSE 8070

ENV APP_HOME /usr/src/app

COPY --from=maven_build /target/shopping-cart-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar

WORKDIR $APP_HOME

ENTRYPOINT exec java -jar app.jar
