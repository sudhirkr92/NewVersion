FROM sudhirkr92/java-soapui-base
FROM eclipse-temurin:8-jdk-jammy as BUILD
WORKDIR /opt/app
COPY --from=BUILD /opt/app/target/*.jar /opt/app/*.jar
EXPOSE 8090 8088
COPY ./demo1/soapui/AccountDetails.xml /opt/app/AccountDetails.xml
CMD /opt/SoapUI-5.2.0/bin/mockservicerunner.sh -p 8088 /opt/app/AccountDetails.xml & java -jar /opt/app/*.jar
