FROM ubuntu:22.04 AS build

RUN apt-get update
RUN apt-get install -y openjdk-11-jdk maven

COPY src /build
COPY pom.xml /build/pom.xml

WORKDIR /build

RUN mvn package

FROM fabric8/java-alpine-openjdk11-jre:1.9.0

COPY --from=build /build/target/CryptoTradingBot.jar /opt/cryptobot/CrpytoTradingBot.jar

WORKDIR /opt/cryptobot

CMD java -jar /opt/cryptobot/CryptoTradingBot.jar