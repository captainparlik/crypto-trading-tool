FROM ubuntu:22.04 AS build

RUN apt-get update
RUN apt-get install -y openjdk-11-jdk maven

COPY ../.. /build

WORKDIR /build

RUN mvn package --projects crypto-trading-bot

FROM fabric8/java-alpine-openjdk11-jre:1.9.0

COPY --from=build /build/crypto-trading-bot/target/CryptoTradingBot.jar /opt/cryptobot/CrpytoTradingBot.jar

WORKDIR /opt/cryptobot

CMD java -jar /opt/cryptobot/CryptoTradingBot.jar